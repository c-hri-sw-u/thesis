# Related Work

**Draft Version:** v1
**Created:** 2026-03-11
**Status:** Complete
**Total:** 1,043 words

---

## 2.1 From LLM-Based Agents to Personal AI Agents

The emergence of LLM-based autonomous agents represents a paradigm shift in artificial intelligence. Early systems like Auto-GPT (2023) demonstrated that LLMs could serve as autonomous controllers for multi-step tasks. "Generative Agents: Interactive Simulacra of Human Behavior" (Park et al., 2023) showed agents maintaining coherent behavior through observation, planning, and reflection in simulated environments. Surveys like "A Survey on Large Language Model based Autonomous Agents" (Wang et al., 2023) and "The Rise and Potential of Large Language Model Based Agents" (Xi et al., 2023) established the paradigm, analyzing architectures spanning profiling, memory, planning, and action. These advances moved agents from experimental curiosities to capable multi-domain systems.

This thesis introduces the term **personal AI agents** to describe AI systems designed for long-term, personalized assistance to individual users. Key characteristics include: persistent memory across sessions enabling continuity, adaptation to user preferences over time, and proactive context-aware help rather than reactive responses. OpenCLAW (Steinberger, 2025) represents current state-of-the-art in production personal AI agents, demonstrating practical deployment with integrated tools, memory, and continuous learning capabilities.

These advances show AI agents have moved from research to real-world deployment. However, as these systems mature, a critical question emerges: what makes personal agents truly effective? Research increasingly points to personalization as the key differentiator. But how exactly does personalization work in current systems?

---

## 2.2 Personalization in AI Agents

Before personal AI agents matured, researchers already recognized personalization as crucial for AI systems. "A Survey of Personalized Large Language Models" (Liu et al., 2025) documents extensive work on adapting model weights and prompts to individual users for recommendation systems and personalized generation. This early exploration established that user-specific adaptation significantly improves effectiveness.

As personal AI agents evolved from experimental systems to production deployments, research focus shifted toward agent personalization. "PRIME: Dual-Memory Personalization for AI Agents" (Wang et al., 2025) introduces hierarchical memory organization inspired by human cognitive systems, enabling personalized thought processes. "Toward Personalized LLM-Powered Agents" (2026) provides comprehensive taxonomy organizing personalization across profile modeling, memory, planning, and action execution. This evolution shows personalization has become central to agent effectiveness.

Current approaches build user models from chat logs, interaction history, explicit preferences, and behavioral patterns over time. PRIME maintains dual-memory architecture for user-specific cognitive patterns, demonstrating that personalization significantly improves agent performance in long-term interactions.

However, all current personalization approaches share a fundamental limitation: they build models entirely from digital traces. What they miss is physical context—location, environment, real-time activities, focus state, and social surroundings. An agent might know your calendar shows a meeting, but not that you're in deep focus work and shouldn't be disturbed. How can agents personalize effectively when they're blind to the user's physical world? Memory architectures determine what information agents can use, and current systems weren't designed for physical-world input.

---

## 2.3 Memory Architectures

Memory systems provide the foundation for agent persistence and learning. "Soar: An Architecture for General Intelligence" (Laird, Newell, & Rosenbloom, 1987) established production-rule systems with working memory for goal-directed behavior, while "ACT-R: A Theory of Higher Level Cognition" (Anderson, Matessa, & Lebiere, 1997) introduced activation-based retrieval from declarative and procedural memory modules. These cognitive architectures established core principles: hierarchical organization, spreading activation, and learning from experience.

Modern LLM-based systems have adapted these principles with remarkable scalability. "MemGPT: Towards LLMs as Operating Systems" (2023) implements virtual context management inspired by operating system memory hierarchies, enabling analysis of documents far exceeding context windows. "Mem0: Building Production-Ready AI Agents with Scalable Long-Term Memory" (He et al., 2024) achieves 91% lower latency through graph-based memory representation, and "Memoria: A Scalable Agentic Memory Framework" (Sarin et al., 2025) organizes experiences hierarchically across multiple time scales. "Memory in the Age of AI Agents: A Survey" (Hu et al., 2025) provides comprehensive taxonomy across forms, functions, and dynamics.

However, all these systems share a critical assumption: input is discrete and symbolic. They expect text conversations with low-frequency updates and clear event boundaries. Egocentric vision provides continuous video streams with high-frequency multi-modal data (video, audio, IMU, GPS) and no clear boundaries. This creates a fundamental mismatch—memory systems designed for symbolic input cannot efficiently handle continuous egocentric streams. Memory architectures determine what information agents can use, and current systems were not designed for physical-world input.

---

## 2.4 Embodied Perception

Embodied AI has made remarkable progress in agents that perceive and act in physical environments. "Embodied AI Agents: Modeling World" (Fung et al., 2025) surveys agents navigating, manipulating objects, and understanding environments through sensors and actuators. "VINCI: A New Benchmark for Interactive Multimodal Conversation" (Huang et al., 2025) demonstrates agents requiring visual grounding for human interaction, and "A Survey on Vision-Language Models" (Lin et al., 2024) shows how VLMs bridge visual and textual modalities for sophisticated perception. Collectively, this work has advanced robot navigation, object manipulation, and scene understanding.

However, this research focuses on agents **acting** in the world, not **observing users**. Embodied AI studies robots navigating environments, agents manipulating objects, and multi-agent collaboration in physical spaces. It does not address passive observation of user behavior, long-term user modeling, or personalization through physical context. The anomaly is striking: robots perceive the physical world, but personal agents don't.

Recent work has begun bridging this gap. "MEMENTO: Embodied Agents Meet Personalization" (Kwon et al., 2025) explicitly connects embodied agents with personalization by incorporating user-specific memories about preferences and behaviors. This demonstrates potential for combining physical perception with user-specific knowledge. However, this remains in early stages with no concrete systems demonstrating continuous user observation for personalization. Egocentric vision offers a practical approach to embodied observation.

---

## 2.5 Egocentric Vision and Self-Logging

The vision of capturing personal experience dates back to early lifelogging systems. "SenseCam: A Wearable Camera for Lifelogging" (Hodges et al., 2006) introduced automatic capture every 30 seconds using sensor-triggered recording, while "MyLifeBits" (Gemmell et al., 2006) fulfilled Vannevar Bush's Memex vision with comprehensive personal databases. These early systems established continuous capture as feasible and demonstrated its value for autobiographical memory.

Modern egocentric vision has achieved remarkable scale and sophistication. "EPIC-KITCHENS: Large-Scale Dataset for Egocentric Activity Recognition" (Damen et al., 2021) contributed 100 hours with 20M frames across 45 kitchens, and "Ego4D: Around the World in 3,000 Hours of Egocentric Video" (Grauman et al., 2022) assembled the largest dataset from 874 participants worldwide. Collectively, these datasets have driven significant advances in activity recognition, object interaction understanding, and first-person perception benchmarks.

Recent work has begun connecting egocentric vision to agent systems. "VideoAgent: A Memory-Augmented Multimodal Agent for Video Understanding" (Ma et al., 2025) demonstrates memory-augmented video agents, and "Mem2Ego: Egocentric Memory for Personalized Agents" (Zhang et al., 2025) shows global-to-ego memory integration for navigation. "EgoLog" (2026) provides fine-grained daily logging using audio-IMU fusion with LLM integration for scenario recognition.

However, all these works treat egocentric vision as an end goal—focusing on recognition accuracy, navigation success, or logging completeness—rather than as input for agent personalization. None address how egocentric streams improve personalization, how to integrate ego-vision into agent memory architectures, or how to build long-term user models from continuous observation. This thesis bridges this gap by integrating egocentric vision into personal AI agents, asking: what value, if any, does physical-world observation provide for personalization?

---

## Summary Statistics

- **Section 2.1 (LLM Agents → Personal AI):** 195 words
- **Section 2.2 (Personalization):** 218 words
- **Section 2.3 (Memory Architectures):** 223 words
- **Section 2.4 (Embodied Perception):** 209 words
- **Section 2.5 (Egocentric Vision):** 198 words
- **Total:** 1,043 words

**Status:** First draft complete
**Next:** Review for coherence and transitions
