# Thesis Framework: Hybrid System + Autoethnography Structure

## Methodology Positioning

**Primary Framework:** Design Science Research (DSR)
**Complementary Methods:** Research through Design (RtD) + Autoethnography

**Positioning Statement:**
> "This thesis adopts a Design Science Research approach (Hevner et al., 2004), complemented by Research through Design methodology (Zimmerman et al., 2010) and autoethnographic methods (Ellis et al., 2011) to evaluate both the technical artifact and lived experience of its use."

---

## Research Questions

**RQ1:** How can we design a privacy-preserving life logging system that enables **understanding beyond classification**, with queryable, retrievable, and reasoning-capable personal memory?

**RQ2:** What is the lived experience of using a personalized life logging agent over a longitudinal self-study, particularly regarding privacy concerns, memory utility, and agent integration?

**RQ3:** What design implications emerge from the intersection of cognitive memory theory, agent personalization, and embodied life logging practice?

---

## Contributions

This thesis makes the following contributions:

1. **System Artifact:** A privacy-first life logging system that integrates:
   - **Understanding beyond classification** (vs EgoLog's HAR focus)
   - **Proactive agent integration** (vs passive recording systems)
   - **Multi-dimensional memory** (episodic + semantic + user profile)
   - **Privacy-by-design** (on-device processing, user control)

2. **Empirical Findings:** Insights from a longitudinal self-study revealing:
   - Long-term usage patterns and privacy concerns
   - Memory retrieval effectiveness and limitations
   - Agent integration challenges and opportunities
   - Cognitive load management strategies

3. **Design Implications:** Guidelines for personalized life logging agents:
   - Memory architecture design (ephemeral vs durable, episodic vs semantic)
   - Personalization strategies (know vs do, input vs model vs objective)
   - Self-study methodology (legitimacy strategies, rigor requirements)
   - Privacy-utility trade-offs in practice

---

## Thesis Structure

### 1. Introduction (2-3 pages)

**Opening:** Hook + problem statement + personal motivation

**Motivation:**
- Growing interest in personal AI agents
- Need for continuous life context
- Privacy concerns with existing solutions
- Gap in end-to-end systems

**Research Questions:**
- RQ1: Design question
- RQ2: Experience question
- RQ3: Synthesis question

**Contributions:** Explicit list (artifact, findings, implications)

**Paper Organization:** Brief roadmap

---

### 2. Background & Related Work (3-4 pages)

#### 2.1 Life Logging Systems
- **Classic:** MyLifeBits (2000s) - Foundation of life logging
- **Modern:** EgoLog (2026) - HAR-focused, continuous tracking + multimodal sensing
- **Limitation:** Classification-focused, limited understanding and agent integration

#### 2.2 Personalized LLMs & Agents
- **PLLM Taxonomy** (2025): Input Level (prompting), Model Level (adaptation), Objective Level (alignment)
- **PRIME** (2025): Cognitive dual-memory (episodic + semantic) + personalized thinking
- **Persistent Memory Systems** (2025): STM → summaries → LTM → user profile pipeline
- **Personalized Agents** (2026): Profile modeling, memory, planning, action execution

#### 2.3 Embodied Agent Memory
- **MEMENTO** (2026): Knowledge graph-based user profile to address information overload
- **Generative Agents** (2023): Memory stream + reflection architecture
- **MemGPT** (2023): Virtual context management, self-editing memory
- **Modern Systems:** Mem0 (memory-as-a-service), A-MEM (Zettelkasten-inspired), Memoria (weighted knowledge graphs)

#### 2.4 Cognitive Architectures
- **Classics:** Soar (1987), ACT-R (1993) - Activation-based retrieval, memory decay
- **Modern Applications:** OpenClaw's two-tier memory (ephemeral + durable)
- **Identity Layer:** SOUL.md, USER.md, IDENTITY.md (personality + preferences)

#### 2.5 Autoethnographic Methods
- **Autobiographical Design:** Neustaedter & Sengers (2012) - Guidelines for self-study validity
- **Legitimacy Strategies:** Depth over breadth, insider expertise, transparency, rigor, theoretical contribution, artifact creation

#### 2.6 Research Gap
**Missing in existing work:**
1. **Long-term self-study** of life logging + agent memory (most are short-term user studies or n=1 demos)
2. **Integration** of cognitive theory + agent memory + personalization in embodied context
3. **Privacy-by-design** life logging system with formal evaluation
4. **Understanding beyond classification** - proactive agent vs passive recorder

**This thesis addresses:** All four gaps through system artifact + longitudinal self-study + design implications

---

### 3. Conceptual Framework (1-2 pages)

#### 3.1 Key Concepts

**Continuous Life Logging:**
- Definition: Unobtrusive, long-term capture of daily activities
- Scope: Visual (video), audio, motion (IMU), context (GPS)
- Challenges: Battery, storage, privacy

**Privacy-by-Design:**
- Core principle: Privacy integrated from the start, not added later
- Implementation: On-device processing, minimal data exposure
- User control: Transparent, configurable privacy settings

**Memory-Augmented AI Agents:**
- Role: Personal assistant with access to life context
- Integration: How memory enhances agent capabilities
- Use cases: Contextual reminders, behavior insights, personalized assistance

#### 3.2 Design Principles

1. **Minimizing Burden:** System should not interfere with daily life
2. **Privacy First:** User maintains control over all data
3. **Meaningful Memory:** Capture what matters, ignore what doesn't
4. **Agent Synergy:** Memory should enhance, not replace, agent intelligence

---

### 4. System Design & Implementation (4-5 pages)

#### 4.1 System Overview

**Architecture Diagram:** (to be created)
```
[Phone Sensors] → [On-Device Processing] → [Encrypted Storage] → [Agent Interface]
     ↓                      ↓                       ↓                    ↓
  Video/Audio          Privacy Filter         Memory Index         Query API
  IMU/GPS              Activity Recognition   Retrieval System     LLM Integration
```

**Key Components:**
1. Data Capture (iOS app)
2. Privacy Processing (on-device)
3. Memory System (storage + retrieval)
4. Agent Integration (OpenClaw)

#### 4.2 Data Capture Module

**Sensors:**
- Video: Camera (periodic capture, not continuous)
- Audio: Microphone (activity detection)
- Motion: IMU (accelerometer, gyroscope)
- Context: GPS, time, app usage

**Capture Strategy:**
- Adaptive sensing based on activity detection
- Battery-aware scheduling
- User-configurable privacy zones

#### 4.3 Privacy-Preserving Processing

**On-Device Pipeline:**
1. **Face Obfuscation:** Blur faces in video
2. **Text Redaction:** Remove sensitive text
3. **Activity Recognition:** Classify activities locally
4. **Semantic Embedding:** Create searchable embeddings
5. **Metadata Extraction:** Time, location, duration

**Privacy Guarantees:**
- No raw video/audio leaves device
- Only embeddings and metadata stored
- User controls what's captured

#### 4.4 Memory System

**Memory Types (Simplified from MIRIX):**
1. **Episodic:** Specific events with temporal context
2. **Semantic:** General knowledge and patterns
3. **Procedural:** Routine behaviors and habits

**Storage:**
- Local encrypted database
- Cloud backup (optional, encrypted)
- Efficient indexing for retrieval

**Retrieval:**
- Semantic search via embeddings
- Temporal queries (e.g., "last week")
- Activity-based queries (e.g., "when I was cooking")

#### 4.5 Agent Integration

**OpenClaw Integration:**
- Memory API for agent access
- Context injection into prompts
- Personalized responses

**Use Cases:**
1. "What did I do last Tuesday?"
2. "Remind me when I last took medication"
3. "How much time did I spend on X this week?"
4. "Suggest activities based on my patterns"

#### 4.6 Implementation Details

**iOS App:**
- Swift / SwiftUI
- CoreML for on-device ML
- AVFoundation for media capture
- CoreMotion for IMU

**Backend:**
- Node.js / Express
- Vector database (Pinecone / Weaviate)
- LLM integration (OpenAI / local)

**Web Dashboard:**
- React / Next.js
- Data visualization
- Privacy controls

---

### 5. Methodology (2-3 pages)

#### 5.1 Design Science Research Framework

**Justification:**
- System artifact is primary contribution
- Clear problem → solution → evaluation cycle
- Standard in HCI systems research

**DSR Cycle:**
1. **Problem Identification:** Life logging systems lack privacy + agent integration
2. **Solution Design:** Privacy-by-design system with memory
3. **Development:** Build working prototype
4. **Evaluation:** Technical tests + self-study
5. **Communication:** This thesis

**Reference:** Hevner et al. (2004), Peffers et al. (2007)

#### 5.2 Autoethnographic Method

**Justification:**
- Long-term usage patterns invisible in short studies
- Insider access to nuanced experiences
- Growing acceptance in HCI (Neustaedter & Sengers, 2012)

**Data Sources:**
- **System logs:** Battery, storage, performance metrics
- **Usage data:** Capture frequency, activity distribution
- **Personal journal:** Daily reflections, critical incidents
- **Screenshots/Photos:** Interface usage examples

**Data Collection:**
- 7-day continuous self-experiment
- Daily evening reflection (15-30 min)
- Automatic system metrics logging
- Critical incident documentation

**Analysis Approach:**
- **Quantitative:** System performance metrics
- **Qualitative:** Thematic analysis of journal entries
- **Integration:** Triangulation of technical + experiential data

**Rigor Strategies:**
- **Reflexivity:** Explicit positionality statement
- **Transparency:** Full documentation of process
- **Thick Description:** Rich context for transferability
- **Peer Debriefing:** Regular advisor discussions

**Reference:** Ellis et al. (2011), Neustaedter & Sengers (2012)

#### 5.3 Positionality Statement

> "As both the designer and primary user of this system, I occupy a unique dual position. This insider perspective enables deep understanding of the lived experience, while also introducing potential bias. I address this through explicit reflexivity, transparent documentation, and triangulation with technical data."

---

### 6. Evaluation & Results (4-5 pages)

#### 6.1 Technical Evaluation

**Performance Metrics:**
- **Battery Consumption:** % per day
- **Storage Usage:** GB per day
- **Processing Latency:** Time per activity recognition
- **Accuracy:** Activity recognition performance

**System Reliability:**
- Uptime / data loss rate
- Error handling effectiveness
- User intervention requirements

**Privacy Metrics:**
- Face obfuscation success rate
- Text redaction accuracy
- Data exposure assessment

**Comparison:**
- Baseline: Continuous capture (no privacy)
- Optimized: Adaptive sensing + privacy
- Improvement: Battery/storage/privacy gains

#### 6.2 Autoethnographic Findings

**Theme 1: [To be determined from data]**
- Pattern observed
- Representative quote/experience
- Interpretation

**Theme 2: [To be determined from data]**
- Pattern observed
- Representative quote/experience
- Interpretation

**Theme 3: [To be determined from data]**
- Pattern observed
- Representative quote/experience
- Interpretation

**Critical Incidents:**
- Moment 1: [Surprising/insightful experience]
- Moment 2: [Unexpected challenge or discovery]
- Moment 3: [Breakthrough or realization]

**Temporal Patterns:**
- Day 1-2: [Early experience]
- Day 3-5: [Adjustment period]
- Day 6-7: [Stabilization / insights]

---

### 7. Discussion (3-4 pages)

#### 7.1 Synthesis of Findings

**Technical + Experiential Integration:**
- How do system performance and personal experience relate?
- Where do technical metrics miss important aspects?
- What does self-study reveal that technical tests cannot?

#### 7.2 Design Implications

**For System Designers:**
- Guideline 1: [Based on findings]
- Guideline 2: [Based on findings]
- Guideline 3: [Based on findings]

**For Privacy-First Systems:**
- Lessons about user control and transparency
- Balancing capture vs. privacy

**For Agent Integration:**
- How memory enhances agent capabilities
- Designing for meaningful agent-memory synergy

#### 7.3 Theoretical Contributions

**Extending Existing Frameworks:**
- Connection to autobiographical design (Neustaedter & Sengers)
- Contribution to personal informatics literature
- Privacy-by-design principles in practice

#### 7.4 Limitations

**Honest Acknowledgment:**
- **Sample size:** n=1, limited generalizability
- **Duration:** 7 days may not capture long-term patterns
- **Researcher bias:** Dual role as designer and subject
- **Technical scope:** Simplified system, not production-ready

**Mitigation Strategies:**
- Transparency about limitations
- Focus on depth over breadth
- Clear positioning as exploratory study

#### 7.5 Future Work

**Short-term Extensions:**
- Longer self-study (14-30 days)
- Additional participants (3-5 users)
- More comprehensive evaluation

**Long-term Directions:**
- Production deployment
- Advanced memory features
- Multi-device support
- Broader agent capabilities

---

### 8. Conclusion (1-2 pages)

**Summary:**
- Restate problem and approach
- Recap key contributions
- Highlight main findings

**Personal Reflection:**
- What I learned from this process
- How this changed my perspective on life logging

**Broader Impact:**
- Implications for personal AI agents
- Future of privacy-preserving systems
- Vision for human-AI collaboration

---

## Key References

### Methodology
- Hevner, A. R., et al. (2004). Design Science in Information Systems Research. *MIS Quarterly*.
- Zimmerman, J., et al. (2010). An Analysis and Critique of Research through Design. *CHI 2010*.
- Neustaedter, C., & Sengers, P. (2012). Autobiographical Design in HCI Research. *DIS 2012*.
- Ellis, C., et al. (2011). Autoethnography: An Overview. *Historical Social Research*.

### Technical Domain
- He, X., et al. (2026). EgoLog: Ego-Centric Fine-Grained Daily Log. arXiv:2504.02624.
- Wang, S., et al. (2025). MIRIX: AI Smart Glasses with Multimodal Memory. arXiv:2507.07957.
- [Other technical references to be added]

### Privacy & Ethics
- [Privacy references to be added]

---

## Writing Timeline

**Week 1 (Days 1-7):**
- [ ] Introduction (Day 1-2)
- [ ] Related Work (Day 3-5)
- [ ] Conceptual Framework (Day 5-6)
- [ ] Methodology (Day 6-7)

**Week 2 (Days 8-14):**
- [ ] System Design (refine during experiment)
- [ ] Collect data (all week)

**Week 3 (Days 15-21):**
- [ ] Evaluation & Results (Day 15-17)
- [ ] Discussion (Day 18-19)
- [ ] Conclusion (Day 19)
- [ ] Revision & Defense Prep (Day 20-21)

---

*Framework version: 1.0*
*Last updated: 2026-03-03*
*Structure based on: Hybrid System + Autoethnography (Advisor recommendation)*
