# Related Work Writing Plan v2

**Based on:** READING_COMPLETION_REPORT.md + Expert Writing Principles
**Created:** 2026-03-08
**Status:** Ready to execute

---

## 🎯 Core Goal

**Related Work enriches the problem, not demonstrates knowledge.**

Every section should make the reader feel:
- "This problem is urgent"
- "Current approaches are limited"
- "This thesis fills a critical gap"

---

## 📊 Section Overview

| Section | Papers | Length | Instability Focus |
|---------|--------|--------|-------------------|
| 2.1 LLM Agents → Personal AI | 9 | 800w | Evolution → BUT blind to physical world |
| 2.2 Personalization | 4 | 600w | Recognized → BUT limited to digital traces |
| 2.3 Memory Architectures | 16 | 700w | Advanced → BUT assume symbolic input |
| 2.4 Embodied Perception | 6 | 600w | Embodied AI → BUT focused on action not observation |
| 2.5 Egocentric Vision | 7 | 800w | Mature → BUT not integrated into agents |
| **Total** | **43** | **3,500w** | |

---

## 📝 Section-by-Section Plan

### **2.1 From LLM-Based Agents to Personal AI Agents**

#### Instability Structure
**History:** LLM agents evolved from experimental → production
**BUT:** As they become personalized, they remain blind to physical world
**Why it matters:** Personalization effectiveness depends on user model richness

#### Paragraph Breakdown

**P1: Evolution (200 words)**
- **Opening:** "LLM-based agents have moved from experimental projects..."
- **Evidence:**
  - **015 Generative Agents (2023):** "Simulates believable human behavior using LLM"
  - **016 LLM Agents Survey (2023):** "LLM-based autonomous agents represent a new paradigm"
  - **017 Rise and Potential (2023):** "Demonstrated remarkable capabilities in complex reasoning"
- **BUT:** "However, these agents operate in simulated or digital environments..."
- **Instability word:** "However", "remain limited to"

**P2: Production Systems (200 words)**
- **Transition:** "This evolution has reached production systems..."
- **Evidence:**
  - **018 OpenCLAW (2025):** "Production-ready personal AI agent system"
  - **040 Long-term Interactions (2025):** "Persistent memory across sessions"
- **BUT:** "Yet these systems build user models entirely from digital traces"
- **Quote:** "Personalization effectiveness depends on user model richness" (013 PLLM Survey)
- **Instability:** "remain blind to", "limited to"

**P3: The Problem (200 words)**
- **Anomaly:** "This creates a critical limitation"
- **Concrete example (from Intro):** Focus work interruption at 3pm
- **Quote:** "Current personal AI agents build these models entirely from digital traces" (Intro v5)
- **Question:** "How can agents personalize effectively when they don't know where the user is or what they're doing?"
- **Setup for next section:** Personalization is the goal, BUT current approaches are limited

**P4: Recent Advances (200 words)**
- **Bridge:** "Recent work has begun addressing this gap..."
- **Evidence:**
  - **041 Personalized LLM-Powered Agents (2026):** "Latest taxonomy"
  - **042 MEMENTO (2025):** "Embodied agents meet personalization"
- **BUT:** "These works recognize the problem, but don't provide concrete solutions"
- **Lead to 2.2:** Personalization as the core challenge

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

#### Instability Structure
**History:** Personalization recognized as critical for agent effectiveness
**BUT:** Current approaches only use digital traces
**Anomaly:** How can agents personalize without knowing user's physical situation?

#### Paragraph Breakdown

**P1: Importance (200 words)**
- **Opening:** "Personalization has become central to AI agent effectiveness..."
- **Evidence:**
  - **013 PLLM Survey (2025):** "Personalized LLMs have emerged as crucial direction"
  - **012 PRIME (2025):** "Dual-memory personalization for AI agents"
- **Quote:** "Personalization is critical for adapting to individual users, preferences, and contexts" (013 PLLM Survey)
- **BUT:** "However, current personalization approaches are limited to digital traces..."

**P2: What's Missing (200 words)**
- **Anomaly:** "This creates a fundamental limitation"
- **What digital traces capture:** Chat logs, files, calendars
- **What they miss:** Physical location, activities, environment, focus state
- **Concrete example (from Intro):** "Agent doesn't know you're in deep focus work"
- **Quote:** "Current personal AI agents build these models entirely from digital traces" (013 PLLM Survey)

**P3: Taxonomy (200 words)**
- **History:** "Personalization research has developed taxonomies..."
- **Evidence:**
  - **038 Personalization: A Taxonomy (2000):** "Process of changing a system to increase personal relevance"
  - **039 What Is Personalization:** Perspectives on design
- **BUT:** "These frameworks assume information is already available digitally"
- **Gap:** "No framework addresses how to obtain physical-world information"

**P4: The Opportunity (100 words)**
- **Bridge:** "This thesis asks: what if agents could perceive the physical world?"
- **Lead to next section:** Memory architectures need to handle this new input

#### Key Citations
- 012 PRIME (Wang et al., 2025)
- 013 PLLM Survey (Liu et al., 2025)
- 038 Personalization: A Taxonomy (Blom, 2000)
- 041 Personalized LLM-Powered Agents (2026)

---

### **2.3 Memory Architectures - The Foundation**

#### Instability Structure
**History:** Memory systems evolved from cognitive architectures → LLM-based
**BUT:** All assume discrete, symbolic input
**Challenge:** How to handle continuous, multi-modal egocentric input?

#### Paragraph Breakdown

**P1: Historical Evolution (200 words)**
- **Opening:** "Memory architectures have evolved from cognitive science..."
- **Evidence:**
  - **043 Soar (1987):** "Architecture for general intelligence"
  - **044 ACT-R (1997):** "Theory of higher level cognition"
- **Transition:** "These inspired modern LLM-based memory systems..."
- **BUT:** "However, cognitive architectures assumed symbolic, discrete representations"

**P2: LLM-Based Memory (200 words)**
- **Achievement:** "Modern systems have achieved remarkable scalability..."
- **Evidence:**
  - **022 MemGPT (2023):** "Virtual context management with hierarchical memory"
  - **011 Mem0 (2024):** "Production-ready with 91% lower latency"
  - **045 Memoria (2025):** "Scalable agentic memory framework"
- **Quote:** "Persistent memory mechanisms for long-term conversational coherence" (011 Mem0)
- **BUT:** "All assume text-based, discrete input"

**P3: The Challenge (200 words)**
- **Anomaly:** "This creates a fundamental mismatch"
- **What egocentric vision provides:**
  - Continuous, high-frequency stream
  - Multi-modal (video + audio + IMU)
  - Raw sensorimotor data
- **What memory systems expect:**
  - Discrete events
  - Text or structured data
  - Low-frequency updates
- **Quote:** "Memory systems handle symbolic input well, but weren't designed for continuous multimodal streams" (004 Memory Survey)

**P4: Recent Advances (100 words)**
- **Bridge:** "Recent work has begun addressing multimodal memory..."
- **Evidence:**
  - **003 VideoAgent (2025):** "Memory-augmented multimodal agent"
  - **008 Mem2Ego (2025):** "Egocentric memory for navigation"
- **BUT:** "These focus on video understanding, not personalization"
- **Lead to next section:** Memory needs egocentric input

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

#### Instability Structure
**History:** Embodied AI focused on robotics, navigation, action
**BUT:** What about embodied observation for personalization?
**Anomaly:** Robots perceive physical world, personal agents don't

#### Paragraph Breakdown

**P1: Embodied AI (200 words)**
- **Opening:** "Embodied AI research has focused on physical interaction..."
- **Evidence:**
  - **001 Embodied AI Agents (2025):** "Understand and interact with physical world"
  - **005 VINCI (2025):** "Interactive multimodal conversation with visual grounding"
- **Achievement:** Navigation, manipulation, environment understanding
- **BUT:** "This work focuses on agents acting in the world, not observing users"

**P2: Perception Capabilities (200 words)**
- **Transition:** "Vision-language models provide powerful perception..."
- **Evidence:**
  - **007 VLM Survey (2024):** "Vision-language models bridge visual and textual modalities"
- **Quote:** "VLMs have achieved remarkable success in multimodal understanding" (007 VLM Survey)
- **BUT:** "VLMs are used for external visual input, not egocentric sensing"

**P3: The Gap (100 words)**
- **Anomaly:** "Robots perceive the physical world, but personal agents don't"
- **What's missing:** Passive, continuous observation of user's environment
- **Recent work:**
  - **042 MEMENTO (2025):** "Embodied agents meet personalization"
- **BUT:** "Still in early stages, no concrete systems"
- **Lead to next section:** Egocentric vision provides the solution

**P4: Technical Constraints (100 words)**
- **Challenge:** "24/7 egocentric sensing faces technical constraints..."
- **Evidence:**
  - **006b On-Device AI (2024):** "Computational resource limitations, memory constraints"
- **But solvable:** Modern smartphones have sufficient capability
- **Lead to 2.5:** Egocentric vision as the solution

#### Key Citations
- 001 Embodied AI Agents (2025)
- 005 VINCI (2025)
- 007 VLM Survey (2024)
- 042 MEMENTO (2025)
- 006b On-Device AI (2024)

---

### **2.5 Egocentric Vision and Self-Logging**

#### Instability Structure
**History:** Egocentric vision matured for activity recognition
**BUT:** Treated as end goal (recognition accuracy), not agent integration
**Missing:** How to integrate ego-vision into agent memory for personalization?

#### Paragraph Breakdown

**P1: Early Lifelogging (200 words)**
- **Opening:** "The vision of capturing personal experience dates back..."
- **Evidence:**
  - **027 SenseCam (2006):** "Wearable camera for automatic lifelogging, captures every 30 seconds"
  - **037 MyLifeBits (2006):** "Personal database fulfilling Memex vision"
- **Achievement:** Demonstrated feasibility of continuous capture
- **Quote:** "SenseCam enables automatic lifelogging without user intervention" (027 SenseCam)
- **BUT:** "These systems were passive archives, not active agent inputs"

**P2: Recognition Focus (200 words)**
- **Transition:** "Modern egocentric vision has achieved remarkable scale..."
- **Evidence:**
  - **020 EPIC-KITCHENS (2021):** "100 hours, 20M frames, 90K actions"
  - **019 Ego4D (2022):** "3,000 hours from 874 participants worldwide"
- **Quote:** "Largest first-person dataset to date" (020 EPIC-KITCHENS)
- **Achievement:** Activity recognition, object interaction understanding
- **BUT:** "All focus on recognition accuracy as end goal"

**P3: The Gap (200 words)**
- **Anomaly:** "Egocentric vision is mature, but not integrated into agent systems"
- **What's missing:**
  - No agent integration
  - No personalization
  - No long-term user modeling
- **Recent work:**
  - **036 EgoLog (2026):** "Ego-centric daily logging with audio-IMU fusion"
  - **008 Mem2Ego (2025):** "Egocentric memory for navigation"
- **Quote:** "EgoLog provides continuous logging, but focuses on daily logs not agent personalization" (036 EgoLog)
- **BUT:** "Still focused on logging/recognition, not agent integration"

**P4: This Thesis (200 words)**
- **Bridge:** "This thesis addresses this gap by integrating egocentric vision into personal AI agents"
- **Contributions:**
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

**✅ Instability Words (use frequently):**
- BUT, HOWEVER, ALTHOUGH, NEVERTHELESS
- ANOMALY, INCONSISTENCY, PARADOX
- REMAINS UNKNOWN, UNEXPLORED, LIMITED TO

**✅ Community Signals:**
- "widely recognized", "reported in", "accepted understanding"
- NOT: "I found that", "This paper says"

**✅ Subject Strategy:**
- Make community's work the subject
- "Personalization research has focused on..." (not "Many papers have...")

**✅ Sentence Length Variation:**
- Mix short (stress) + medium (flow) + long (elaboration)

**✅ Each Paragraph:**
- Start: History/Achievement
- Middle: BUT (instability)
- End: Question/Gaps

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
