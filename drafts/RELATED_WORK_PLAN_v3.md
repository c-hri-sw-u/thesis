# Related Work Writing Plan v3

**Created:** 2026-03-11
**Based on:** User feedback + Expert Writing Principles
**Total Length:** ~1,000 words (5 sections × 200 words)

---

## 🎯 核心原则

**Related Work enriches the problem, not demonstrates knowledge.**

- ✅ 精炼叙事：每section 150-200词
- ✅ 突出重点：只讲核心contribution和limitation
- ✅ 创建instability：History → BUT → Gap
- ✅ 为thesis铺路：每个section都指向research gap

---

## 📊 Section Overview

| Section | Length | Key Narrative | Purpose |
|---------|--------|---------------|---------|
| 2.1 LLM Agents → Personal AI | 200w | Evolution + Definition + Promise | Define the space, show importance |
| 2.2 Personalization | 200w | PLLM vs P-for-Agents → Gap in physical context | Show current approaches' limits |
| 2.3 Memory Architectures | 200w | Advanced BUT assume symbolic input | Technical challenge |
| 2.4 Embodied Perception | 200w | Embodied action BUT not observation | Missing piece |
| 2.5 Egocentric Vision | 200w | Mature BUT not integrated | This thesis bridges gap |
| **Total** | **1,000w** | | |

---

## 📝 Section-by-Section Plan

### **2.1 From LLM-Based Agents to Personal AI Agents** (200 words)

#### Structure (3 parts)

**Part 1: Historical Evolution (60 words)**
- Auto-GPT (2023): First LLM-based autonomous agent
- Generative Agents (Park et al., 2023): Simulated believable behavior
- LLM Agents Surveys (Wang et al., 2023; Xi et al., 2023): Established paradigm
- Evolution: experimental → capable multi-domain agents

**Part 2: Defining "Personal AI Agent" (80 words)**
- **This is a new term coined in this thesis**
- Definition: AI agents designed for **long-term, personalized assistance** to individual users
- Key characteristics:
  1. Persistent memory across sessions
  2. Adapts to user preferences over time
  3. Provides proactive, context-aware help
- **Example:** **OpenCLAW** (Steinberger, 2025) - production personal AI agent
  - ⚠️ Note: OpenCLAW is a **product**, not a research paper
  - Represents current SOTA in personal AI agent systems

**Part 3: The Promise + Bridge (60 words)**
- Collective: "These advances show AI agents have moved from research to real-world deployment"
- BUT: "As these systems mature, a critical question emerges: what makes personal agents truly effective?"
- Bridge: "Research increasingly points to **personalization** as the key differentiator"
- Transition to 2.2: "But how exactly does personalization work in current systems?"

#### Key Citations
- Auto-GPT (2023) - historical milestone
- 015 Generative Agents (Park et al., 2023)
- 016 LLM Autonomous Agents Survey (Wang et al., 2023)
- 017 Rise and Potential (Xi et al., 2023)
- 018 OpenCLAW (Steinberger, 2025) - **as SOTA product example**
- 041 Toward Personalized LLM-Powered Agents (2026)

---

### **2.2 Personalization in AI Agents** (200 words)

#### Structure (4 parts)

**Part 1: Early Recognition (40 words)**
- 013 PLLM Survey (Liu et al., 2025): Personalization recognized as crucial for LLMs
- Early work explored: adapting model weights, personalized prompting
- Context: Recommendation systems, personalized text generation

**Part 2: Evolution to Agents (60 words)**
- **As personal AI agents matured** (OpenCLAW 2025, generative agents)
- Research focus shifted: **personalization for agents**
- Papers: 012 PRIME (Wang et al., 2025), 041 Toward Personalized LLM-Powered Agents (2026)
- Focus: Long-term user preferences, persistent memory, adaptive behavior
- Collective: "This evolution shows personalization has become central to agent effectiveness"

**Part 3: What They Achieve (50 words)**
- Current approaches build user models from:
  - Chat logs and interaction history
  - Explicit preferences and feedback
  - Behavioral patterns over time
- Example: "PRIME maintains dual-memory architecture for user-specific cognitive patterns"
- Collective: "These approaches demonstrate that personalization significantly improves agent effectiveness"

**Part 4: The Critical Gap (50 words)**
- **BUT:** "However, all current personalization approaches share a fundamental limitation"
- What they miss:
  - Physical location and environment
  - Real-time activities and focus state
  - Social context and surroundings
- Concrete example (from Intro): "An agent might know your schedule, but not that you're in deep focus work"
- **Anomaly:** "How can agents personalize effectively when they're **blind to the user's physical world**?"
- Bridge to 2.3: "Memory architectures determine what information agents can use—and current systems weren't designed for physical-world input"

#### Key Citations
- 012 PRIME (Wang et al., 2025)
- 013 PLLM Survey (Liu et al., 2025)
- 041 Toward Personalized LLM-Powered Agents (2026)

---

### **2.3 Memory Architectures** (200 words)

#### Structure (3 parts)

**Part 1: Historical Foundation (50 words)**
- Cognitive architectures: 043 Soar (1987), 044 ACT-R (1997)
- Established: hierarchical memory, activation-based retrieval, learning from experience
- Contribution: "These provided theoretical foundations for modern agent memory"

**Part 2: Modern LLM-Based Systems (60 words)**
- 022 MemGPT (2023): Virtual context management, OS-inspired
- 011 Mem0 (2024): Production system, graph-based representation
- 045 Memoria (2025): Scalable hierarchical organization
- 004 Memory Survey (Hu et al., 2025): Comprehensive taxonomy
- Collective: "Modern systems have achieved remarkable scalability and persistence"

**Part 3: The Mismatch (90 words)**
- **BUT:** "All these systems share a critical assumption: input is discrete and symbolic"
- What they expect:
  - Text conversations (low frequency, structured)
  - Discrete events (clear boundaries)
  - Symbolic representations (already processed)
  
- What egocentric vision provides:
  - Continuous video stream (high frequency, raw pixels)
  - Multi-modal data (video + audio + IMU + GPS)
  - No clear event boundaries

- **The Challenge:** "This creates a fundamental mismatch—memory systems designed for text cannot efficiently handle continuous egocentric input"
- Bridge to 2.4: "Memory needs input. For personal agents, this means perceiving the physical world"

#### Key Citations
- 043 Soar (1987)
- 044 ACT-R (1997)
- 022 MemGPT (2023)
- 011 Mem0 (2024)
- 045 Memoria (2025)
- 004 Memory Survey (2025)

---

### **2.4 Embodied Perception** (200 words)

#### Structure (3 parts)

**Part 1: Embodied AI's Focus (70 words)**
- 001 Embodied AI Agents (Fung et al., 2025): Navigation, manipulation, world interaction
- 005 VINCI (2025): Interactive multimodal conversation
- 007 VLM Survey (2024): Vision-language models for perception
- Collective: "Embodied AI has made remarkable progress in agents that perceive and act in physical environments"
- Focus areas: Robot navigation, object manipulation, scene understanding

**Part 2: The Observation Gap (70 words)**
- **BUT:** "This work focuses on agents **acting** in the world, not **observing users**"
- What embodied AI does:
  - Robots navigating environments
  - Agents manipulating objects
  - Multi-agent collaboration in physical spaces

- What it doesn't do:
  - **Passive observation of user behavior**
  - **Long-term user modeling**
  - **Personalization through physical context**

- **Anomaly:** "Robots perceive the physical world, but personal agents don't"

**Part 3: Recent Bridge (60 words)**
- 042 MEMENTO (2025): First to explicitly connect embodied agents and personalization
- Contribution: "Shows potential for combining physical perception with user-specific memory"
- **Limitation:** "However, this remains in early stages, with no concrete systems demonstrating continuous user observation"
- Bridge to 2.5: "Egocentric vision offers a practical approach to embodied observation"

#### Key Citations
- 001 Embodied AI Agents (Fung et al., 2025)
- 005 VINCI (2025)
- 007 VLM Survey (2024)
- 042 MEMENTO (2025)

**Note:** No on-device AI paper (046 was deleted as fake)

---

### **2.5 Egocentric Vision and Self-Logging** (200 words)

#### Structure (3 parts)

**Part 1: Evolution (60 words)**
- Early: 027 SenseCam (2006), 037 MyLifeBits (2006) - passive capture, personal archives
- Datasets: 020 EPIC-KITCHENS (2021), 019 Ego4D (2022) - massive scale, activity recognition
- Collective: "Egocentric vision has evolved from passive lifelogging to sophisticated activity recognition"

**Part 2: Recent Agent Integration (60 words)**
- 003 VideoAgent (2025): Memory-augmented video understanding
- 008 Mem2Ego (2025): Global-to-ego memory for navigation
- 036 EgoLog (2026): Fine-grained daily logging with audio-IMU fusion
- Collective: "Recent work has begun connecting ego-vision to agent systems"

**Part 3: The Integration Gap (80 words)**
- **BUT:** "All these works treat egocentric vision as an **end goal**, not as input for personalization"
- What they focus on:
  - Recognition accuracy (activity detection benchmarks)
  - Navigation success (spatial reasoning)
  - Logging completeness (comprehensive daily records)

- What they don't address:
  - **How ego-vision improves personalization**
  - **Integration into agent memory architectures**
  - **Long-term user modeling from egocentric streams**

- **Quote:** "EgoLog provides continuous logging, but focuses on activity recognition, not agent personalization" (036 EgoLog)

- **This Thesis:** "We bridge this gap by integrating egocentric vision into personal AI agents, asking: what value, if any, does physical-world observation provide for personalization?"

#### Key Citations
- 027 SenseCam (2006)
- 037 MyLifeBits (2006)
- 020 EPIC-KITCHENS (2021)
- 019 Ego4D (2022)
- 003 VideoAgent (2025)
- 008 Mem2Ego (2025)
- 036 EgoLog (2026)

---

## 🎨 Writing Guidelines

### **For Each Section (150-200 words)**

**Pattern A: Evolution → Promise (for 2.1)**
1. Historical evolution (2-3 sentences)
2. Definition/New term (3-4 sentences)
3. Promise + Bridge (2 sentences)

**Pattern B: Achievement → Limitation (for 2.2-2.5)**
1. What the field has achieved (2-3 sentences)
2. BUT what they miss (3-4 sentences)
3. Why this matters (2 sentences)

### **Sentence-level Tips**

✅ **Use collective conclusions:**
- "Together, these approaches show..."
- "This body of work demonstrates..."
- "Collectively, these advances indicate..."

✅ **Use strategic BUT:**
- "However, all current approaches share..."
- "Yet these systems assume..."
- "But what about..."

✅ **Make community the subject:**
- "Personalization research has recognized..."
- "Memory architecture work has achieved..."
- "Embodied AI has focused on..."

❌ **Avoid:**
- Definition-first openings
- Detailed paper summaries
- "There is a gap in the literature"

---

## ✅ Success Criteria

Each section succeeds when readers:
1. ✅ Understand the **key contribution** of that research area
2. ✅ See the **fundamental limitation** that creates instability
3. ✅ Feel why **this thesis is needed**
4. ✅ Can read it in **1-2 minutes** (150-200 words)

**Overall Related Work succeeds when:**
- Total reading time: 10-15 minutes (1,000 words)
- Reader thinks: "Physical context for personalization is an obvious gap"
- Reader asks: "How will this thesis solve it?"

---

## 📊 Word Count Tracking

| Section | Target | Draft | Status |
|---------|--------|-------|--------|
| 2.1 LLM Agents | 200w | - | ⏳ To write |
| 2.2 Personalization | 200w | - | ⏳ To write |
| 2.3 Memory | 200w | - | ⏳ To write |
| 2.4 Embodied | 200w | - | ⏳ To write |
| 2.5 Egocentric | 200w | - | ⏳ To write |
| **Total** | **1,000w** | **0w** | **0%** |

---

## 🎯 Key Changes from v2

1. **Length:** 3,500w → 1,000w (75% reduction)
2. **2.1 Structure:** Evolution + Definition + Promise (3 clear parts)
3. **OpenCLAW Treatment:** Product example, not paper; SOTA reference
4. **2.2 Distinction:** PLLM vs P-for-Agents clearly separated
5. **2.4 Update:** Removed on-device AI (deleted as fake paper)
6. **Personal AI Agent:** Explicitly stated as **new term coined in this thesis**

---

## 📝 Execution Plan

**Day 1-2:** Write 2.5 (Egocentric Vision) - closest to contribution
**Day 3-4:** Write 2.3 (Memory) - technical foundation
**Day 5-6:** Write 2.4 (Embodied) - connects ego-vision to agents
**Day 7-8:** Write 2.2 (Personalization) - problem importance
**Day 9-10:** Write 2.1 (LLM Agents) - context and definition
**Day 11-12:** Review all sections for coherence
**Day 13-14:** Final polish and transitions

**Total: 2 weeks**

---

**Plan Status:** Ready to execute
**Next Action:** Start with Section 2.5 (Egocentric Vision)
