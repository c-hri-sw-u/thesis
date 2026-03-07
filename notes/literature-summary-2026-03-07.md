# Literature Summary - March 7, 2026

## Research Direction

**My Focus:** 
- 超越"分类"，做"理解"
- 可查询、可检索、可推理的个人记忆系统
- Agent作为主动参与者
- 多维度人生日志

---

## Categories

### 1. Self-log (Life Logging)

**Classic:**
- **MyLifeBits** (2000s) - 最经典的self-log
- **EgoLog** (2026) - HAR为主，但强调连续追踪+多模态传感+AI辅助

**Key Insight:**
- 现有系统重在"记录"和"分类"
- 我要做"理解"和"主动agent"

---

### 2. Self-study / Autoethnography (方法论)

**Core Paper:**
- **Autobiographical design** (Neustaedter & Sengers, 2012) - DIS 2012

**Legitimacy Strategies:**
1. **Depth over breadth**: "I studied myself in DEPTH for X years"
2. **Insider expertise**: Unique access to subtle experiences
3. **Generalizability through transparency**: Detailed reporting
4. **Methodological rigor**: Clear documentation, reflexive analysis, peer debriefing
5. **Theoretical contribution**: Connect to broader HCI theories
6. **Artifact creation**: Build tools that others can use

**Guidelines:**
- **Transparency**: Explicitly state designing for yourself
- **Critical reflection**: Examine biases and position
- **Generalization**: How findings apply beyond yourself
- **Validation**: Supplement with other methods when possible

---

### 3. Personalization

**Framework:**
- **know**: memory, profile - 识别什么对用户更重要
- **do**: planning, thinking, action - 输出更符合用户预期

**HCI Perspective:**
- **Personalization: a taxonomy** (2000) - Personalization = changing a system to increase personal relevance
- **What Is Personalization?** (2010) - Customization: 用户主动修改系统 (agency)

**PLLM (Personalized LLM):**
- **Survey of PLLM** (2025) - 三个level:
  - **Input Level**: Personalized Prompting
  - **Model Level**: Personalized Adaptation (Fine-tuning)
  - **Objective Level**: Personalized Alignment
  
  核心挑战: understanding individual emotions, writing styles, preferences

---

### 4. Agent Memory Systems

#### Non-embodied Agents

**PRIME** (2025):
- Cognitive dual-memory: **Episodic Memory** + **Semantic Memory**
- **Personalized Thinking**: 慢思考策略 + self-distillation
- Key finding: Semantic > Episodic (更robust)

**Persistent Memory + User Profiles** (2025):
- Four modules:
  1. **Persistent memory**: STM → summaries → LTM → user profile
  2. **Dynamic coordination**: multi-agent协作
  3. **Self-validation**: agent自检一致性
  4. **Evolving user profiles**: 持续更新

**Toward Personalized LLM-Powered Agents** (2026):
- **Profile modeling**: explicit vs implicit preferences
- **Memory**: STM/LTM/episodic/semantic分层
- **Planning**: 将用户偏好编码进目标函数
- **Action execution**: 工具使用中的personalization

#### Embodied Agents

**MEMENTO** (2026):
- 问题: Agent在user patterns上失败，两大瓶颈:
  - **Information overload**: 记忆太多检索退化
  - **Coordination failures**: 综合多条记忆时崩溃
  
- Solution: **Hierarchical knowledge graph-based user profile**
  - 顶层: Users
  - 中间: Knowledge Types (object semantics, user patterns)
  - 底层: Elements (objects, patterns, locations)
  
- 关键: **预提取、预结构化**个人化知识到profile

#### OpenClaw's Approach

**Identity Layer** (2026):
- **SOUL.md**: personality, values, communication style, behavioral boundaries
- **USER.md**: 用户个人信息、偏好
- **IDENTITY.md**: agent外在身份

**Two-tier Memory** (2026):
- **Ephemeral Memory**: `memory/YYYY-MM-DD.md` (daily log, append-only)
- **Durable Memory**: `MEMORY.md` (curated long-term, private only)
- Philosophy: **Files are the source of truth**

---

### 5. Cognitive Architectures

**Classics:**
- **Soar** (1987):
  - Four memories: working, procedural, semantic, episodic
  - Base-level activation (BLA) for retention
  
- **ACT-R** (1993):
  - **Activation-based retrieval**: recency + frequency + spreading activation
  - Memory decay防止无限累加

**Modern:**
- **Generative Agents** (2023):
  - Memory stream (append-only)
  - Retrieval: recency + importance + relevance
  - Reflection: 周期性合成higher-level abstractions
  
- **MemGPT** (2023):
  - **Virtual context management** (OS paging)
  - Core memory (in-context, RAM)
  - Archival memory (out-of-context, disk)
  - **Self-editing memory** via tool calling
  
- **Mem0** (2025):
  - **Memory-as-a-service**: independent layer
  - Memory extraction and consolidation
  - Graph-based representation (enhanced)
  
- **A-MEM** (2025):
  - Zettelkasten-inspired
  - Agent自主组织记忆关系
  
- **Memoria** (2025):
  - Dynamic session-level summarization
  - Weighted knowledge graph-based user modeling

**Survey:**
- **Memory in the Age of AI Agents** (2025) - 最全面的survey

---

## Key Insights for My Thesis

### 1. Memory Architecture
**Decision:** 
- Ephemeral + Durable (OpenClaw's approach)
- Episodic + Semantic (PRIME's dual-memory)
- Graph-based user profile (MEMENTO's solution to overload)

### 2. Personalization Strategy
**Decision:**
- **Input Level**: Retrieval-augmented prompting (RAG)
- **Model Level**: Optional PEFT per user (if needed)
- **Objective Level**: Focus on user preference alignment

### 3. Self-study Methodology
**Decision:**
- Follow Neustaedter & Sengers (2012) guidelines
- All 6 legitimacy strategies
- Critical reflection + transparency

### 4. Differentiation from Existing Work

| System | Focus | My Differentiation |
|--------|-------|-------------------|
| EgoLog | HAR + classification | **Understanding + agent integration** |
| PRIME | Non-embodied personalization | **Embodied + life logging context** |
| MEMENTO | Embodied agent memory | **Self-study + longitudinal** |
| OpenClaw | File-based memory | **Formal evaluation + cognitive framework** |

---

## Research Gap

**Missing:**
1. **Long-term self-study** of life logging + agent memory (most are short-term user studies)
2. **Integration** of cognitive theory + agent memory + personalization in embodied context
3. **Privacy-by-design** life logging system with formal evaluation

**My Contribution:**
1. **System artifact**: Privacy-first life logging with agent memory
2. **Empirical findings**: Long-term self-study (3 weeks)
3. **Design implications**: Guidelines for personalized life logging agents

---

## Next Steps

1. Finalize research questions (RQ1, RQ2, RQ3)
2. Complete system design
3. Begin self-study (7 days minimum)
4. Write related work section

---

*Last updated: 2026-03-07*
