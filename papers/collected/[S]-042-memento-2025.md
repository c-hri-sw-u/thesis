# 042 - MEMENTO: Embodied Agents Meet Personalization (2025)

**Authors:** Taeyoon Kwon, Dongwook Choi, Sunghwan Kim, Hyojun Kim, Seungjun Moon, Beong-woo Kwak, Kuan-Hao Huang, Jinyoung Yeo

**Source:** arXiv:2505.16348 | Accepted at ICLR 2026

## Summary

MEMENTO presents a comprehensive evaluation framework investigating memory utilization in personalized embodied agents. The authors address the challenge of providing personalized assistance that leverages user-specific knowledge from past interactions. They evaluate agents along two critical dimensions: object semantics (identifying objects based on personal meaning) and user patterns (recalling behavioral routines). Their experiments reveal that while current agents can recall simple object semantics, they struggle to apply sequential user patterns to planning. Two critical bottlenecks identified are information overload and coordination failures when handling multiple memories. Based on these findings, they design a hierarchical knowledge graph-based user-profile memory module that separately manages personalized knowledge. This architecture achieves substantial improvements on both single and joint-memory tasks, demonstrating the value of episodic memory for providing both personalized knowledge and in-context learning benefits.

## Key Contributions

- MEMENTO evaluation framework with single-memory and joint-memory tasks
- Identification of information overload and coordination as key bottlenecks
- Hierarchical knowledge graph-based memory architecture for user profiles
- Empirical validation showing improved performance on memory-dependent tasks

## Relevance to Thesis

This paper is directly relevant to Section 2.4 (Embodied Perception) and Section 2.2 (Personalization in AI Agents), providing both evaluation methodology and architectural solutions for personalized embodied agents.
