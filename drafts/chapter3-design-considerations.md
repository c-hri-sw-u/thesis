# 3. Design Considerations

To integrate physical-world observation into personal AI agent memory, we must address core requirements while making principled design choices. This chapter analyzes constraints imposed by continuous personal agent deployment and justifies our selection of physical-world input modality and agent integration platform.

## 3.1 Core Requirements

Personal AI agents—unlike task-bounded systems that terminate after workflows—operate continuously over weeks and months, demanding memory systems that handle persistent physical-world input. We identify three requirements that constrain our design space.

### 3.1.1 Continuous Capture

Personal AI agents maintain persistent relationships with users across domains, adapting to evolving preferences over extended periods (OpenCLAW (Steinberger, 2025); Letta (Packer et al., 2024)). This demands a capture system that runs unobtrusively for days or weeks without interruption—a constraint absent in previous egocentric vision work focused on short-term recordings for activity recognition benchmarks (Ego4D (Grauman et al., 2022); EPIC-KITCHENS (Damen et al., 2021)).

The challenge is not merely technical (battery and storage) but practical: a system that interferes with daily life will not be used continuously, undermining the longitudinal personalization it aims to enable. Capture must be lightweight enough to run in the background, yet frequent enough to capture meaningful context.

### 3.1.2 Privacy Preservation

Egocentric video captures sensitive information—faces of bystanders, text on screens, private conversations, and identifiable locations. Unlike robotics applications where video is processed on powerful hardware with controlled environments (Embodied VideoAgent (Fan et al., 2025)), personal AI agents run on consumer devices where privacy must be preserved before any data leaves the phone.

The tension is fundamental: rich physical-world observation requires capturing information that users may not want recorded. Yet no existing egocentric vision system addresses this for agent integration—current work either assumes controlled environments (robotics) or prioritizes human review over autonomous agent use (EgoLife (Yang et al., 2025)). Privacy must be built into the capture pipeline, not retrofitted.

### 3.1.3 Integration Compatibility

The system must extend existing agent memory architectures, not replace them. Current personalization systems—spanning memory extraction (Mem0 (Chhikara et al., 2025)), knowledge-graph user modeling (Memoria (Sarin et al., 2025)), and markdown-based persistent storage (OpenCLAW (Steinberger, 2025))—assume textual input from digital interactions.

Physical-world input must be converted to representations these systems can ingest without architectural redesign. The conversion pipeline must preserve semantic meaning while fitting into existing storage, indexing, and retrieval mechanisms. A system requiring wholesale replacement of memory infrastructure would not answer our research question—we aim to enhance existing agents, not build parallel systems.

---

## 3.2 Design Choices

Given these requirements, we make two key design decisions: selecting egocentric vision as the primary physical-world input modality, and choosing OpenCLAW as the integration platform.

### 3.2.1 Egocentric Vision as Primary Modality

We select egocentric vision—first-person video from smartphone cameras—as the primary physical-world input modality for three reasons.

**First-Person Perspective Alignment.** Personal AI agents assist a single user continuously—their perspective should match the user's. Third-person cameras (surveillance, room cameras) capture environment but miss what the user sees and attends to. Ambient sensors (motion, location) provide context but lose visual detail. Egocentric vision naturally aligns with user attention, capturing not just where the user is but what they're looking at and interacting with (Ego4D (Grauman et al., 2022); Ego-Exo4D (Grauman et al., 2024)).

**Technical Maturity.** The pipeline from egocentric video to structured text is no longer a research bottleneck. Vision-language models achieve real-time semantic extraction—identifying activities, objects, and environment (Embodied VideoAgent (Fan et al., 2025); Vinci (Pei et al., 2025); EgoLife (Yang et al., 2025)). This makes integration technically viable without requiring novel perception research. The question shifts from "can we extract information?" to "what information should we extract and how does it improve personalization?"

**Privacy-Utility Balance.** Egocentric capture can be filtered on-device—faces can be obfuscated, text redacted, audio transcribed without storing raw recordings—while preserving activity and environment information (SenseCam privacy studies (Hodges et al., 2006); contemporary on-device ML (PHIA (Coravos et al., 2026))). Audio-only loses visual context; video-only loses conversational privacy; continuous logging without filtering creates surveillance risks. Egocentric vision with on-device processing provides a balanced trade-off.

**Alternatives Considered.** Ambient sensors (motion, light, temperature) lose user-specific context and fail to capture activities. Third-person cameras raise privacy concerns in shared spaces and misalign with user perspective. Smartphone usage logs (app usage, notifications) remain digital-only and miss physical-world context. Wearable health devices (heart rate, steps) capture physiology but not environment. Egocentric vision uniquely captures rich physical context from the user's perspective with acceptable privacy trade-offs.

### 3.2.2 OpenCLAW as Integration Platform

We build on OpenCLAW rather than creating a new agent system or using closed platforms for three reasons.

**Production-Grade Foundation.** OpenCLAW demonstrates practical deployment with integrated tools, persistent memory, and continuous learning in real-world use (Steinberger, 2025). Building on production systems ensures our extension addresses genuine constraints—battery consumption, storage limits, retrieval latency, user interface integration—rather than toy scenarios. This is critical for our research question: we aim to discover where physical context helps in realistic personal agent use, which requires a realistic baseline.

**Transparent Memory Architecture.** Unlike closed-source systems (Mem0, Memoria) or complex virtual context management (MemGPT (Packer et al., 2023)), OpenCLAW's memory is plain markdown files—fully transparent, easily inspectable, and simple to extend. This transparency is critical for answering RQ2 (design requirements for memory integration) and RQ3 (where physical context helps). We must observe how physical-world data flows into and is retrieved from memory, which requires understanding the memory system completely.

**Markdown-Based Representation.** OpenCLAW's text-based memory aligns naturally with LLM-based semantic extraction from egocentric video. The pipeline "video → VLM → text summary → markdown memory" requires no representation conversion—VLMs produce text, OpenCLAW stores text. This simplifies integration and preserves interpretability: users and researchers can read memory files directly without decoding graph structures or database schemas.

**Alternatives Considered.** MemGPT provides sophisticated virtual context management but is closed-source with complex hierarchical memory unsuitable for inspection. Memoria uses knowledge graphs that mismatch text-based VLM output and would require representation conversion. Building from scratch would reinvent solved problems (memory persistence, retrieval, LLM integration) without advancing our research questions. OpenCLAW provides the right abstraction level: simple enough to understand and extend, complex enough to represent realistic agent deployment.

---

These design considerations lead to a three-layer architecture: physical input layer (egocentric capture with privacy filtering), processing layer (VLM-based extraction and summarization), and memory extension layer (OpenCLAW integration). Chapter 4 details this architecture and implementation.
