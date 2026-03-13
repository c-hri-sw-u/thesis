# 2. Related Work - v2

**Related Work enriches the problem, not demonstrates knowledge.**

Every section should make the reader feel:

- "This problem is urgent"
- "Current approaches are limited"
- "This thesis fills a critical gap"

**Content**

- 2.1: Personal AI agent 是什么 → 需要 personalization
- 2.2: Personalization 的现状 → 全靠 digital traces
- 2.3: Memory architecture → pipeline 里没有 physical entry point
- 2.4: Egocentric perception → 技术成熟但只在 robotics
- 2.5: Self-logging → 理念存在但从未接入 agent memory

### **2.1 From LLM-Based Agents to Personal AI Agents**
LLM-based autonomous agents—systems that combine profiling, memory, planning, and action into autonomous workflows (A Survey on Large Language Model based Autonomous Agents (Wang et al., 2023))—have proliferated across social simulation (Generative Agents (Park et al., 2023)), software engineering (SWE-Agent (Yang et al., 2024)), and autonomous research (Agent Laboratory (2025)). These agents, however, are task-bounded: they terminate after completing a workflow.

A distinct subset—what this thesis terms personal AI agents—is designed for long-term, personalized, diverse-scenario assistance to individual users. Unlike task-specific agents that terminate after a bounded workflow, personal AI agents maintain a persistent relationship with a single user across domains, adapting to evolving preferences over weeks and months.

This category is increasingly visible in open-source deployment (Letta (Packer et al., 2024); Charlie Mnemonic (GoodAI, 2024); PAI (Miessler, 2025); OpenClaw (Steinberger, 2025)) and commercial products, though academic formalization has only recently begun (Toward Personalized LLM-Powered Agents (Xu et al., 2026)). As these agents move from demonstrations to persistent deployment, the pressure on personalization intensifies—an agent that runs continuously must infer what the user needs and learn what not to do, both of which depend on the richness of its user model.

### **2.2 Personalization for personal AI Agents**
Personalization—adapting a system to increase its personal relevance (Personalization: A Taxonomy (Blom, 2000))—has been a persistent challenge throughout the evolution of AI systems.

At the model level, researchers have explored how to modify an LLM's outputs to reflect individual preferences (A Survey of Personalized Large Language Models (Liu et al., 2025); Measuring What Makes You Unique (Qiu et al., 2025)), establishing that user-specific adaptation significantly improves task performance. At the agent level, personalization becomes a design problem spanning an agent's entire pipeline—profiling, memory, planning, and action—rather than a single model call (Toward Personalized LLM-Powered Agents (Xu et al., 2026)). The shift matters: it is no longer about what the model says but what the agent does, and doing the right thing over weeks and across domains demands richer knowledge of the user.

Memory has received particular attention as the architectural foundation for this richer knowledge. Recent systems—spanning scalable memory extraction (Mem0 (Chhikara et al., 2025)), knowledge-graph-based user modeling (Memoria (Sarin et al., 2025)), and evolving user profiles (Enabling Personalized Long-term Interactions (Westhäußer et al., 2025))—demonstrate that persistent memory improves both agent performance and perceived personalization over multi-day deployments. For personal AI agents—where interactions span weeks and domains shift constantly—memory is not optional but structural.

Yet whether personalization operates at the model level or the system level, the data source remains the same: digital traces. Personalized prompts draw on chat histories; memory systems extract facts from conversations; user profiles aggregate patterns from tool usage, calendar entries, and file activity (Mem0 (Chhikara et al., 2025); OpenClaw (Steinberger, 2025)). No current approach captures the physical world—the environment a user occupies, the activity they are engaged in, or the state they are in.

### **2.3 Memory Architectures for Personalization**
To understand where this limitation is structurally embedded, it helps to examine how current agent memory systems work. Despite variation in implementation, they share a common three-stage pipeline: ingestion, storage, and retrieval.

At the ingestion stage, memory systems consume digital interaction data—conversation transcripts, tool call results, API responses—and use LLM-based extraction to distill salient facts, preferences, and events (Mem0 (Chhikara et al., 2025); MemGPT (Packer et al., 2023)). The input interface is not merely textual in practice—it is textual by design assumption. These systems were architected to process language-based interaction records; no current architecture includes a perception channel for physical-world observation.

At the storage stage, extracted information is organized into persistent structures. Implementations vary—vector databases (Mem0 (Chhikara et al., 2025)), knowledge graphs (Memoria (Sarin et al., 2025)), plain markdown files (OpenClaw (Steinberger, 2025))—but all store information extracted from digital interactions.

At the retrieval stage, agents surface relevant memories at inference time through hybrid strategies combining keyword matching (BM25) with vector similarity search (MemGPT (Packer et al., 2023)), selecting context to condition the LLM's next action.

This pipeline is well-optimized for digital traces. But its ingestion interface contains no entry point for physical-world data—not as an oversight, but as a reflection of an unchallenged design assumption: that the user's digital interaction surface is the only surface worth modeling.

### **2.4 Egocentric Perception**
The technology to observe the physical world from a user's perspective already exists. Egocentric vision—first-person video captured from head- or body-mounted cameras—has matured into an established research field, with large-scale benchmarks demonstrating that egocentric video captures rich information about a user's environment, activities, and social context (Ego4D (Grauman et al., 2022); Ego-Exo4D (Grauman et al., 2024)).

Recent vision-language models have made it technically viable to convert this visual stream into structured representations—persistent object memory, temporal reasoning over long video sequences, and real-time context-based dialogue (Embodied VideoAgent (Fan et al., 2025); EgoLife (Yang et al., 2025); Vinci (Pei et al., 2025)). The pipeline from egocentric observation to structured textual output is no longer a research bottleneck.

But this work pursues two objectives, neither of which is personalization. One line builds environment models for agent action—tracking object locations and spatial layouts to support navigation and manipulation (Embodied VideoAgent (Fan et al., 2025)). The other builds queryable records for human memory augmentation—letting users review what happened yesterday (EgoLife (Yang et al., 2025); Vinci (Pei et al., 2025)). What remains unexplored is feeding egocentric observation into an agent's memory pipeline as a source of personalization.

### **2.5 Self-Logging**
The idea of continuously capturing personal experience has a long history. Wearable and ambient devices have been recording daily life for decades—from automatic photography to full-spectrum digital archiving—accumulating rich records of activities, environments, and physiological signals (Memex (Bush, 1945); MyLifeBits (Gemmell et al., 2006); SenseCam (Hodges et al., 2006)). More recently, LLM-based agents have begun reasoning over wearable health data to surface personalized insights (PHIA (Coravos et al., 2026)).

But the goal throughout this tradition has been human memory augmentation—helping people recall their own past, or answer their own questions. Data is stored for the person to review, not for an AI agent to act on. No lifelogging system has fed its captured data into an agent's memory pipeline to improve autonomous decision-making or personalization.