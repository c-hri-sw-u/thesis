## Vision Capture 总结

**🔒 主模态：** egocentric vision，smartphone 穿戴在身上模拟 smart glasses。

**Capture 模式：Adaptive Interval**

一个动态调整的 capture 频率，由场景变化信号驱动：

- **max_interval（🧪）：** 场景稳定时的低频 baseline，推荐 15-30 秒起步。保证静态场景仍有持续覆盖——模式型信息（每天固定时间做饭、桌上常备的物品）依赖长期低频采样的累积，不能放弃。
- **min_interval：** 场景活跃时的密集频率，推荐 3 秒。
- **Trigger 源：** VAD onset/offset、motion state change（stationary ↔ sustained_motion）。
- **行为：** 默认以 max_interval 运转。Trigger 触发 → 立即降到 min_interval 密集捕获。连续若干帧无新 trigger → interval 逐步回升（3s → 5s → 8s → 12s → ... → max_interval）。回升中再次 trigger → 立刻回到 min_interval。

**设计理由：** 密集捕获服务于事件检测（场景转换时发生了什么），低频 baseline 服务于模式积累（用户日常规律是什么）。两者对 personalization 的贡献方式不同，缺一不可。

**注：** Trigger 瞬间的帧可能因运动模糊而无用，这由 Layer 1.5 的 blur detection 处理，不在 capture 层解决。

---

分清**采样频率**和**输出频率**。

**Audio 和 IMU 的采样是持续的、远快于 3 秒的。** AVAudioEngine tap 每 100ms 就给你一帧音频数据，accelerometer 也可以每 100ms 采样一次。它们一直在跑，一直在更新内部状态。

**3 秒的 sliding window 是平滑窗口，不是输出间隔。** Noise level 的 3 秒窗口意思是"用最近 3 秒的数据算一个均值"，但这个均值随时可以读——你任何时刻问它"现在噪音多大"，它都能给你一个基于最近 3 秒平滑后的答案。VAD 更快，libfvad 每拿到一帧音频（10-30ms）就返回一次判断。IMU 的方差计算也是类似，2-3 秒窗口持续滚动。

所以实际的关系是：**Audio 和 IMU 是一直在后台跑的连续信号流，Vision capture 是离散的采样点。** 每次 vision capture 触发的时候，你就去读一下 Audio 和 IMU 当前的状态，附到这帧上。

**所以 min_interval 不需要是 3s,** interval 的递增序列也不需要卡 3 的倍数，按体感合理就行，比如 3s → 5s → 8s → 15s → 30s。

## Audio Channel 总结

**一个** `AVAudioEngine` **tap[^1]，同时产出三样东西：**

1. **VAD** — libfvad（WebRTC VAD 独立 fork），优先找现成 Swift package，否则 C bridging 接入。通过 AVAudioEngine tap 获取音频帧，每帧返回 speech/not speech。用作 **trigger**（标记 batch boundary + 触发额外 frame capture）和 **tag**。
2. **Noise Level** — 同一个 tap 里算 RMS → dB，3 秒 sliding window 平滑，映射到 quiet/moderate/loud。只用作 **tag**。
3. **Transcription** — `SFSpeechRecognizer`，默认 **off**。在 Layer 1.5 batch boundary 时按需触发，只处理 VAD 标记为有语音的片段。作为 🧪 experiment variable，中后期视需要开启。

**Speaker count：不做。** 没有轻量级 iOS 方案，VLM 从画面里就能推断社交场景。

---

[^1]: <p>iOS 音频管线上的一个"监听口"。<code>AVAudioEngine</code> 是 Apple 的音频处理框架，你在它上面装一个 tap，意思是"每隔一小段时间（比如 100ms），把麦克风录到的原始 PCM 音频帧给我一份"</p>

## IMU Channel 总结

**用** `CMAccelerometer` **原始数据，不依赖** `CMMotionActivityManager`**。**

三轴加速度 → 合成 magnitude → 2-3 秒窗口算方差。方差低 = stationary，方差高且持续 >5-8 秒 = sustained_motion，短暂 spike = 忽略。

**输出：**

```
imu_tags: {
    motion_state: "stationary" | "sustained_motion"
}
```

**双角色：**

- **Trigger：** 状态转换（stationary ↔ sustained_motion）触发额外 frame capture + preprocess batch boundary
- **Tag：** 当前状态附到 frame metadata 上，给 VLM 提供运动上下文

**不做 activity classification。** 手机穿戴姿态与系统预设不符，分类结果不可靠。VLM 从画面就能判断具体活动类型，IMU 只需要回答"动没动"。

## 对 Layer 1.5 Preprocessing 的适配论证

Preprocessing 需要做两件事：划 batch boundary 和 batch 内 frame filtering。逐项检查：

**Batch boundary 划分需要：**

- `timestamp` — 判断是否到了 max window ✅
- `audio_tags.speech_detected` — VAD 翻转（前一帧 false 这一帧 true，或反过来）是 batch 切分信号 ✅
- `imu_tags.motion_state` — 状态转换是 batch 切分信号 ✅

**Frame filtering 需要：**

- `image` — black detection、blur detection、pixel similarity 的输入 ✅
- `timestamp` — 相邻帧去重需要按时间序列处理 ✅
- `audio_tags` + `imu_tags` — multimodal prioritization：有语音的帧、motion state 刚转换的帧优先保留 ✅

`current_interval` **的额外价值：**

- 对 frame filtering 有用：interval 很小（比如 3s）意味着这段时间帧密度高，去重可以更激进；interval 很大（比如 30s）意味着每帧都珍贵，去重应更保守
- 对 batch boundary 有辅助价值：interval 从大突然变小意味着刚发生了 trigger，可以作为切 batch 的参考信号

## Layer 1 → Layer 1.5 数据流总结

### 两个独立循环

**Capture 循环（Layer 1）：** 持续运行的数据生产者。按 adaptive interval 拍帧，往 buffer 里扔。Sensor trigger（VAD 翻转、motion state change）只调节 interval 大小，不直接产出任何处理结果。

**Preprocess 循环（Layer 1.5）：** 被动等待的数据消费者。两种唤醒条件：sensor trigger 通知"可以来看看了"，或 max window 到时间了。

### 三层结构

**Sensor Trigger（Layer 1）：** 低门槛，宁可多触发。它做两件事：把 capture interval 调小（多拍几帧留着），以及通知 preprocess "你可以来看看了"。

**Preprocess 验证（Layer 1.5）：** 拿到 buffer 里的帧之后，先做一个**视觉层面的 scene change 判断**——比较这批帧和上一个 batch 最后几帧的 pixel similarity。如果视觉内容没有实质变化（用户只是动了一下但还在同一个场景），那这批帧就不构成一个独立的 batch，而是**合并回去**，等 max window 或者下一次 trigger 再一起处理。

**只有视觉验证确认了 scene change，才真正切出一个新 batch 送去 Layer 2 inference。**

这样流程就变成：

1. Sensor trigger fires → capture interval 调小 → preprocess 被唤醒
2. Preprocess 取出 buffer 里的帧，跟上一个 batch 的尾帧做 pixel similarity 比较
3. **如果视觉确认了 scene change：** 切出新 batch → frame filtering → 送 Layer 2
4. **如果视觉没变化：** 不切 batch，帧留在 buffer 里，等下次触发或 max window

### 关键区分

- **Sensor Trigger ≠ Scene Change。** Sensor trigger 是低门槛的猜测（宁可多触发），scene change 是 preprocess 通过视觉比较做出的判断。
- **Capture interval 跟着 sensor trigger 走** — 多拍几帧成本低，拍了不用就扔。
- **Batch 切分权在 preprocess 手里** — 送去 VLM 的 batch 数量由视觉内容变化决定，不由 sensor 灵敏度决定。
- **Max window 是兜底机制** — 即使没有任何 trigger，每隔 max window（🧪 10-15 分钟）也强制切一次 batch，保证静态场景不会被遗忘。

## Scene Change 视觉验证总结

**方案：SSIM（Structural Similarity）起步。**

将当前帧与上一个 batch 尾帧做 SSIM 比较，低于阈值（🧪）则确认 scene change，切出新 batch。

**为什么选 SSIM：**

- 比像素级比较对光照变化更鲁棒
- 纯 CPU、纯 OpenCV，无需额外模型，零功耗增量
- 此时已有 sensor trigger 作为先验，SSIM 只需做确认/否决，不需要独立发现 scene change

**降级/升级路径：**

- 如果 SSIM false positive 太多（光照、轻微视角偏移），升级到 embedding similarity（MobileNet / CLIP vision encoder via Core ML），作为 🧪 experiment variable
- VLM 在 Layer 2 仍然是最终兜底——即使 scene change 判断偶尔失误，不会产生错误的 memory entry

---

**Pixel deduplication：** 在一个 batch 内部，相邻帧之间做像素相似度比较，把几乎一样的帧去掉。比如你坐在桌前 10 分钟，即使是 max_interval 30 秒拍一帧也有 20 帧，但这 20 帧画面基本一模一样。Pixel deduplication 就是把这些重复帧丢掉，只留有变化的。这跟 scene change 验证用的 SSIM 不是一回事——SSIM 是跨 batch 比较（当前帧 vs 上一个 batch 尾帧），pixel deduplication 是 batch 内部的相邻帧去重。

**Multimodal prioritization：** 经过前面三轮过滤（black、blur、deduplication）之后，剩下的帧里面再做一次优先级排序。优先保留那些 metadata 标记了"有事发生"的帧——比如 `speech_detected: true` 的帧（有人在说话那一刻的画面）、或者 `motion_state` 刚刚发生转换的帧。这些帧的信息量更高，因为它们对应着某个事件正在发生。如果过滤后剩余帧数仍然超过目标范围（4-8 帧），就优先砍掉那些没有任何 audio/imu 事件标记的帧。

简单说：pixel deduplication 是**去掉没用的**，multimodal prioritization 是**在有用的里面挑最有用的**。

## Frame Importance Score

**公式：** `score = w1 * visual + w2 * audio + w3 * imu + w4 * sparsity`

**四个分量，每个归一化到 0-1：**

- **visual：** 该帧与前一帧的 pixel difference（deduplication 步骤已算出），min-max 归一化到 batch 内 0-1
- **audio：** `speech_detected: false` = 0，`speech_detected: true` = 0.5，VAD 翻转点（onset/offset）= 1.0
- **imu：** 状态无变化 = 0，motion state 刚转换 = 1.0
- **sparsity：** `current_interval / max_interval`，归一化到 0-1。interval 越大，帧越珍贵，分越高

**默认权重（🧪 全部可调）：**

`w1 = 0.3, w2 = 0.3, w3 = 0.2, w4 = 0.2`

视觉和语音权重最高，因为它们直接反映场景内容变化。IMU 和 sparsity 是辅助信号。

**选帧：** batch 内所有帧按 score 降序排列，取 top-K（K = 4-8，🧪）。

## Layer 3 Memory Integration 总结

### 核心发现

OpenClaw 的 `memory_search` 索引范围是 `MEMORY.md` + `memory/**/*.md`，即 memory 目录下所有 markdown 文件。这意味着 perception pipeline **不需要进入 OpenClaw 的任何原生写入路径**（不需要 silent session，不需要触发 compaction，不需要竞争 context window）。只需要往 `memory/` 目录下放 markdown 文件，OpenClaw 的 agent 在任何 session 中都能通过 `memory_search` 检索到。

### 文件结构

```
memory/
├── 2026-03-14.md                # OpenClaw 原生 daily log（digital interactions）
├── MEMORY.md                    # OpenClaw 原生长期记忆（digital）
│
├── physical-logs/
│   ├── 2026-03-14.md            # 当天所有 batch observations（实时写入）
│   └── 2026-03-15.md
├── physical-insights/
│   ├── 2026-03-14.md            # nightly summary（当日关键信息提取）
│   └── 2026-03-15.md
├── physical-pattern.md          # 跨天持久 pattern（如 "user cooks dinner ~6pm daily"）
```

### 三层写入逻辑

**physical-logs/**（全量记录层）

- 写入时机：实时，每个 VLM inference batch 完成后立即 append
- 内容：faithful observation + interpretive annotation
- 特征：volume 最大，粒度最细，受 temporal decay 降权
- 服务：RQ1（什么信息变得可见了）

**physical-insights/**（日级提炼层）

- 写入时机：每天晚上，nightly job 读取当天 physical-logs
- 内容：当天值得注意的信息——新行为、异常事件、与已知 pattern 的偏离
- 特征：每天一个简短文件，受 temporal decay
- 服务：RQ2（什么信息对 personalization 有用）

**physical-pattern.md**（持久 pattern 层）

- 写入时机：nightly job 同步维护
- 内容：跨天反复出现的 pattern（routines, preferences, habits）
- 特征：单文件，无日期，不受 temporal decay，始终正常权重参与检索
- 服务：RQ2 + RQ3（personalization 核心产出 + 设计发现）

### 与 OpenClaw 原生架构的平行关系

|  | Digital（OpenClaw 原生） | Physical（perception pipeline） |
| --- | --- | --- |
| 全量记录 | `memory/YYYY-MM-DD.md` | `physical-logs/YYYY-MM-DD.md` |
| 日级提炼 | （无原生等价物） | `physical-insights/YYYY-MM-DD.md` |
| 持久知识 | `MEMORY.md` | `physical-pattern.md` |

### 架构优势

- **纯 additive extension**：不修改 OpenClaw 代码，不干扰 session/compaction 机制
- **两条 pipeline 的唯一交汇点**是 `memory_search`：agent 检索时自然同时搜索 digital 和 physical 两个来源
- **日级提炼层是 pipeline 独有的**：OpenClaw 原生没有 nightly summary 机制，daily log 到 MEMORY.md 的提炼完全依赖 model 在 session 中主动判断。perception pipeline 通过 nightly job 补上了这个中间层——这本身是一个 RQ3 的 design finding

### 对 Layer 2 Inference 的倒推

- VLM batch output 应该是 **observation + interpretive annotation**（faithful description 为主，附加语义友好的标注），因为它直接写入 physical-logs，需要对 hybrid search 友好
- 每个 entry 应该是**独立短段落 + timestamp header**，确保 chunking 后检索粒度足够细
- 不需要在 batch 级别做 pattern extraction——这留给 nightly job

## 总结：OpenClaw Memory Retrieval & Context Loading 机制

### 1. OpenClaw 原生的两层记忆可见性

**Bootstrap files（系统级注入，每个 turn 都在 system prompt 里）：**
AGENTS.md, SOUL.md, USER.md, IDENTITY.md, TOOLS.md, HEARTBEAT.md, **MEMORY.md** — 这些是硬编码的列表，每个 turn 自动注入，不需要 agent 做任何 tool call。

**Daily logs（指令驱动，session 开头 agent 主动读取）：**
`memory/YYYY-MM-DD.md`（今天+昨天）— 不是系统注入的，而是 AGENTS.md 里写了一条指令："On session start, read today + yesterday + memory.md if present"，agent 在 session 开头执行 read tool call 把内容拉进 conversation context。

**`memory_search`（按需检索）：**
`memory/` 目录下所有 `.md` 文件都被 BM25 + vector hybrid search 索引，agent 调用 `memory_search` 时可以搜到。Temporal decay 基于文件名日期，近期文件权重更高。

### 2. Perception pipeline 三层文件的可见性设计

| 文件 | 可见性级别 | 实现方式 | 理由 |
|------|-----------|---------|------|
| `physical-pattern.md` | 每个 turn 都在 system prompt 里 | `agent:bootstrap` hook 注入 bootstrap file 列表 | 持久 pattern，内容短，agent 需要始终"知道" |
| `physical-insights/YYYY-MM-DD.md`（今天+昨天） | Session 开头加载 | AGENTS.md 加一行读取指令 | 日级摘要，session 开始时了解近两天的物理世界要点 |
| `physical-logs/YYYY-MM-DD.md` | 按需检索 | `memory_search` 自动索引 | 全量 batch observations，太大不适合主动加载，需要时再搜 |

### 3. 可插拔，零源码修改

- `physical-pattern.md` 的注入通过 OpenClaw **内置的 `bootstrap-extra-files` hook**（或自定义 `agent:bootstrap` hook）实现 — hook 放在 `~/.openclaw/hooks/` 目录，OpenClaw 更新不受影响
- `physical-insights` 的读取通过编辑 **AGENTS.md**（用户可编辑的配置文件）实现
- `physical-logs` 不需要任何配置，放在 `memory/` 下就自动进入 `memory_search` 索引

整个 perception pipeline 与 OpenClaw 的集成是 **纯 additive**：不改源码、不装插件依赖、不干扰原生 session/compaction 机制。唯一的交汇点是 `memory/` 目录和一个轻量级 hook。