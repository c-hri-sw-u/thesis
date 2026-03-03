# Research Update: 2026-03-03

## Research Lead Summary for Chris Wu's Thesis

**Thesis Focus:** End-to-End System for Continuous Life Logging and Personalized AI Agents

---

## 1. Current State of Literature Collection

### Papers Collected (11 papers with PDFs)
| Paper | Category | Relevance |
|-------|----------|-----------|
| Embodied AI Agents (2026) | World Model | High |
| MemVerse (2025) | Multimodal Memory | **Very High** |
| VideoAgent (2025) | Video Understanding | High |
| Memory Survey (2025) | Memory Systems | **Very High** |
| VINCI (2025) | Multimodal | High |
| MARC (2026) | Memory | Medium |
| VLM Survey (2025) | Vision-Language | Medium |
| Mem2Ego (2025) | Egocentric | High |
| Long-term Memory (2025) | Memory | High |
| A-Mem (2025) | Memory | **Very High** |
| Mem0 (2024) | Memory | High |

### Gaps Identified
- **Privacy-preserving systems:** Only 2 papers collected, 8 marked "To Find"
- **End-to-end continuous logging systems:** Very few practical deployments
- **Long-term user studies:** Most HCI studies are short-term (days/weeks)
- **On-device AI implementation:** Limited technical papers

---

## 2. Key New Papers Found (2025-2026)

### 🔥 HIGHLY RELEVANT - Must Read

#### **EgoPrivacy: What Your First-Person Camera Says About You?** (ICML 2025)
- **arXiv:** 2506.12258
- **Why Critical:** First large-scale benchmark for egocentric video privacy risks
- **Key Findings:**
  - Foundation models can recover wearer identity, scene, gender, race with 70-80% accuracy
  - Three privacy types: demographic, individual, situational
  - Proposes Retrieval-Augmented Attack strategy
- **Relevance to Thesis:** Directly supports RQ2 (Privacy Preservation) - demonstrates the privacy threats we need to address

#### **EgoLog: Ego-Centric Fine-Grained Daily Log with Ubiquitous Wearables** (Jan 2026)
- **arXiv:** 2504.02624 (v3)
- **Why Critical:** VERY CLOSE to our thesis - continuous daily logging with wearables
- **Key Innovations:**
  - Audio-IMU fusion for temporal + spatial understanding
  - On-device keyword spotting (privacy-preserving!)
  - LLM integration for scenario recognition
  - Knowledge transferred back to device for efficient inference
- **Relevance to Thesis:** Almost identical scope! Must compare and differentiate

#### **MIRIX: Multi-Agent Memory System for LLM-Based Agents** (July 2025)
- **arXiv:** 2507.07957
- **Why Critical:** Most comprehensive multimodal memory system to date
- **Key Innovations:**
  - Six memory types: Core, Episodic, Semantic, Procedural, Resource, Knowledge Vault
  - Multimodal support (transcends text!)
  - Real-time screen monitoring with local storage
  - 99.9% storage reduction vs RAG baseline
- **Relevance to Thesis:** Direct competitor for memory architecture - must cite and compare

#### **M3-Agent: A Multimodal Agent with Long-Term Memory** (ByteDance, Oct 2025)
- **arXiv:** 2508.09736
- **Why Critical:** Multimodal long-term memory from industry (ByteDance)
- **Key Innovations:**
  - Entity-centric memory organization (faces, voices, knowledge)
  - Trained via reinforcement learning
  - M3-Bench benchmark (100 robot videos + 920 web videos)
  - Outperforms GPT-4o and Gemini-1.5-pro
- **Relevance to Thesis:** Shows industry interest, provides benchmark for comparison

#### **TeleMem: Building Long-Term and Multimodal Memory for Agentic AI** (Jan 2026)
- **arXiv:** 2601.06037
- **Why Critical:** Latest multimodal memory with video understanding
- **Key Innovations:**
  - Narrative dynamic extraction for user profiles
  - Structured writing pipeline (batch, retrieve, cluster, consolidate)
  - ReAct-style reasoning for video understanding
  - 19% higher accuracy, 43% fewer tokens, 2.1x speedup vs Mem0
- **Relevance to Thesis:** State-of-the-art baseline to compare against

#### **A-MEM: Agentic Memory for LLM Agents** (NeurIPS 2025)
- **arXiv:** 2502.12110
- **Why Critical:** NeurIPS paper on Zettelkasten-inspired memory
- **Key Innovations:**
  - Dynamic indexing and linking (knowledge networks)
  - Memory evolution (update historical memories)
  - Comprehensive notes with contextual descriptions, keywords, tags
- **Relevance to Thesis:** Alternative memory organization approach

### 📌 MEDIUM RELEVANCE - Should Read

#### **Extra-Lightweight AI-Based Privacy Preserving Framework for Egocentric Wearable Cameras** (CVPR 2025 Workshop)
- **Focus:** On-device privacy protection
- **Relevance:** Supports RQ2 privacy component

#### **WorldMM: Dynamic Multimodal Memory Agent for Long Video Reasoning** (Dec 2025)
- **Focus:** Long video understanding
- **Relevance:** Technical approach for video memory

#### **Memoria: A Scalable Agentic Memory Framework for Personalized Conversational AI** (Dec 2025)
- **arXiv:** 2512.12686
- **Focus:** Scalable personalized memory
- **Relevance:** Architecture reference

---

## 3. Critical Analysis: Research Gaps for Chris's Thesis

### Gap 1: End-to-End Privacy-Preserving System
**What's Missing:** Most papers focus on EITHER:
- Memory systems (without privacy considerations)
- Privacy techniques (without full system integration)

**Our Opportunity:** Build a complete pipeline with privacy-by-design from the start

### Gap 2: Continuous Phone-Based Life Logging
**What's Missing:** Most systems use:
- Smart glasses / dedicated devices (not phones)
- Controlled lab environments
- Limited duration recordings

**Our Opportunity:** 24/7 phone-based system (more accessible, more challenging)

### Gap 3: Long-Term User Studies with Deep Personalization
**What's Missing:** Most user studies are:
- Short-term (days to weeks)
- Focus on functional preferences
- Don't test "creepy threshold" systematically

**Our Opportunity:** 2-4 week study with emotional understanding and boundary exploration

### Gap 4: Multimodal Memory with Egocentric Video Focus
**What's Missing:** Memory systems are mostly:
- Text-based (MemGPT, Mem0, A-MEM)
- Or multimodal but not egocentric-focused

**Our Opportunity:** First-person video as primary modality with audio/IMU fusion

---

## 4. Recommendations for Next Steps

### Immediate Priority (This Week)

1. **Read EgoLog carefully** - It's the closest existing work to our thesis
   - Differentiate: What can we do that they don't?
   - Possible angles: Privacy focus, agent integration, longer deployment

2. **Read MIRIX carefully** - Most sophisticated multimodal memory system
   - Evaluate their six-memory-type architecture
   - Consider adapting or simplifying for phone deployment

3. **Read EgoPrivacy** - Critical for understanding privacy threats
   - Use their benchmark to evaluate our privacy measures

### Medium Priority (Next 2 Weeks)

4. **Compare TeleMem vs M3-Agent vs MemVerse**
   - All handle multimodal memory
   - Identify trade-offs and design choices
   - Determine which approaches fit our constraints

5. **Survey the Agent-Memory-Paper-List GitHub**
   - Comprehensive list of 50+ recent papers
   - Identify any we're missing

### Thesis Positioning

Based on this literature review, Chris's thesis can be positioned as:

> **"The first end-to-end, phone-based, privacy-preserving life logging system with integrated personalized AI agents, validated through longitudinal user study."**

**Key Differentiators:**
1. **Phone-based** (vs smart glasses): More accessible, harder constraints
2. **Privacy-by-design** (vs add-on): Privacy throughout pipeline
3. **End-to-end** (vs components): Complete system integration
4. **Long-term user study** (vs short-term): 2-4 weeks with deep analysis
5. **Agent integration** (vs memory-only): Actual AI agent use cases

---

## 5. Paper Summary Table (New Finds)

| Paper | Venue | Memory | Privacy | Multimodal | System | User Study |
|-------|-------|--------|---------|------------|--------|------------|
| EgoLog | arXiv 2026 | ✓ | Partial | Audio+IMU | ✓ | Limited |
| MIRIX | arXiv 2025 | ✓✓✓ | ✓ | ✓✓✓ | ✓ | ✗ |
| M3-Agent | arXiv 2025 | ✓✓ | ✗ | ✓✓ | ✓ | Benchmark |
| TeleMem | arXiv 2026 | ✓✓ | ✗ | ✓✓ | ✓ | Benchmark |
| EgoPrivacy | ICML 2025 | ✗ | ✓✓✓ | Video | ✗ | ✗ |
| A-MEM | NeurIPS 2025 | ✓✓ | ✗ | Planned | ✗ | ✗ |
| **Our Thesis** | - | ✓✓ | ✓✓✓ | ✓✓✓ | ✓✓✓ | ✓✓✓ |

Legend: ✓ = present, ✓✓ = significant, ✓✓✓ = core focus

---

## 6. Open Questions for Chris

1. **EgoLog overlaps significantly with our scope.** Should we:
   - Pivot to differentiate more clearly?
   - Focus more on privacy (their weakness)?
   - Emphasize agent integration (they don't have one)?

2. **MIRIX's six-memory architecture** is sophisticated. Should we:
   - Adopt their structure?
   - Simplify for phone deployment?
   - Propose a different organization?

3. **User study duration:** The lit review suggests 2-4 weeks is longer than most studies. Is this feasible?

4. **Privacy benchmark:** Should we use EgoPrivacy's benchmark to evaluate our system?

---

*Compiled by: Research Lead Subagent*
*Date: 2026-03-03*
*Next Review: After Chris's feedback*
