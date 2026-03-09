# Related Work Writing Plan v2

**Based on:** READING_COMPLETION_REPORT.md + Expert Writing Principles
**Created:** 2026-03-08
**Status:** Ready to execute

---

## 🎯 Core Goal

**Related Work enriches the problem, not demonstrates knowledge.**

### Writing Philosophy

**Instability is a tool, not a rule.**

✅ **Use instability when:**
- Pointing out genuine limitations
- Creating narrative tension
- Highlighting why this thesis matters

✅ **Use collective conclusions when:**
- Summarizing a body of work
- Building toward the next point
- Showing evolution/progress

**Examples:**
- "Collectively, these studies highlight the promise of X in Y"
- "This body of work demonstrates that Z is critical"
- "Together, these approaches show..."
- "As these systems mature, a key question emerges..."

### Section Goals
- **2.1:** Show agent evolution → leads to personalization need
- **2.2:** Show how personalization works → BUT limited to digital traces
- **2.3:** Show memory systems → BUT assume discrete input
- **2.4:** Show embodied perception → BUT focus on action
- **2.5:** Show ego-vision mature → BUT not integrated into agents

---

## 📊 Section Overview

| Section | Papers | Length | Narrative Flow |
|---------|--------|--------|----------------|
| 2.1 LLM Agents → Personal AI | 9 | 800w | Evolution of agent capabilities → leads to personalization need |
| 2.2 Personalization | 4 | 600w | Personalization is critical → **BUT limited to digital traces** |
| 2.3 Memory Architectures | 16 | 700w | Memory systems are advanced → **BUT assume discrete symbolic input** |
| 2.4 Embodied Perception | 6 | 600w | Embodied agents perceive physical world → **BUT focus on action** |
| 2.5 Egocentric Vision | 7 | 800w | Ego-vision is mature → **BUT not integrated into agents** |
| **Total** | **43** | **3,500w** | |

**Key Principle:** Not every paragraph needs instability. Collective conclusions are valuable:
- ✅ "Collectively, these studies highlight the promise of X in Y"
- ✅ "This body of work demonstrates that Z is critical"
- ✅ "Together, these approaches show..."

---

## 📝 Section-by-Section Plan

### **2.1 From LLM-Based Agents to Personal AI Agents**

#### Narrative Flow
**Focus:** Evolution of agent capabilities and architectures
**Leads to:** Recognition that personalization is critical for effectiveness
**Transition to 2.2:** "As these agents become more capable, personalization emerges as the key challenge"

#### Paragraph Breakdown

**P1: Evolution (200 words)**
- **Opening:** "LLM-based agents have moved from experimental projects..."
- **Evidence:**
  - **015 Generative Agents (2023):** "Simulates believable human behavior using LLM"
  - **016 LLM Agents Survey (2023):** "LLM-based autonomous agents represent a new paradigm"
  - **017 Rise and Potential (2023):** "Demonstrated remarkable capabilities in complex reasoning"
- **Collective conclusion:** "Collectively, these works demonstrate that LLM-based agents can maintain coherent behavior, plan multi-step actions, and interact naturally with users"

**P2: Production Systems (200 words)**
- **Transition:** "This evolution has reached production systems..."
- **Evidence:**
  - **018 OpenCLAW (2025):** "Production-ready personal AI agent system"
  - **040 Long-term Interactions (2025):** "Persistent memory across sessions"
- **Quote:** "OpenCLAW demonstrates practical deployment of personal agents" (018 OpenCLAW)
- **Bridge:** "As these systems mature, a key question emerges: what makes personal agents truly effective?"

**P3: The Answer (200 words)**
- **Response:** "Research increasingly points to personalization as the critical factor..."
- **Evidence:**
  - **041 Personalized LLM-Powered Agents (2026):** "Latest taxonomy on personalization"
  - **042 MEMENTO (2025):** "Embodied agents meet personalization"
- **Quote:** "Personalization effectiveness depends on user model richness" (013 PLLM Survey)
- **Lead to 2.2:** "The next section examines how personalization works in current systems"

**P4: Recent Recognition (200 words)**
- **Observation:** "Recent work has begun recognizing the importance of physical context..."
- **Evidence:**
  - **042 MEMENTO (2025):** First to explicitly connect embodied agents and personalization
- **However:** "This work is in early stages and provides no concrete systems"
- **Transition:** "To understand why physical context matters, we must first examine current personalization approaches"

#### Key Citations
- 015 Generative Agents (Park et al., 2023)
- 016 LLM Agents Survey (Wang et al., 2023)
- 017 Rise and Potential (Xi et al., 2023)
- 018 OpenCLAW (Steinberger, 2025)
- 040 Long-term Interactions (2025)
- 041 Personalized LLM-Powered Agents (2026)
- 042 MEMENTO (2025)

---

### **2.2 Personalization in AI Agents**

#### Narrative Flow
**Focus:** How personalization currently works
**Key Instability:** Current approaches only use digital traces → miss physical context
**Leads to:** Question of what information sources are available

#### Paragraph Breakdown

**P1: Why Personalization Matters (200 words)**
- **Opening:** "Personalization has become central to AI agent effectiveness..."
- **Evidence:**
  - **013 PLLM Survey (2025):** "Personalized LLMs have emerged as crucial direction"
  - **012 PRIME (2025):** "Dual-memory system for personalized thought processes"
- **Quote:** "An agent's effectiveness depends on the richness and accuracy of its user model" (013 PLLM Survey)
- **Collective conclusion:** "Together, these works establish personalization as essential for agent effectiveness"

**P2: How It Works (200 words)**
- **Transition:** "Current personalization approaches build user models from..."
- **Evidence:**
  - **012 PRIME (2025):** "Hierarchical memory with cognitive and semantic layers"
  - **023 O-Mem (2025):** "Active user profiling from interactions"
- **What's captured:** Chat logs, preferences, interaction patterns
- **Quote:** "PRIME enables personalized thought processes through dual-memory architecture" (012 PRIME)

**P3: The Limitation (200 words)**
- **BUT:** "However, these approaches share a critical limitation..."
- **What they miss:** Physical location, activities, environment, focus state
- **Concrete example (from Intro):** "Agent sends recommendation based on schedule, but doesn't know you're in deep focus"
- **Quote:** "Current personal AI agents build these models entirely from digital traces" (Intro v5)
- **Anomaly:** "How can agents personalize effectively when they don't know where the user is or what they're doing?"

**P4: The Information Gap (100 words)**
- **Observation:** "This raises the question: what information sources are available beyond digital traces?"
- **Lead to 2.3:** "Memory architectures determine what information agents can use and how"

#### Key Citations
- 012 PRIME (Wang et al., 2025)
- 013 PLLM Survey (Liu et al., 2025)
- 038 Personalization: A Taxonomy (Blom, 2000)
- 041 Personalized LLM-Powered Agents (2026)

---

### **2.3 Memory Architectures - The Foundation**

#### Narrative Flow
**Focus:** How memory systems work and what they assume
**Key Instability:** Designed for symbolic discrete input → challenge for continuous multi-modal
**Leads to:** Question of how to handle egocentric stream

#### Paragraph Breakdown

**P1: Historical Foundation (200 words)**
- **Opening:** "Memory architectures provide the foundation for agent persistence..."
- **Evidence:**
  - **043 Soar (1987):** "Architecture for general intelligence"
  - **044 ACT-R (1997):** "Theory of higher level cognition"
- **Contribution:** "These established hierarchical memory as essential for intelligent behavior"
- **Quote:** "Soar provides a unified architecture for general intelligence" (043 Soar)

**P2: Modern LLM-Based Systems (200 words)**
- **Evolution:** "Modern systems have adapted these principles for LLMs..."
- **Evidence:**
  - **022 MemGPT (2023):** "Virtual context management with hierarchical memory"
  - **011 Mem0 (2024):** "Production-ready with 91% lower latency"
  - **045 Memoria (2025):** "Scalable agentic memory framework"
- **Quote:** "Persistent memory mechanisms for long-term conversational coherence" (011 Mem0)
- **Collective:** "Together, these systems demonstrate scalable, persistent memory"

**P3: What They Assume (200 words)**
- **BUT:** "However, these systems share a common assumption..."
- **What they expect:**
  - Discrete events
  - Text or structured data
  - Low-frequency updates
- **Quote:** "Memory systems handle symbolic input well" (004 Memory Survey)
- **The mismatch:** Egocentric vision provides continuous, high-frequency, multi-modal stream

**P4: Recent Multimodal Memory (100 words)**
- **Bridge:** "Recent work has begun addressing multimodal memory..."
- **Evidence:**
  - **003 VideoAgent (2025):** "Memory-augmented multimodal agent"
  - **008 Mem2Ego (2025):** "Egocentric memory for navigation"
- **Observation:** "These show video memory is possible, but focus on understanding not personalization"
- **Lead to 2.4:** "Memory needs input - where does this input come from?"

#### Key Citations
- 043 Soar (1987)
- 044 ACT-R (1997)
- 022 MemGPT (2023)
- 011 Mem0 (2024)
- 045 Memoria (2025)
- 003 VideoAgent (2025)
- 008 Mem2Ego (2025)
- 004 Memory Survey (2025)

---

### **2.4 Embodied Perception - The Missing Piece**

#### Narrative Flow
**Focus:** What embodied AI has achieved
**Key Observation:** Focuses on action/robotics, not passive observation
**Leads to:** Question of what embodied observation could provide

#### Paragraph Breakdown

**P1: Embodied AI (200 words)**
- **Opening:** "Embodied AI research has focused on agents that interact with the physical world..."
- **Evidence:**
  - **001 Embodied AI Agents (2025):** "Understand and interact with physical world"
  - **005 VINCI (2025):** "Interactive multimodal conversation with visual grounding"
- **Quote:** "Embodied AI agents must understand and interact with the physical world" (001)
- **What they do:** Navigation, manipulation, environment understanding

**P2: Perception Capabilities (200 words)**
- **Observation:** "These agents rely on sophisticated perception systems..."
- **Evidence:**
  - **007 VLM Survey (2024):** "Vision-language models bridge modalities"
  - **006b On-Device AI (2024):** "Edge deployment challenges"
- **Quote:** "VLMs have achieved remarkable success in multimodal understanding" (007 VLM Survey)
- **Collective:** "Together, these show agents can perceive and reason about physical environments"

**P3: The Focus (100 words)**
- **Observation:** "However, embodied AI focuses on agents acting in the world..."
- **What they study:** Robots navigating, manipulating objects
- **What they don't study:** Passive observation of user's environment
- **Anomaly:** "Robots perceive the physical world, but personal agents don't"

**P4: Recent Bridge (100 words)**
- **Recent work:**
  - **042 MEMENTO (2025):** "Embodied agents meet personalization"
- **Quote:** "First to explicitly connect embodied agents and personalization" (042 MEMENTO)
- **However:** "Still in early stages, provides no concrete systems"
- **Lead to 2.5:** "Egocentric vision offers a practical approach to embodied observation"

#### Key Citations
- 001 Embodied AI Agents (2025)
- 005 VINCI (2025)
- 007 VLM Survey (2024)
- 042 MEMENTO (2025)
- 006b On-Device AI (2024)

---

### **2.5 Egocentric Vision and Self-Logging**

#### Narrative Flow
**Focus:** Evolution of egocentric vision capabilities
**Key Instability:** Mature for recognition → BUT not integrated into agent systems
**Conclusion:** This thesis bridges the gap

#### Paragraph Breakdown

**P1: Early Vision (200 words)**
- **Opening:** "The vision of capturing personal experience has a long history..."
- **Evidence:**
  - **027 SenseCam (2006):** "Wearable camera for automatic lifelogging"
  - **037 MyLifeBits (2006):** "Personal database fulfilling Memex vision"
- **Quote:** "SenseCam enables automatic lifelogging without user intervention" (027)
- **Collective:** "These established continuous capture as feasible and valuable"

**P2: Recognition Focus (200 words)**
- **Evolution:** "Modern egocentric vision has achieved remarkable scale..."
- **Evidence:**
  - **020 EPIC-KITCHENS (2021):** "100 hours, 20M frames, 90K actions"
  - **019 Ego4D (2022):** "3,000 hours from 874 participants worldwide"
- **Quote:** "Largest first-person dataset to date" (020 EPIC-KITCHENS)
- **Collective:** "Together, these datasets have driven significant advances in activity recognition, object interaction, and scene understanding"

**P3: Recent Agent Integration (200 words)**
- **Recent work:** "Recent work has begun connecting ego-vision to agents..."
- **Evidence:**
  - **036 EgoLog (2026):** "Ego-centric daily logging with LLM integration"
  - **008 Mem2Ego (2025):** "Egocentric memory for navigation"
  - **003 VideoAgent (2025):** "Memory-augmented multimodal agent"
- **Quote:** "EgoLog provides continuous logging with audio-IMU fusion" (036 EgoLog)
- **Observation:** "These show agent integration is possible"

**P4: The Gap (200 words)**
- **BUT:** "However, these works treat egocentric vision as end goals..."
- **What they focus on:** Recognition accuracy, logging completeness, navigation success
- **What they don't address:**
  - How ego-vision improves personalization
  - Integration into agent memory architectures
  - Long-term user modeling from ego-streams
- **Quote:** "EgoLog focuses on daily logs, not agent personalization" (036 EgoLog)

**P5: This Thesis (100 words)**
- **Contribution:** "This thesis addresses this gap by integrating egocentric vision into personal AI agents"
- **What it provides:**
  1. System integrating ego-vision into OpenClaw's memory
  2. Design requirements for continuous sensing
  3. Empirical findings on where physical context helps personalization
- **Lead to Chapter 3:** System Design

#### Key Citations
- 027 SenseCam (2006)
- 037 MyLifeBits (2006)
- 020 EPIC-KITCHENS (2021)
- 019 Ego4D (2022)
- 036 EgoLog (2026)
- 008 Mem2Ego (2025)
- 003 VideoAgent (2025)

---

## 🎨 Writing Techniques Checklist

### From Expert Writing Skill

**✅ Use Strategically:**

**Instability Words (for genuine limitations):**
- BUT, HOWEVER, ALTHOUGH, NEVERTHELESS
- ANOMALY, INCONSISTENCY, PARADOX
- REMAINS UNKNOWN, UNEXPLORED, LIMITED TO

**Collective Conclusion Words (for building narrative):**
- "Collectively, these studies..."
- "This body of work demonstrates..."
- "Together, these approaches..."
- "As these systems mature..."

**Community Signals:**
- "widely recognized", "reported in", "accepted understanding"
- NOT: "I found that", "This paper says"

**Subject Strategy:**
- Make community's work the subject
- "Personalization research has focused on..." (not "Many papers have...")

**Sentence Length Variation:**
- Mix short (stress) + medium (flow) + long (elaboration)

### Paragraph Patterns

**Pattern A: Evolution → Recognition**
1. What the field has achieved
2. What this demonstrates
3. What question emerges

**Pattern B: Achievement → Limitation**
1. What approaches do well
2. BUT what they miss
3. Why this matters

**Pattern C: Foundation → Build**
1. What foundational work established
2. How recent work extends it
3. What this thesis contributes

### What to AVOID

**❌ Gap in knowledge:**
- NOT: "There's a gap in the literature..."
- YES: "However, this approach assumes..."

**❌ Literature summaries:**
- NOT: "Park et al. did X. Wang et al. did Y."
- YES: "Personalization research has evolved from X to Y, BUT..."

**❌ Definition-first:**
- NOT: "Personal AI agents are defined as..."
- YES: "An emerging class of AI system has moved from experimental to daily use..."

**❌ Explaining everything:**
- NOT: Detailed explanations of each paper
- YES: Strategic citations to build argument

---

## 📊 Execution Plan

### Phase 1: Draft Each Section (5 days)
- **Day 1:** Section 2.5 (Egocentric Vision) - start with closest to contribution
- **Day 2:** Section 2.3 (Memory) - technical foundation
- **Day 3:** Section 2.4 (Embodied) - connects ego-vision to agents
- **Day 4:** Section 2.2 (Personalization) - shows problem importance
- **Day 5:** Section 2.1 (LLM Agents) - provides context

### Phase 2: Revise (2 days)
- **Day 6:** Review all sections for instability flow
- **Day 7:** Check citations, quotes, coherence

### Phase 3: Integrate (1 day)
- **Day 8:** Ensure Related Work → System Design transition is smooth

---

## ✅ Success Criteria

Related Work succeeds when readers:
1. ✅ Feel the urgency of the problem
2. ✅ Understand why current approaches are limited
3. ✅ Are convinced that physical context matters
4. ✅ Are curious about the solution
5. ✅ Are NOT bored by literature summary

---

## 📁 File Locations

**Input:**
- `thesis/papers/unified-index.md` - all notes & quotes
- `thesis/drafts/intro-v5.md` - core problem statement
- `thesis/drafts/framework.md` - research questions

**Output:**
- `thesis/drafts/related-work-v1.md` - first draft
- Save each section as separate file during drafting

---

**Plan Created:** 2026-03-08 16:35 EST
**Status:** Ready to execute
**Estimated Time:** 8 days (5 days drafting + 2 days revision + 1 day integration)
