# 1. Introduction

A new category of AI system is taking shape—the **personal AI agent**—a system designed to serve a single individual continuously across their entire daily life by maintaining persistent memory, acting proactively, and spanning multiple domains. OpenClaw (2025) exemplifies this shift: a text-based agent that remembers conversations, anticipates needs, and operates across a user's digital ecosystem. As these agents transition from experimental prototypes (**Generative Agents** (Park et al., 2023); **A Survey on Large Language Model based Autonomous Agents** (2023)) to daily tools, their **personalization** capabilities become structurally consequential (*cites: personalization research*): an agent acting on your behalf is only as effective as its model of you.

However, this creates a fundamental blind spot: agents cannot see where users spend most of their waking hours—the physical world. Current personal AI agents build user models entirely from digital traces—chat logs, files, calendars, browsing history (**PLLM** (Zhang et al., 2025))—while remaining oblivious to physical activities, environments, and embodied states. For instance, when an agent suggests scheduling a 2-hour meeting at 3pm, it doesn't know you've been standing for 6 hours and are physically exhausted—information that would fundamentally change its recommendation. Without this context, agents cannot adapt to users' energy levels, environmental constraints, or physical conditions, leading to generic suggestions that ignore the user's actual situation. The question is whether bridging this gap matters: **what value, if any, does continuous physical-world observation provide for personal AI agent personalization?**

This thesis takes an exploratory approach. Rather than assuming value, I design a system to discover where it exists and where it doesn't. Through a 2-week self-study, I investigate where egocentric perception (vision + audio + motion) enhances personalization and where it introduces noise. The investigation is structured around three research questions:

**RQ1: What physical-world information can egocentric perception capture that digital traces cannot?**
*[Preview] Chapter 4 shows that location, activity, and environmental context become visible, while fine-grained emotional states remain challenging.*

**RQ2: In what contexts does this information meaningfully improve personalization, and when does it introduce noise?**
*[Preview] Chapter 5 reveals value in activity-aware scheduling but limited benefit for email composition tasks.*

**RQ3: What design requirements emerge for integrating egocentric sensing into agent memory systems?**
*[Preview] Chapter 6 identifies storage granularity, privacy trade-offs, and abstraction mechanisms as key design dimensions.*

This thesis contributes:
1. **Empirical findings** on where physical perception aids personalization (activity-aware scheduling, environmental adaptation) and where it doesn't (email drafting, file organization)
2. **A system artifact** integrating egocentric vision into OpenClaw's markdown-based memory architecture
3. **Design implications** for storage granularity (text summaries vs. key frames), privacy trade-offs (14-day retention policy), and abstraction mechanisms (real-time detection + nightly summarization)
