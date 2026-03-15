# 论文后半段：极简骨架 v2

> 前半段回顾：
> - Ch1 Introduction — 问题 + RQs
> - Ch2 Related Work — 文献 gap
> - Ch3 Design Rationale — 为什么选 egocentric vision + OpenClaw
> - Ch4 System Design — pipeline 怎么建的（capture → preprocess → inference → memory integration）
>   - Pipeline 的终点是 memory integration。数据流到此结束。

---

## Chapter 5: Methodology（我怎么研究这个系统）

### 5.1 Research through Design + Autoethnography
- RtD 的核心逻辑：知识不是来自"建完系统然后评估"，而是来自"建、用、发现问题、改、再用"的迭代过程。迭代本身就是数据。
- Autoethnography 的 rationale：longitudinal deployment with external users 不可行；自我研究允许深度持续观察；HCI 先例（Neustaedter & Sengers, 2012）
- 你同时是设计者、被试、分析者——upfront 承认这个身份重叠及其局限

### 5.2 Study Design

**时长：** 两周。前半段允许系统迭代，后半段稳定运行以收集可比较数据。

**三个阶段：**

| 阶段 | 时间 | 系统状态 | 观察方式 | 目的 |
|------|------|---------|---------|------|
| Phase 0: Calibration | Day 1-3 | Pipeline 运行，允许迭代（调 prompt、参数、batch window） | 观察 perception log 质量，识别故障模式 | 让 pipeline 稳定到可以产生有意义的 memory entries |
| Phase 1: Baseline | Day 4-10 | Pipeline 稳定运行，无 proactive cron | 被动观察 + structured probes | 观察物理信息在自然交互中的 surface 频率和质量；用 probe 测试 agent 被问到时能否利用物理信息 |
| Phase 2: Proactive | Day 11-14 | 加入 proactive cron job | 被动观察 + structured probes + proactive messages | 观察 agent 主动利用物理信息的频率和质量；与 Phase 1 对比 |

**三种观察方式（递进光谱）：**

这三种方式共同回答"agent 是否识别到物理世界中的有用信息并有效利用"，但从不同角度：

1. **被动观察：** 自然使用 OpenClaw，不刻意引导话题。观察 agent 是否自发 surface 物理世界 memory。测试的是：在完全自然的条件下，物理信息的利用率是多少？
2. **Structured probes：** 你查看 perception log，确认 pipeline 捕捉到了某些信息（比如连续三天下午去咖啡店），然后刻意向 agent 提出相关问题（"帮我规划下午"）。测试的是：当机会出现时，agent 能不能用物理信息？这隔离了"agent 没机会用"和"agent 有机会但不会用"两种失败模式。
3. **Proactive cron job：** 定时触发 agent 审查近期物理世界 memory，决定是否主动联系你。测试的是：agent 能不能自己判断何时该主动利用物理信息？

Phase 1 使用方式 1 + 2。Phase 2 使用方式 1 + 2 + 3。

**迭代作为研究活动：**

Phase 0 中的所有迭代（prompt 修改、参数调整、pipeline 修复）都被完整记录，包括：改了什么、为什么改、改前改后的输出对比。这些迭代记录是 RQ3 的直接数据来源——design requirements 从中提炼。

Phase 1 和 Phase 2 中，pipeline 配置保持稳定。如果出现必须修改的问题，记录为 finding 但不改动，除非问题导致 pipeline 完全无法运行。

### 5.3 Data Sources

| 数据源 | 内容 | 对应 RQ |
|-------|------|--------|
| Perception log | Pipeline 产生的所有 VLM output（全量，不经 OpenClaw 筛选） | RQ1：物理世界信息的类型和覆盖范围 |
| OpenClaw retained memory | OpenClaw memory pipeline 实际保留的条目（daily logs + MEMORY.md 变化） | RQ3：现有 memory architecture 对物理信息的处理能力 |
| 交互记录 | 研究期间所有与 OpenClaw 的对话 transcript（含 structured probe sessions 的标注） | RQ2：哪些交互中物理信息有用 / 无用 |
| Proactive messages log | Phase 2 中 cron job 触发的所有 agent 主动消息 | RQ2：proactive surfacing 的质量 |
| Autoethnographic journal | 每日日记 — 见 5.4 | 所有 RQ + design implications |
| Design iteration log | Phase 0 中的所有 pipeline 修改记录 | RQ3：design requirements |

### 5.4 Journal Protocol
每日日记记录以下维度：
- 今天 agent 的哪些回复引用了物理世界信息？是否有用？为什么？
- 有没有 agent 本该知道但没用到的物理信息？（missed opportunity）
- 有没有物理信息引入了噪音或不相关内容？
- Structured probe 的结果（如果当天做了 probe）
- Phase 2 中：proactive messages 的质量评估
- Pipeline 的技术观察、主观反思

### 5.5 Analysis Method
- **Perception log 内容分类：** 对所有 VLM output 进行归类（活动、环境、物品、社交、时间模式等） → RQ1
- **交互记录定性编码：** 标注每次交互中物理信息的角色（有用 / 无关 / 有害 / 未被利用） → RQ2
- **Perception log vs. retained memory 比较：** 看 OpenClaw 保留了什么、丢弃了什么、保留格式是否合理 → RQ3
- **日记 + 迭代记录的主题分析：** 从反思和迭代决策中提取 recurring themes → design implications
- **Phase 1 vs. Phase 2 对比：** 三种观察方式下物理信息利用率和质量的变化

---

## Chapter 6: Findings（我发现了什么）

**职责：** 描述性地呈现数据和观察。"我看到了什么"。

### 6.1 What Physical-World Information Was Captured（→ RQ1）
- Perception log 的内容分类和分布
- 代表性例子：哪些信息类别是 digital traces 完全无法获取的
- 信息密度和质量的变化（一天之内、跨天的 pattern）

### 6.2 When Physical Context Helped vs. Didn't（→ RQ2）

**三种观察方式的发现：**

- **被动观察：** 自然交互中物理信息被 surface 的频率、场景、质量
- **Structured probes：** 当你针对性提问时，agent 利用物理信息的成功率和失败模式
- **Proactive messages（Phase 2）：** agent 主动推送的消息中，有多少是有价值的、有多少是噪音

**按任务类型的发现：**

- 有帮助的场景（附具体交互例子）
- 没有帮助或引入噪音的场景（附具体交互例子）

**Phase 1 vs. Phase 2 对比**

### 6.3 Pipeline Behavior and Design Iterations（→ RQ3）
- Phase 0 中的迭代记录：改了什么、为什么、效果如何
- Perception log vs. OpenClaw retained memory 的差异分析
- 具体的失败案例（pipeline 产出低质量 memory、OpenClaw 丢弃有价值信息、nightly summary 的效果等）

---

## Chapter 7: Discussion（这意味着什么）

**职责：** 从个人经验提升为可推广的设计知识。RtD 论文的核心贡献章节。

### 7.1 Design Implications（→ RQ3 的核心回答）
从 Findings 中提炼的可推广设计建议。可能包括（取决于实际 findings）：

- **Proactive surfacing 是否必要：** 物理世界信息的使用模式是否与数字信息根本不同
- **Granularity trade-off：** 实时状态 vs. 日级模式 vs. 周级趋势，哪个层级的物理信息对 personalization 最有价值
- **Memory ingestion 的多模态扩展：** text-only 假设的具体局限在哪里，需要什么样的入口
- **Privacy 和 capture 的张力：** always-on capture 的实际体验，14 天 retention 的合理性
- **Prompt design for personalization-oriented perception：** VLM prompt 需要什么样的引导才能产出 personalization-relevant 而非 generic description 的输出

### 7.2 Revisiting the Research Questions
- 综合回答 RQ1、RQ2、RQ3，把 Findings 和 Design Implications 串联

### 7.3 Limitations
- 单一被试（autoethnography 的固有局限，findings 的可推广性受限）
- 两周时长——某些 longitudinal patterns 可能需要更长时间才能浮现
- Smartphone proxy vs. 真正 smart glasses 的差异（佩戴方式、视角、社交接受度）
- 研究者 = 设计者 = 被试的 triple role bias
- OpenClaw 作为唯一 integration target 的局限

### 7.4 Future Work
- 更大规模 user study 验证 design implications
- 更长部署周期
- 其他 agent 平台的迁移性
- Audio transcription 的深度探索
- Proactive surfacing 机制的系统性设计研究

---

## Chapter 8: Conclusion
简短收尾。重申问题、方法、核心发现、贡献。

---

## 逻辑流

```
Ch1-2:  这个问题存在，没人研究过
Ch3:    我选了这些工具来研究它
Ch4:    我建了这个系统（pipeline 到 memory integration 结束）
Ch5:    我怎么用这个系统来产生知识（三阶段 × 三种观察方式 × 六种数据源）
Ch6:    我观察到了什么（描述性结果，按 RQ 组织）
Ch7:    这对整个领域意味着什么（design implications = 论文的核心贡献）
Ch8:    总结
```

关键边界：
- Ch4 的终点是 memory integration，不涉及"怎么用"或"怎么评估"
- Ch5 的 Phase 0（calibration + 迭代）承认 pipeline 不是一次建完的，迭代是 RtD 的合法研究活动
- Ch6 严格描述性，不做推论
- Ch7 的 design implications 是论文的最高价值产出——后来的研究者拿走的是这些，不是你的系统代码