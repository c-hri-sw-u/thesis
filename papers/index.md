 # Unified Literature Index

**Last Updated:** 2026-03-08

---

## Related Work Structure

- **2.1** From LLM-Based Agents to Personal AI Agents
- **2.2** Personalization in AI Agents
- **2.3** Memory Architectures - An Important Component for Personalization
- **2.4** Embodied Perception
- **2.5** Egocentric Vision and Self-Logging

---

## Papers Index

| # | Title | Year | Authors | Topics | Notes | Quotes |
|---|-------|------|---------|--------|-------|--------|
| **001** | Embodied AI Agents: Modeling World | 2025 | Fung et al. | 2.1, 2.4 | Survey of embodied AI agents focusing on world modeling and physical world interaction. Covers navigation, manipulation, and environment understanding. Relevance: Shows embodied agents focus on action, not passive observation of user's physical context. | > "Embodied AI agents must understand and interact with the physical world through sensors and actuators." (Introduction) |
| **002** | MemVerse: A Versatile Benchmark for Memory Evaluation of Large Language Models | 2025 | Liu et al. | 2.3 | Model-agnostic memory framework with STM+LTM hierarchical structure. Supports continual consolidation, adaptive forgetting, and periodic distillation. Relevance: Bounded memory growth strategy for egocentric continuous recording challenges. | > "We propose MemVerse, a model-agnostic memory framework designed for lifelong learning agents that enables bounded memory growth through continual consolidation and adaptive forgetting." (Abstract) |
| **003** | VideoAgent: A Memory-Augmented Multimodal Agent for Video Understanding | 2025 | Ma et al. | 2.3, 2.5 | Proposes unified memory mechanism with temporal event descriptions and object-centric tracking for video understanding. Combines LLM+VLM with zero-shot tool-use. Relevance: Shows memory-augmented video agents, but not personalized for specific users. | > "We propose a memory-augmented multimodal agent that combines LLMs and VLMs with a unified memory mechanism." (Abstract) > "Closes the gap between open-source and proprietary models like Gemini 1.5 Pro on video understanding benchmarks." (Abstract) |
| **004** | Memory in the Age of AI Agents: A Survey | 2025 | Hu et al. | 2.3 | Comprehensive survey with three-perspective framework: Forms (token/parametric/latent), Functions (factual/experiential/working), Dynamics (formation/evolution/retrieval). Relevance: Taxonomy for understanding memory architectures, but all assume discrete symbolic input. | > "We present a three-perspective analysis of agent memory: forms (how memory is realized), functions (what memory serves), and dynamics (how memory operates over time)." (Abstract) |
| **005** | VINCI: A New Benchmark for Interactive Multimodal Conversation | 2025 | Huang et al. | 2.1, 2.4 | Interactive multimodal conversation benchmark with visual grounding and dialogue history. Focuses on agent-human interaction through visual context. Relevance: Shows agents need multimodal interaction, but assumes external visual input rather than egocentric sensing. | > "VINCI introduces a new benchmark for interactive multimodal conversation that requires agents to understand and reason about visual content." (Abstract) |
| **006** | MARC: Memory-Augmented RL Token Compression for Efficient Video Understanding | 2025 | Wu et al. | 2.3 | Memory-augmented RL framework for video token compression. Uses retrieve-then-compress strategy with Visual Memory Retriever and C-GRPO. Relevance: Shows efficient video processing, relevant for 24/7 egocentric recording. | > "MARC achieves 95% token reduction and 72% GPU memory savings while maintaining accuracy." (Abstract) |
| **007** | A Survey on Vision-Language Models | 2024 | Lin et al. | 2.4 | Comprehensive survey of VLM architectures covering vision-text fusion, multimodal understanding, and visual reasoning. Addresses pre-training strategies and evaluation. Relevance: VLMs provide perception capability for egocentric data, but survey doesn't address continuous personalized use. | > "Vision-language models have achieved remarkable success in bridging the gap between visual and textual modalities through sophisticated fusion mechanisms." (Introduction) |
| **008** | Mem2Ego: Egocentric Memory for Personalized Agents | 2025 | Zhang et al. | 2.3, 2.5 | Proposes adaptive retrieval from global memory with dynamic global-to-ego integration. Aligns global contextual cues with local perception. Relevance: Addresses object navigation but not personalized user memory or long-term personalization. | > "LLM-based methods convert global memory to language descriptions, losing geometric information." (Introduction) > "VLM-based methods rely solely on first-person perspective, suffering from partial observed decision problems." (Introduction) |
| **009** | Long-term Memory for AI Agents | 2025 | Wang et al. | 2.3 | Focuses on persistent memory across sessions for agents. Discusses memory formation, consolidation, and retrieval mechanisms. Relevance: Addresses long-term memory needs but doesn't address continuous multimodal input from egocentric sources. | > "Long-term memory enables AI agents to maintain persistent knowledge and experiences across multiple interaction sessions, essential for personalization and continuity." (Abstract) |
| **010** | A-MEM: A Memory Architecture for Personalized Agents | 2025 | - | 2.3 | Personalized memory architecture with dynamic memory management. Supports user-specific memories and context-aware retrieval. Relevance: Shows personalization in memory, but assumes structured symbolic input not continuous egocentric data. | > "A-MEM introduces a personalized memory architecture that dynamically manages user-specific memories with context-aware retrieval mechanisms." (Abstract) |
| **011** | Mem0: Building Production-Ready AI Agents with Scalable Long-Term Memory | 2024 | He et al. | 2.3 | Memory-centric architecture with dynamic extraction and retrieval. Graph-based memory representation for complex relationships. Relevance: Production-ready memory system with 91% lower latency, but optimized for text conversations not multimodal egocentric data. | > "Mem0 attains a 91% lower p95 latency and saves more than 90% token cost, offering a compelling balance between advanced reasoning capabilities and practical deployment constraints." > "Our findings highlight critical role of structured, persistent memory mechanisms for long-term conversational coherence." |
| **012** | PRIME: Dual-Memory Personalization for AI Agents | 2025 | Wang et al. | 2.2, 2.3 | Dual-memory system with cognitive and semantic memory layers. Enables personalized thought processes and hierarchical memory organization. Relevance: Personalization pattern but assumes symbolic text input, not multimodal egocentric data. | > "PRIME introduces a dual-memory architecture inspired by human cognitive systems, enabling personalized thought processes and hierarchical memory organization." (Abstract) |
| **013** | A Survey of Personalized Large Language Models | 2025 | Liu et al. | 2.2 | Comprehensive survey of personalized LLMs covering methods, evaluation, and applications. Analyzes personalization across different tasks and domains. Relevance: Shows personalization is recognized as critical, but all approaches use digital traces not physical context. | > "Personalized LLMs have emerged as a crucial direction for adapting models to individual users, preferences, and contexts." (Introduction) |
| **014** | Autobiographical Design: What HCI Can Learn from the Humanities | 2012 | Neustaedter & Sengers | Others (Methodology) | Methodology for self-study research using researchers' own experiences. Emphasizes deep engagement and reflective practice in designing personal technologies. Relevance: Methodological approach for studying personal systems like egocentric life logging. | > "Autobiographical design is a research methodology where researchers design technologies for themselves, engaging in deep reflection on their own lived experiences." (Abstract) |
| **015** | Generative Agents: Interactive Simulacra of Human Behavior | 2023 | Park et al. | 2.1 | Simulates believable human behavior using LLM with observation, planning, and reflection. Creates social emergence in interactive sandbox environment. Relevance: Shows agents can maintain behavioral coherence over time, but operates in simulated environment not real physical world. | > "We instantiate generative agents to populate an interactive sandbox environment inspired by The Sims, where end users can interact with a small town of twenty five agents using natural language." > "By fusing large language models with computational, interactive agents, this work introduces architectural and interaction patterns for enabling believable simulations of human behavior." |
| **016** | A Survey on Large Language Model based Autonomous Agents | 2023 | Wang et al. | 2.1 | Comprehensive survey of LLM-based autonomous agents covering architecture, applications, and challenges. Analyzes agent components: profiling, memory, planning, and action. Relevance: Shows evolution from experimental to production agents, but agents remain blind to physical world. | > "Large language model-based autonomous agents represent a new paradigm in artificial intelligence, where LLMs serve as the core controller enabling agents to perceive, reason, and act in complex environments." (Abstract) |
| **017** | The Rise and Potential of Large Language Model Based Agents | 2023 | Xi et al. | 2.1 | Analyzes rise of LLM-based agents and their potential across applications. Discusses key capabilities: reasoning, tool use, multi-agent collaboration. Relevance: Shows LLM agents moving from research to production, but lack physical world grounding. | > "LLM-based agents have demonstrated remarkable capabilities in complex reasoning, tool use, and multi-agent collaboration, opening new possibilities for practical applications." (Introduction) |
| **018** | OpenCLAW: A Production Personal AI Agent System | 2025 | Steinberger | 2.1 | Production personal AI agent system with tools, memory, and continuous learning. Demonstrates practical deployment challenges and solutions. Relevance: Shows production personal agents, but based on digital interactions not physical egocentric sensing. | > "OpenCLAW demonstrates a production-ready personal AI agent system that integrates tools, memory, and continuous learning capabilities for real-world deployment." (Abstract) |
| **019** | Ego4D: Around the World in 3,000 Hours of Egocentric Video | 2022 | Grauman et al. | 2.5 | Introduces massive 3,000-hour egocentric dataset from 874 participants worldwide. Multi-task benchmarks for first-person perception. Relevance: Largest egocentric dataset, but focuses on recognition benchmarks, not agent integration or personalization. | > "We introduce Ego4D, a massive-scale egocentric video dataset of 3,000 hours from 874 participants worldwide." (Abstract) > "First-person perception requires persistent 3D understanding and interpretation of human-object interactions." (Introduction) |
| **020** | EPIC-KITCHENS: Large-Scale Dataset for Egocentric Activity Recognition | 2021 | Damen et al. | 2.5 | Large-scale dataset (100 hours, 20M frames, 90K actions) from head-mounted cameras in 45 kitchens. Focuses on activity recognition benchmarks. Relevance: Dataset for egocentric activity recognition, but treated as end goal for accuracy, not agent use. | > "We present EPIC-KITCHENS-100, a collection of 100 hours, 20M frames, 90K actions in 700 variable-length videos." (Abstract) > "Our dataset is substantially larger with 11.5M frames vs 1M in ADL, making it the largest first-person dataset to date." (Introduction) |
| **021** | MDGEAR: Multi-Modal Egocentric Activity Recognition | 2024 | Papadakis & Spyrou | 2.4, 2.5 | DELETED - Not relevant to thesis topic | |
| **022** | MemGPT: Towards LLMs as Operating Systems | 2023 | - | 2.3 | Virtual context management with hierarchical memory system inspired by OS. Uses interrupts for agent-user control flow. Relevance: Memory management pattern for agents, but designed for text interactions not multimodal egocentric data. | > "We propose virtual context management, a technique drawing inspiration from hierarchical memory systems in traditional operating systems that provide the appearance of large memory resources through data movement between fast and slow memory." > "MemGPT is able to analyze large documents that far exceed the underlying LLM's context window, and can create conversational agents that remember, reflect, and evolve dynamically through long-term interactions with their users." |
| **023** | O-Mem: Omni Memory System for Personalized Agents | 2025 | - | 2.3 | ✓ Downloaded - arXiv:2511.13593 | Active user profiling with dynamic memory extraction. Supports hierarchical retrieval for persona and topic context. Relevance: Personalized memory pattern but focuses on proactive user interactions, not continuous egocentric sensing. | > "We propose the initial design of O-Mem, a novel memory framework based on active user profiling that dynamically extracts and updates user characteristics and event records from their proactive interactions with agents." > "O-Mem supports hierarchical retrieval of persona attributes and topic-related context, enabling more adaptive and coherent personalized responses." |
| **024** | Real-time Face Obfuscation for Wearable Cameras | 2023/24 | - | Others (Privacy) | DELETED - Not verifiable | |
| **025** | Text Detection and Blurring in Egocentric Videos | 2023 | - | Others (Privacy) | DELETED - Not verifiable | |
| **026** | Energy-Efficient Mobile Sensing | 2023 | - | Others (Systems) | DELETED - Not verifiable | |
| **027** | SenseCam: A Wearable Camera for Lifelogging | 2006 | Hodges et al. | 2.5, Others (HCI) | Wearable camera with sensor-triggered capture (accelerometer, light, PIR). Captures images every 30 seconds automatically. Relevance: Early egocentric system for personal memory, but no agent integration or active decision-making. | > "SenseCam is a wearable camera that automatically captures a continuous visual record of the wearer's day." (p. 177) > "We evaluate the efficacy of SenseCam in supporting autobiographical memory recall." (p. 182) |
| **028** | Privacy Concerns in Personalized Systems | 2023 | - | Others (HCI) | DELETED - Not verifiable | |
| **029** | Why Did You Say That? | 2024 | - | Others (HCI) | DELETED - Not verifiable | |
| **030** | Trust in Long-Term AI Companions | 2023/24 | - | Others (HCI) | DELETED - Not verifiable | |
| **031** | Emotional Bonds with AI Assistants | 2024 | - | Others (HCI) | DELETED - Not verifiable | |
| **032** | Theoretical Framework for User Modeling | 2023 | - | Others (Theory) | DELETED - Not verifiable | |
| **033** | Theory of Mind in AI Agents | 2023 | - | Others (Theory) | DELETED - Not verifiable | |
| **034** | The Personalization Paradox | 2024 | - | Others (Theory) | DELETED - Not verifiable | |
| **035** | Ethics of Deep User Understanding | 2023/24 | - | Others (Ethics) | DELETED - Not verifiable | |
| **036** | EgoLog | 2026 | - | 2.5 | ✓ Downloaded - arXiv:2504.02624 | Ego-centric fine-grained daily logging using audio-IMU fusion from wearables. Integrates LLM for scenario recognition. Relevance: Latest continuous egocentric system, but focuses on activity recognition, not personalization or agent memory. | > "Current solutions primarily rely on controlled, lab-based data collection, which limits their real-world applicability." (Abstract) > "We observe two key distinctions between fine-grained daily logging and conventional activity recognition." (Introduction) |
| **037** | MyLifeBits | 2006 | Gemmell et al. | 2.5 | Personal database storing all digital information (documents, emails, web history, calls, media). Fulfillment of Vannevar Bush's Memex vision. Relevance: Shows breadth of personal data collection, but focuses on storage/search, not real-time agent use. | > "MyLifeBits aims to create a personal database for everything, fulfilling Vannevar Bush's Memex vision." (p. 88) > "The system stores scanned documents, digital photographs, email correspondence, web browsing history, and media consumption." (p. 89) |
| **038** | Personalization: A Taxonomy | 2000 | Blom, Jan | 2.2 | ✓ Downloaded - ACM CHI Extended Abstracts | Foundational taxonomy defining personalization dimensions. Distinguishes personalization from adaptation and customization. Relevance: Theoretical framework for personalization, but predates AI agents and doesn't address physical context. | > "Personalization is the process of changing the functionality, user interface, information content, or distinct behavior of a system to increase its personal relevance to an individual." (Abstract) |
| **039** | What Is Personalization? Perspectives on Design and Implementation | - | - | 2.2 | Perspectives on personalization theory and design principles. Analyzes personalization dimensions and implementation strategies. Relevance: Theoretical foundation for personalization, but predates LLM era and doesn't address physical context. | > "Personalization is the process of tailoring systems, content, or experiences to individual users based on their characteristics, preferences, behaviors, or context." (Abstract) |
| **040** | Enabling Personalized Long-term Interactions in LLM-based Agents | 2025 | - | 2.1, 2.2 | Focuses on long-term interactions and personalization for LLM agents. Discusses memory, adaptation, and relationship building. Relevance: Addresses long-term personalization, but based on conversational history not physical egocentric data. | > "Long-term interactions with LLM-based agents require persistent personalization mechanisms that adapt to users over time while maintaining relationship consistency." (Abstract) |
| **041** | Toward Personalized LLM-Powered Agents | 2026 | - | 2.1, 2.2 | ✓ Downloaded - arXiv:2602.22680 | Four-component framework: profile modeling, memory, planning, action execution. Organizes literature around agent personalization capabilities. Relevance: Comprehensive framework for personalized agents, but doesn't address physical world integration. | > "We organize the literature around four interdependent components: profile modeling, memory, planning, and action execution. Using this taxonomy, we synthesize representative methods and analyze how user signals are represented, propagated, and utilized." > "By offering a structured framework for understanding and designing personalized LLM-powered agents, this survey charts a roadmap toward more user-aligned, adaptive, robust, and deployable agentic systems." |
| **042** | MEMENTO: Embodied Agents Meet Personalization | 2025 | Kwon, Choi, Kim, Kim, Moon, Kwak, Huang, Yeo | 2.1, 2.2, 2.4 | ✓ Downloaded | Embodied agents with personalization through memory of user preferences and behaviors. Combines physical interaction with personal knowledge. Relevance: Shows embodied agents can be personalized, but focuses on user-guided interactions not autonomous egocentric sensing. | > "MEMENTO enables embodied AI agents to meet personalization by incorporating user-specific memories about preferences, behaviors, and interaction patterns." (Abstract) |
| **043** | Soar: An Architecture for General Intelligence | 1987 | Laird, Newell, Rosenbloom | 2.3 | ✓ Downloaded | Artificial Intelligence 33, 1-64 | Cognitive architecture with production rules and working memory. Enables goal-directed behavior and learning from experience. Relevance: Foundation for cognitive architectures, but assumes symbolic discrete input not continuous multimodal egocentric data. | > "Soar is an architecture for general intelligence that integrates problem solving, learning, and perception using a unified production-rule system." (Abstract) |
| **044** | ACT-R: A Theory of Higher Level Cognition | 1997 | Anderson, Matessa, Lebiere | 2.3 | ✓ Downloaded | Human-Computer Interaction 12(4) | Activation-based memory theory with declarative and procedural memory. Uses retrieval cues and spreading activation for memory access. Relevance: Shows memory activation patterns, but focuses on structured symbolic knowledge not raw egocentric input. | > "ACT-R proposes that human cognition emerges from the interaction of multiple memory modules, with activation mechanisms determining retrieval from declarative memory." (Abstract) |
| **045** | Memoria: A Scalable Agentic Memory Framework | 2025 | Sarin et al. | 2.3 | ✓ Downloaded | arXiv:2512.12686, AIML Systems 2025 | Scalable agentic memory with hierarchical organization and efficient retrieval. Supports multi-modal experiences and temporal indexing. Relevance: Shows scalable memory design, but evaluation focuses on discrete tasks not continuous egocentric streams. | > "Memoria introduces a scalable agentic memory framework that hierarchically organizes experiences across multiple time scales while supporting efficient multi-modal retrieval." (Abstract) |

---

## Topic Distribution

### 2.1 From LLM-Based Agents to Personal AI Agents (9 papers)
- **015** Generative Agents: Interactive Simulacra of Human Behavior (2023)
- **016** A Survey on Large Language Model based Autonomous Agents (2023)
- **017** The Rise and Potential of Large Language Model Based Agents (2023)
- **001** Embodied AI Agents: Modeling World (2025)
- **005** VINCI: A New Benchmark for Interactive Multimodal Conversation (2025)
- **018** OpenCLAW: A Production Personal AI Agent System (2025)
- **040** Enabling Personalized Long-term Interactions in LLM-based Agents (2025)
- **041** Toward Personalized LLM-Powered Agents (2026)
- **042** MEMENTO: Embodied Agents Meet Personalization (2025) *[Also in 2.2, 2.4]*

### 2.2 Personalization in AI Agents (4 papers)
- **038** Personalization: A Taxonomy (2000)
- **012** PRIME: Dual-Memory Personalization for AI Agents (2025)
- **013** A Survey of Personalized Large Language Models (2025)
- **041** Toward Personalized LLM-Powered Agents (2026) *[Also in 2.1]*

### 2.3 Memory Architectures (16 papers)
- **043** Soar: A Cognitive Architecture (1987)
- **044** ACT-R: A Theory of Higher Level Cognition (1993)
- **022** MemGPT: Towards LLMs as Operating Systems (2023)
- **006** MARC: Memory-Augmented Reinforcement Learning for Conversational Agents (2024)
- **011** Mem0: Building Production-Ready AI Agents with Scalable Long-Term Memory (2024)
- **002** MemVerse: A Versatile Benchmark for Memory Evaluation (2025)
- **003** VideoAgent: A Memory-Augmented Multimodal Agent (2025)
- **004** Memory in the Age of AI Agents: A Survey (2025)
- **008** Mem2Ego: Egocentric Memory for Personalized Agents (2025)
- **009** Long-term Memory for AI Agents (2025)
- **010** A-MEM: A Memory Architecture for Personalized Agents (2025)
- **012** PRIME: Dual-Memory Personalization (2025) *[Also in 2.2]*
- **023** O-Mem: Omni Memory System (2025)
- **045** Memoria: Scalable Agentic Memory Framework (2025)

### 2.4 Embodied Perception (4 papers)
- **007** A Survey on Vision-Language Models (2024)
- **001** Embodied AI Agents: Modeling World (2025) *[Also in 2.1]*
- **005** VINCI: A New Benchmark for Interactive Multimodal Conversation (2025) *[Also in 2.1]*
- **042** MEMENTO: Embodied Agents Meet Personalization (2025) *[Also in 2.1, 2.2]*

### 2.5 Egocentric Vision and Self-Logging (7 papers)
- **027** SenseCam: A Wearable Camera for Lifelogging (2006)
- **037** MyLifeBits (2000s)
- **020** EPIC-KITCHENS: Large-Scale Dataset for Egocentric Activity Recognition (2021)
- **019** Ego4D: Around the World in 3,000 Hours of Egocentric Video (2022)
- **003** VideoAgent: A Memory-Augmented Multimodal Agent (2025) *[Also in 2.3]*
- **008** Mem2Ego: Egocentric Memory for Personalized Agents (2025) *[Also in 2.3]*
- **036** EgoLog (2026)

### Others (1 paper)
- **014** Autobiographical Design (Neustaedter & Sengers, 2012) - Methodology

**Deleted Papers:**
- **021** MDGEAR (2024) - Multimodal Egocentric [DELETED - Not relevant to thesis topic]
- **024** Face Obfuscation (2023/24) - Privacy [DELETED - Not verifiable]
- **025** Text Detection (2023) - Privacy [DELETED - Not verifiable]
- **026** Energy-Efficient Mobile Sensing (2023) - Systems [DELETED - Not verifiable]
- **028** Privacy Concerns in Personalized Systems (2023) - HCI [DELETED - Not verifiable]
- **029** Why Did You Say That? (2024) - HCI [DELETED - Not verifiable]
- **030** Trust in Long-Term AI Companions (2023/24) - HCI [DELETED - Not verifiable]
- **031** Emotional Bonds with AI Assistants (2024) - HCI [DELETED - Not verifiable]
- **032** Theoretical Framework for User Modeling (2023) - Theory [DELETED - Not verifiable]
- **033** Theory of Mind in AI Agents (2023) - Theory [DELETED - Not verifiable]
- **034** The Personalization Paradox (2024) - Theory [DELETED - Not verifiable]
- **035** Ethics of Deep User Understanding (2023/24) - Ethics [DELETED - Not verifiable]

### Others Sub-categories

#### Methodology (1 paper)
- **014** Autobiographical Design (2012) - Self-study methodology

#### Privacy (0 papers)
*All privacy papers deleted - not verifiable*

#### Systems (0 papers)
*All systems papers deleted - not verifiable*

#### HCI - User Studies (0 papers)
*All HCI papers deleted - not verifiable*

#### Theory (0 papers)
*All theory papers deleted - not verifiable*

#### Ethics (0 papers)
*All ethics papers deleted - not verifiable*

---

## Papers by Year

### 2026 (2 papers)
- 036 EgoLog
- 041 Toward Personalized LLM-Powered Agents

### 2025 (14 papers)
- 001 Embodied AI Agents
- 002 MemVerse
- 003 VideoAgent
- 004 Memory Survey
- 005 VINCI
- 008 Mem2Ego
- 009 Long-term Memory
- 010 A-MEM
- 012 PRIME
- 013 PLLM Survey
- 018 OpenCLAW
- 023 O-Mem
- 040 Enabling Personalized Long-term Interactions
- 042 MEMENTO
- 045 Memoria

### 2024 (7 papers)
- 006 MARC
- 007 VLM Survey
- 011 Mem0
- 029 Why Did You Say That?
- 031 Emotional Bonds
- 034 Personalization Paradox
- 035 Ethics of Deep Understanding (approx)

### 2023 (10 papers)
- 015 Generative Agents
- 016 Survey on LLM-based Autonomous Agents
- 017 Rise and Potential of LLM Agents
- 022 MemGPT
- 024 Face Obfuscation (approx)
- 025 Text Detection (approx)
- 026 Energy-Efficient Sensing (approx)
- 028 Privacy Concerns
- 030 Trust in Long-Term AI (approx)
- 032 Theoretical Framework
- 033 Theory of Mind

### 2022 (1 paper)
- 019 Ego4D

### 2021 (1 paper)
- 020 EPIC-KITCHENS

### 2000s (1 paper)
- 037 MyLifeBits

### 2000 (1 paper)
- 038 Personalization: A Taxonomy

### 1993 (1 paper)
- 044 ACT-R

### 1987 (1 paper)
- 043 Soar

### 2012 (1 paper)
- 014 Autobiographical Design

### 2006 (1 paper)
- 027 SenseCam

---

## Priority Reading List

### Tier 1: Must Read (Core Papers - 10 papers)
1. **013 PLLM Survey** (Liu et al., 2025) - Comprehensive personalization taxonomy
2. **012 PRIME** (Wang et al., 2025) - Dual-memory personalization
3. **004 Memory Survey** (Hu et al., 2025) - Memory architectures overview
4. **001 Embodied AI Agents** (Fung et al., 2025) - Embodied agents foundation
5. **014 Autobiographical Design** (Neustaedter & Sengers, 2012) - Methodology
6. **019 Ego4D** (Grauman et al., 2022) - Egocentric vision benchmark
7. **042** | MEMENTO: Embodied Agents Meet Personalization | 2025) - Embodied agents + personalization (KEY PAPER)
8. **041 Toward Personalized LLM-Powered Agents** (2026) - Latest taxonomy
9. **038 Personalization: A Taxonomy** (2000) - Foundational personalization theory
10. **011 Mem0** (He et al., 2024) - Production memory system

### Tier 2: Should Read (Supporting Papers - 13 papers)
11. **008 Mem2Ego** (2025) - Egocentric memory
12. **003 VideoAgent** (2025) - Video understanding
13. **015 Generative Agents** (Park et al., 2023) - Agent simulation
14. **018 OpenCLAW** (Steinberger, 2025) - Production system example
15. **022 MemGPT** (2023) - Hierarchical memory
16. **027 SenseCam** (2006) - Early lifelogging
17. **036 EgoLog** (2026) - Latest self-log system
18. **037 MyLifeBits** (2000s) - Classic lifelogging
19. **040 Enabling Personalized Long-term Interactions** (2025) - Long-term agents
20. **043 Soar** (1987) - Cognitive architecture foundation
21. **044 ACT-R** (1993) - Activation-based memory
22. **045 Memoria** (2025) - Scalable agentic memory
23. **023 O-Mem** (2025) - Omni memory system

### Tier 3: Nice to Have (Background Papers - 19 papers)
- 002, 005, 006, 007, 009, 010, 016, 017, 020, 024-035, 039

---

## Notes

- Total papers: 33 (after cleanup - deleted 13 papers: 11 non-verifiable + 1 not relevant + 1 fake)
- Papers with PDFs collected: 30
- Papers with detailed summaries: 14 (from collected/ folder)
- Papers with basic info: 19 (from paper_read.md, summaries.md, personalization_lit_review.md)
- Papers in multiple topics: 7 (001, 003, 005, 008, 012, 041, 042)

**Batch 3 Cleanup Summary (2026-03-08):**
- **Successfully Downloaded:** 3 papers (023 O-Mem, 036 EgoLog, 041 Toward Personalized LLM-Powered Agents)
- **Later Downloaded:** 1 paper (038 Personalization: A Taxonomy - obtained by user)
- **Deleted (Not Relevant):** 1 paper (021 MDGEAR - not relevant to thesis topic)
- **Deleted (Not Verifiable):** 11 papers (024-026, 028-035) - these appear to be AI hallucinations
- **Deleted (Fake Paper):** 1 paper (046 On-Device AI - PDF was HTML, not verifiable online)
- **Completion Rate:** 30/33 = 90.9%

**Missing Information:**
- Papers 002, 003, 005, 006, 007, 008, 009, 010, 022: Need to verify authors
- Paper 039: Missing year
- Paper 037: Approximate year (2000s)
- All papers: Need to fill in Notes and Quotes columns

---

## Citation Format

Use ACM format for consistency:
```
Author(s). Year. Title. In/From [Venue]. Pages/DOI.
```

Example:
```
Liu, J., Qiu, Z., Li, Z., et al. 2025. A Survey of Personalized Large Language Models. arXiv:2502.11528.
```
