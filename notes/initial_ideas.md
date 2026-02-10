# Initial Ideas & Discussion

## Theme
通过视觉（+辅助sensor）检测日常生活，压缩后让Agent更了解用户

## Key Insights

### 1. 历史背景
- **Self-log:** 长期记录自己生活的传统
- **Urban design:** 通过record了解空间使用方式
- **Quantified self:** Fitbit, Apple Watch等健康追踪

### 2. 现有产品
- **Plaud.ai:** 会议记录（音频为主）
- **Friend AI:** 生活场景记录
- **NUNA:** 情绪追踪pendant
- **Limitation:** 视觉为主的产品较少

### 3. 未来趋势
- **Smart glasses普及** → 视觉成为重要输入模态
- **OpenClaw新纪元** → Agent能力成熟，关键在于了解用户
- **Personalization成为核心** → 越了解用户，agent越有用

## Research Directions

### Option A: 技术导向
**Focus:** 视觉理解算法 + 记忆压缩
- Novel activity recognition for egocentric video
- Multimodal fusion (vision + audio + IMU)
- Memory hierarchy design

### Option B: 系统导向
**Focus:** End-to-end system + Agent integration
- Build complete life logging system
- Integrate with OpenClaw agent
- Demonstrate utility through real use cases

### Option C: 用户导向
**Focus:** 用户体验 + 隐私 + 可接受度
- How much info users are willing to share?
- What aspects of life are most useful for agent?
- Privacy-preserving techniques

## My Bias (Chris)
CMU建筑+HCI+AI多学科背景，倾向于：
- **系统导向**（从应用出发）
- **用户体验**（不仅仅是技术）
- **真实场景**（不是toy dataset）

## Hardware Decision ✅
**Device: Phone camera (现有的)**
- 优势：多模态（video + audio + IMU）、易开发、随身携带、隐私可控
- 具体使用：
  - Camera: 视觉记录（后台录制？periodic capture？）
  - Mic: 环境音频/语音识别
  - IMU: 运动检测、姿态识别
  - GPS/Location: 位置上下文

## Questions to Explore

1. **Scope:** "日常生活"有多宽？
   - ✅ **All-day / 24/7** (全天候覆盖)
   - 包括：home, work, commute, social, leisure, exercise, sleep...
   - 如何定义"有意义的"活动？

2. **Data Collection:** 具体怎么收集？
   - Continuous recording? Periodic snapshots?
   - Battery/隐私如何平衡？
   - 后台限制（iOS/Android）？

3. **Memory:** 存什么？怎么存？
   - Raw video → Compressed embeddings?
   - Summarized text → Structured facts?
   - 保留多久？怎么遗忘？

4. **Agent:** 怎么用？
   - Context-aware prompting?
   - Personalized recommendations?
   - Proactive assistance?

5. **Evaluation:** 怎么衡量成功？
   - Quantitative: Recognition accuracy, compression ratio
   - Qualitative: User satisfaction, utility
   - Comparative: vs baseline (no memory, flat memory)

---

*Last updated: 2026-02-09*
