# 论文精读任务分解

**目标：** 为每个topic下的论文填充Notes和Quotes列
**方法：** 5个独立的subagent任务，每个处理一个topic

---

## Task 1: Topic 2.1 - LLM-Based Agents → Personal AI Agents

**论文数量：** 9篇

### 论文列表
1. **015** Generative Agents (2023) - Park et al.
2. **016** LLM Autonomous Agents Survey (2023) - Wang et al.
3. **017** Rise and Potential of LLM Agents (2023) - Xi et al.
4. **001** Embodied AI Agents (2025) - Fung et al.
5. **005** VINCI (2025) - Huang et al.
6. **018** OpenCLAW (2025) - Steinberger
7. **040** Enabling Personalized Long-term Interactions (2025)
8. **041** Toward Personalized LLM-Powered Agents (2026)
9. **042** MEMENTO (2025) - Kwon et al.

### 任务要求
- 精读每篇PDF
- Notes：50-100字，总结核心贡献
- Quotes：1-2个可直接引用的关键句
- 更新unified-index.md第12-20行

### Writing Focus
**Instability to create:**
- History: LLM agents evolved from experimental → production
- BUT: As they become more personalized, they remain blind to physical world
- Why it matters: Personalization effectiveness depends on user model richness

---

## Task 2: Topic 2.2 - Personalization in AI Agents

**论文数量：** 4篇

### 论文列表
1. **038** Personalization: A Taxonomy (2000) - Blom
2. **012** PRIME (2025) - Wang et al.
3. **013** PLLM Survey (2025) - Liu et al.
4. **041** Toward Personalized LLM-Powered Agents (2026)

### 任务要求
- Notes：50-100字，总结核心贡献
- Quotes：1-2个可直接引用的关键句
- 更新unified-index.md第13, 24-25, 62行

### Writing Focus
**Instability to create:**
- History: Personalization recognized as critical
- BUT: Current approaches only use digital traces
- Anomaly: How can agents personalize without knowing user's physical situation?

---

## Task 3: Topic 2.3 - Memory Architectures

**论文数量：** 16篇

### 论文列表
1. **043** Soar (1987) - Laird et al.
2. **044** ACT-R (1997) - Anderson et al.
3. **022** MemGPT (2023)
4. **006** MARC (2024) - Wu et al.
5. **011** Mem0 (2024) - He et al.
6. **002** MemVerse (2025) - Liu et al.
7. **003** VideoAgent (2025) - Ma et al.
8. **004** Memory Survey (2025) - Hu et al.
9. **008** Mem2Ego (2025) - Zhang et al.
10. **009** Long-term Memory (2025) - Wang et al.
11. **010** A-MEM (2025)
12. **012** PRIME (2025) - Wang et al.
13. **023** O-Mem (2025)
14. **045** Memoria (2025) - Sarin et al.

### 任务要求
- Notes：50-100字，总结核心贡献
- Quotes：1-2个可直接引用的关键句
- 更新unified-index.md第7-11, 13, 21-23, 44-45行

### Writing Focus
**Instability to create:**
- History: Memory evolved from cognitive architectures to LLM-based
- BUT: All assume discrete, symbolic input
- Challenge: How to handle continuous, multi-modal egocentric input?

---

## Task 4: Topic 2.4 - Embodied Perception

**论文数量：** 6篇

### 论文列表
1. **006b** On-Device AI (2024)
2. **007** VLM Survey (2024) - Lin et al.
3. **021** MDGEAR (2024) - Papadakis & Spyrou ❌ (无法下载)
4. **001** Embodied AI Agents (2025) - Fung et al.
5. **005** VINCI (2025) - Huang et al.
6. **042** MEMENTO (2025) - Kwon et al.

### 任务要求
- Notes：50-100字，总结核心贡献
- Quotes：1-2个可直接引用的关键句
- 更新unified-index.md第8, 9, 15, 20, 41行

### Writing Focus
**Instability to create:**
- History: Embodied AI focused on robotics, navigation
- BUT: What about embodied observation for personalization?
- Anomaly: Robots perceive physical world, personal agents don't

---

## Task 5: Topic 2.5 - Egocentric Vision and Self-Logging

**论文数量：** 8篇

### 论文列表
1. **027** SenseCam (2006) - Hodges et al.
2. **037** MyLifeBits (2006) - Gemmell et al.
3. **020** EPIC-KITCHENS (2021) - Damen et al.
4. **019** Ego4D (2022) - Grauman et al.
5. **021** MDGEAR (2024) - Papadakis & Spyrou ❌ (无法下载)
6. **003** VideoAgent (2025) - Ma et al.
7. **008** Mem2Ego (2025) - Zhang et al.
8. **036** EgoLog (2026)

### 任务要求
- Notes：50-100字，总结核心贡献
- Quotes：1-2个可直接引用的关键句
- 更新unified-index.md第19-21, 27, 36-37, 3, 8行

### Writing Focus
**Instability to create:**
- History: Ego-vision focused on activity recognition
- BUT: Treated as end goal, not integration into agent systems
- Missing: How to integrate ego-vision into agent memory for personalization?

---

## 执行策略

### Option A: 顺序执行（推荐）
- 一次spawn 1个subagent
- 完成一个topic后再spawn下一个
- 避免API rate limit
- 更容易追踪进度

### Option B: 并行执行
- 同时spawn 5个subagents
- 更快完成
- 可能遇到rate limit

### 建议
采用Option A，按以下顺序：
1. **Task 5** (Egocentric Vision) - 最接近thesis contribution
2. **Task 3** (Memory) - 技术挑战
3. **Task 4** (Embodied) - 连接ego-vision和agents
4. **Task 2** (Personalization) - 展示问题重要性
5. **Task 1** (LLM Agents) - 提供context和history

---

## 输出格式

### Notes列格式
```
[核心贡献1句话] + [关键技术/方法] + [与thesis相关性]
```

示例：
```
"Proposes hierarchical memory system for LLMs (main context + external context). Introduces memory management inspired by OS virtual memory. Relevance: Memory architecture pattern for egocentric input integration."
```

### Quotes列格式
```
> "[原文引用]" (p. X)
```

示例：
```
> "Personal AI agents must maintain persistent memory across sessions" (p. 3)
```

---

## 进度追踪

完成后更新此文件：
- [ ] Task 1: LLM-Based Agents (9 papers)
- [ ] Task 2: Personalization (4 papers)
- [ ] Task 3: Memory (16 papers)
- [ ] Task 4: Embodied (6 papers)
- [ ] Task 5: Egocentric Vision (8 papers)

**总计：43篇论文** (excluding 021 MDGEAR - 无法下载)

---

**创建时间：** 2026-03-08 16:20 EST
