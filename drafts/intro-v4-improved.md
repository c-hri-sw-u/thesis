# 1. Introduction

A new category of AI system is emerging—the **personal AI agent**—designed to serve a single individual continuously across their daily life by maintaining persistent memory, acting proactively, and spanning multiple domains. OpenClaw (2025) exemplifies this shift: a text-based agent that remembers conversations, anticipates needs, and operates across a user's digital ecosystem. As these agents transition from research prototypes (**Generative Agents** (Park et al., 2023); **LLM-based Autonomous Agents** (Wang et al., 2024)) to production systems serving daily needs, their **personalization** capabilities become critical: an agent acting on your behalf is only as effective as its model of you.

However, these agents face a fundamental limitation: they cannot see where users spend most of their waking hours—the physical world. Current personal AI agents build user models entirely from digital traces—chat logs, files, calendars, browsing history (**PLLM Survey** (Liu et al., 2025))—while remaining blind to physical activities, environments, and embodied states. For instance, when an agent suggests scheduling a 2-hour meeting at 3pm, it doesn't know you've been standing for 6 hours and are physically exhausted—information that would fundamentally change its recommendation. Without physical context, agents cannot adapt to users' energy levels, environmental constraints, or physical conditions, resulting in generic suggestions that ignore the user's actual situation.

The central question is whether bridging this gap matters: **what value, if any, does continuous physical-world observation provide for personal AI agent personalization?**

This thesis takes an exploratory approach. Rather than assuming physical-world observation improves personalization, I design a system to discover *where* it helps and *where* it doesn't. Through a 2-week self-study, I investigate where egocentric perception (vision + audio + motion) enhances personalization and where it introduces noise. This methodology follows the autoethnographic tradition in HCI research (**Neustaedter & Sengers, 2012**), which validates deep self-study as a means of generating design insights when longitudinal deployment with users is impractical. The investigation is structured around three research questions:

**RQ1: What physical-world information becomes visible through egocentric perception that remains invisible through digital traces alone?**
*[Preview] Chapter 4 demonstrates that location, activity patterns, and environmental context become visible through continuous egocentric sensing, while fine-grained emotional states and subtle cognitive load indicators remain challenging to capture reliably.*

**RQ2: In what task contexts does this physical-world information meaningfully improve personalization, and when does it introduce noise or redundancy?**
*[Preview] Chapter 5 reveals that physical context significantly improves personalization in scheduling and activity recommendation tasks (e.g., avoiding high-energy tasks after physical exhaustion), but provides limited benefit for email composition and file organization tasks where digital traces already suffice.*

**RQ3: What design requirements emerge for integrating continuous egocentric sensing into existing agent memory architectures?**
*[Preview] Chapter 6 identifies three critical design dimensions: storage granularity (text summaries vs. key frames), privacy-utility trade-offs (retention policies, on-device processing), and abstraction mechanisms (real-time detection combined with nightly summarization).*

This thesis contributes:

1. **Empirical findings** on the conditional value of physical-world perception for personalization—documenting specific scenarios where it enhances agent adaptation (activity-aware scheduling, environmental context-matching) and where it fails to provide benefit (tasks already well-supported by digital traces). These findings are derived from 2 weeks of continuous deployment in a single-user setting.

2. **A system artifact** that demonstrates one viable integration path: extending OpenClaw's markdown-based memory architecture with egocentric multimodal input (vision, audio, motion) while preserving compatibility with text-based retrieval and reasoning. The system implements a hybrid storage strategy—text summaries for daily use, key frames for critical moments—and a two-stage abstraction pipeline combining real-time activity detection with nightly summarization.

3. **Design implications** for future embodied personal agents, including: (a) storage granularity trade-offs (text summaries are sufficient for most queries, but key frames are necessary for spatial and visual recall tasks); (b) privacy-utility trade-offs (users prefer 7-14 day retention for raw data, but indefinite retention for text summaries); and (c) abstraction mechanism requirements (purely real-time processing drains battery, purely batch processing loses temporal nuance—a hybrid approach is necessary).

By exploring both the promises and limitations of physical-world perception for personal AI agents, this thesis provides grounded evidence for a question the field has not systematically addressed: whether the substantial technical and privacy costs of continuous egocentric sensing are justified by improvements in personalization outcomes.
