# 045 - Memoria: A Scalable Agentic Memory Framework for Personalized Conversational AI (2025)

**Authors:** Samarth Sarin et al.

**Source:** arXiv:2512.12686 | Accepted at 5th International Conference of AIML Systems 2025, Bangalore, India

## Summary

Memoria presents a modular memory framework that augments LLM-based conversational systems with persistent, interpretable, and context-rich memory. The paper addresses the challenge of enabling LLMs to maintain continuity, personalization, and long-term context across extended user interactions—critical capabilities for deploying LLMs as truly interactive and adaptive agents. Memoria integrates two complementary components: dynamic session-level summarization and a weighted knowledge graph (KG)-based user modeling engine that incrementally captures user traits, preferences, and behavioral patterns as structured entities and relationships. This hybrid architecture enables both short-term dialogue coherence and long-term personalization while operating within the token constraints of modern LLMs. The authors demonstrate how Memoria bridges the gap between stateless LLM interfaces and agentic memory systems, achieving up to 38.7% latency reduction compared to full context prompting while maintaining high accuracy. The framework offers a practical solution for industry applications requiring adaptive and evolving user experiences through recency-aware triplet weighting that preserves contextual fidelity while remaining cost-efficient and scalable.

## Key Contributions

- Modular memory framework with session summarization and knowledge graph components
- Weighted knowledge graph for incremental user profile building
- Recency-aware triplet weighting for memory prioritization
- Significant latency reduction (38.7%) while maintaining accuracy
- Evaluation on LongMemEvals demonstrating effectiveness

## Relevance to Thesis

This paper is highly relevant to Section 2.3 (Memory Architectures), providing a practical implementation of agentic memory systems that balances personalization, scalability, and efficiency for conversational AI applications.
