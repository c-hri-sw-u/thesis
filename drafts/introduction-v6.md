# 1. Introduction - v1
A growing class of AI system—what this thesis terms the personal AI agent—is designed for long-term, personalized, diverse-scenario assistance to individual users. Unlike task-bounded agents that terminate after a workflow, personal AI agents maintain a persistent relationship with a single user across domains, adapting over weeks and months (Letta (Packer et al., 2024); Charlie Mnemonic (GoodAI, 2024); PAI (Miessler, 2025); OpenCLAW (Steinberger, 2025)). As these agents move from demonstrations to persistent deployment, personalization becomes critical: an agent's effectiveness depends on the richness and accuracy of its user model (Toward Personalized LLM-Powered Agents (Xu et al., 2026)). But current personal AI agents build these models entirely from digital traces—chat logs, files, calendars—while remaining blind to the physical world where users spend most of their time.

This blindness creates a critical limitation for personalization. For instance, when an agent proactively sends a non-urgent recommendation based on your manually-set schedule, it doesn't know you're in deep focus work, disrupting your most productive hour. Without physical context, personal AI agents are limited to half the picture. Yet no existing work has investigated whether bridging this gap matters—or where it helps and where it doesn't. The central question is: what value, if any, does continuous physical-world observation provide for personal AI agent personalization?

This thesis takes an exploratory approach. Rather than assuming physical-world observation improves personalization, I design a system to discover where it helps and where it doesn't. This methodology follows the autoethnographic tradition in HCI research (Autobiographical Design (Neustaedter & Sengers, 2012)), which validates deep self-study as a means of generating design insights when longitudinal deployment with users is impractical. The investigation is structured around three research questions:

RQ1: What physical-world information becomes visible through egocentric perception that remains invisible through digital traces alone?
RQ2: In what task contexts does this physical-world information meaningfully improve personalization, and when does it introduce noise or redundancy?
RQ3: What design requirements emerge for integrating continuous egocentric sensing into existing agent memory architectures?

This thesis contributes:

1. Empirical findings on where physical perception aids personalization (activity-aware scheduling, environmental adaptation) and where it doesn't (email drafting, file organization)
2. A system artifact integrating egocentric vision into OpenCLAW's markdown-based memory architecture
3. Design implications for storage granularity (text summaries vs. key frames), privacy trade-offs (14-day retention policy), and abstraction mechanisms (real-time detection + nightly summarization)