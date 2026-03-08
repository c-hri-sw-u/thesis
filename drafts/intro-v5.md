# 1. Introduction

An *emerging* class of AI system—what this thesis terms the **personal AI agent**—has moved from experimental projects (*Generative Agents* (Park et al., 2023); *A Survey on Large Language Model based Autonomous Agents* (2023)) to daily use (*OpenCLAW* (Steinberger, 2025)). As these agents maintain persistent memory, plan and act autonomously, and assist across multiple domains for a single user (*Generative Agents* (Park et al., 2023); *A Survey on Large Language Model based Autonomous Agents* (2023); *The Rise and Potential of Large Language Model Based Agents* (Xi et al., 2023)), **personalization** has become critical (*PLLM* (Liu et al., 2025)): an agent's effectiveness depends on the richness and accuracy of its user model (*PLLM* (Liu et al., 2025)). ***But*** current personal AI agents build these models entirely from digital traces—chat logs, files, calendars (*PLLM* (Liu et al., 2025))—while remaining blind to the physical world where users spend most of their time.

This blindness creates a **critical limitation** for **personalization**. For instance, when an agent proactively sends a non-urgent recommendation based on your manually-set schedule, it doesn't know you're in deep focus work, disrupting your most productive hour. Without physical context, personal AI agents are limited to "half the picture". **However**, the severity of this limitation remains unknown. The central question is whether bridging this gap matters: **what value, if any, does continuous physical-world observation provide for personal AI agent personalization?**

This thesis takes an exploratory approach. Rather than assuming physical-world observation improves personalization, I design a system to discover *where* it helps and *where* it doesn't. This methodology follows the autoethnographic tradition in HCI research (**Neustaedter & Sengers, 2012**), which validates deep self-study as a means of generating design insights when longitudinal deployment with users is impractical. The investigation is structured around three research questions:

**RQ1: What physical-world information becomes visible through egocentric perception that remains invisible through digital traces alone?**
*[Preview]*

**RQ2: In what task contexts does this physical-world information meaningfully improve personalization, and when does it introduce noise or redundancy?**
*[Preview]*

**RQ3: What design requirements emerge for integrating continuous egocentric sensing into existing agent memory architectures?**
*[Preview]*

This thesis contributes:

1. **Empirical findings** on where physical perception aids personalization (activity-aware scheduling, environmental adaptation) and where it doesn't (email drafting, file organization)
2. **A system artifact** integrating egocentric vision into OpenClaw's markdown-based memory architecture
3. **Design implications** for storage granularity (text summaries vs. key frames), privacy trade-offs (14-day retention policy), and abstraction mechanisms (real-time detection + nightly summarization)
