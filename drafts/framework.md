# Thesis Framework: Hybrid System + Autoethnography Structure

## Methodology Positioning

**Primary Framework:** Design Science Research (DSR)
**Complementary Methods:** Research through Design (RtD) + Autoethnography

**Positioning Statement:**
> "This thesis adopts a Design Science Research approach (Hevner et al., 2004), complemented by Research through Design methodology (Zimmerman et al., 2010) and autoethnographic methods (Ellis et al., 2011) to evaluate both the technical artifact and lived experience of its use."

---

## Research Direction

### Context & Motivation

**The Rise of Personalized AI Agents:**
- OpenClaw's爆火代表了AI agent个人化的趋势
- Personalization是AI agent能否最大程度帮助用户的核心

**Current Limitation:**
- 现有personalization主要在**digital world** 和 **digital tasks**
- 缺少**physical world context**

**Core Insight:**
> 通过提供 **physical world input** (egocentric vision) 提升 AI agent 的 personalization

### Positioning

**Embodied Agent Research:**
- **Input**: Physical world (egocentric vision + audio + IMU)
- **Platform**: Smartphone (模拟智能眼镜，实际可行)
- **System**: Built on OpenClaw (non-embodied base + physical world extension)

**Why Egocentric Vision?**
- 智能眼镜最适合**持续**提供physical world input
- 第一人称视角 > 第三人称观察
- 手机作为prototype设备（电池+Wi-Fi+摄像头）

---

## Research Questions

**RQ1:** What **physical world information** is most valuable for AI agent personalization, and how does it complement existing digital world context?

**RQ2:** How should an embodied agent's **memory system** be designed to handle continuous egocentric vision input (format, storage, abstraction, decay)?

**RQ3:** To what extent does physical world input improve AI agent personalization for **digital tasks** vs **physical tasks**?

---

## Core Distinction: Non-embodied vs Embodied Agents

### Non-embodied Agents (e.g., OpenClaw)

**Input Dimension:**
- Information source: Digital interactions (messages, files, web)
- Input timing: Discrete, user-triggered
- Information density: Low-frequency, high-semantic
- Personalization signals: Explicit preferences, interaction patterns

**Task Dimension:**
- Scenarios: Digital workflows, information management
- States: Abstract, symbolic representations
- Needs: Efficiency, accuracy, personalization
- Action reversibility: High (undo, revise)
- Planning horizon: Short-term, task-specific

### Embodied Agents (This Thesis)

**Input Dimension:**
- Information source: **Physical world (egocentric vision, audio, IMU)**
- Input timing: **Continuous, passive capture**
- Information density: **High-frequency, multi-modal, raw**
- Personalization signals: **Implicit behaviors, environmental context, physical activities**

**Task Dimension:**
- Scenarios: **Physical activities, spatial navigation, real-world interactions**
- States: **Embodied, sensorimotor, situational**
- Needs: **Context awareness, proactive assistance, adaptation**
- Action reversibility: **Low (physical actions have consequences)**
- Planning horizon: **Long-term, life-integrated**

---

## Contributions

This thesis makes the following contributions:

1. **Understanding Physical World Value:**
   - Identify which physical world information is valuable for personalization
   - Compare utility for digital vs physical tasks
   - Address the uncertainty: "Is physical world input actually useful?"

2. **Memory System Design for Embodied Agents:**
   - Input format: Multimodal → text abstraction vs raw storage vs hybrid
   - Storage architecture: OpenClaw's markdown + vector DB + ?
   - Abstraction mechanisms: When/how to summarize egocentric vision
   - Decay policies: What to keep vs discard (battery/storage constraints)

3. **Empirical Evidence from Self-Study:**
   - 1-2 week autoethnographic exploration
   - Lived experience of embodied agent + continuous capture
   - Privacy concerns and personalization benefits in practice

4. **Design Framework for Embodied Personalization:**
   - Guidelines for extending non-embodied agents (like OpenClaw) with physical world input
   - Task-specific personalization strategies
   - Privacy-utility trade-offs in continuous capture

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

#### 3.1 OpenClaw: A Representative Non-embodied Agent

**Architecture Overview:**

```
OpenClaw System
│
├── Memory Layer
│   ├── MEMORY.md (Durable, curated long-term)
│   ├── memory/YYYY-MM-DD.md (Ephemeral daily logs)
│   └── Vector Database (chunked, searchable)
│
└── Identity Layer
    ├── USER.md (User info, preferences, habits)
    ├── IDENTITY.md (Agent's external identity)
    └── SOUL.md (Agent's "psyche" - personality, values, boundaries)
```

**Key Characteristics:**
- **Plain Markdown Files**: Low complexity, high transparency
- **File-based Truth**: AI only remembers what's written to disk
- **Two-tier Memory**: Ephemeral (daily) + Durable (curated)
- **Non-embodied**: Text-based, digital world only

**Limitation:**
> No physical world context → Limited personalization for embodied activities

#### 3.2 Extending to Embodied: Adding Physical World Input

**Proposed Extension:**

```
Enhanced Embodied System
│
├── Physical Input Layer (NEW)
│   ├── Egocentric Vision (video frames)
│   ├── Audio (ambient sound, speech)
│   └── IMU (motion, activity)
│
├── Processing Layer (NEW)
│   ├── On-device privacy filter
│   ├── Activity recognition
│   ├── Semantic extraction
│   └── Summarization
│
├── Memory Layer (Extended)
│   ├── OpenClaw's original structure
│   ├── + Physical world logs
│   ├── + Cross-modal indexing
│   └── + Temporal-spatial metadata
│
└── Identity Layer (Inherited)
    └── OpenClaw's USER + SOUL + IDENTITY
```

**Design Challenges:**
1. **Format**: Raw video vs text summaries vs hybrid?
2. **Storage**: How much to keep? Decay policy?
3. **Abstraction**: When to summarize? What granularity?
4. **Retrieval**: How to query multimodal memories?
5. **Integration**: How to merge with existing markdown system?

#### 3.3 Core Concepts

**Physical World Information Types:**
- **Activities**: What am I doing? (climbing, working, commuting)
- **Environment**: Where am I? (gym, office, home)
- **Social**: Who am I with? (alone, with friends)
- **Objects**: What am I interacting with? (phone, laptop, coffee)
- **Emotions**: How am I feeling? (stressed, relaxed, engaged)

**Potential Value for Personalization:**
1. **Context-aware responses**: "You seem tired from climbing, want a lighter task?"
2. **Proactive suggestions**: "You usually call Sarah after the gym"
3. **Behavior pattern discovery**: "You're most productive on Tuesday mornings"
4. **Health insights**: "You've been sedentary for 4 hours"

**Uncertainty (Research Questions):**
- Is this information actually useful?
- For which tasks? (digital vs physical)
- How much detail is needed?
- Does it justify the cost (battery, storage, privacy)?

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

## Critical Uncertainties & Research Questions

### ❓ Problem 1: Application Scenarios

**The Core Question:**
> Physical world input能提升AI agent personalization到**什么程度**？

**Sub-questions:**
1. **For Digital Tasks:**
   - Does knowing I'm at the gym help with email drafting?
   - Does seeing my workspace help with task prioritization?
   - **Hypothesis**: Limited direct utility, potential indirect context

2. **For Physical Tasks:**
   - Better exercise recommendations if AI sees my workouts?
   - Smarter scheduling if AI knows my commute patterns?
   - **Problem**: What ARE "physical tasks" for AI agents?
   - **Gap**: No established evaluation methods for embodied agent tasks

3. **For Hybrid Tasks:**
   - Context-aware reminders (location + activity)
   - Proactive suggestions (behavior patterns)
   - **Challenge**: Defining "success" metrics

**Research Approach:**
- **Exploratory**: Don't assume utility upfront
- **Empirical**: Discover through self-study what's actually valuable
- **Honest**: Report both benefits and limitations

---

### ❓ Problem 2: Memory System Design

**The Core Challenge:**
> 如何将连续的physical world input转化为有用的memory？

**Design Decisions:**

#### A. Input Format

**Option 1: Text-only (Summarized)**
```
✅ Pros:
- Compatible with OpenClaw's markdown system
- Low storage
- Fast retrieval

❌ Cons:
- Information loss
- Summarization errors
- No raw data for re-analysis
```

**Option 2: Raw Files (Video/Audio)**
```
✅ Pros:
- Complete information
- Re-processable

❌ Cons:
- Storage explosion (~100GB/week)
- Privacy nightmare
- Slow retrieval
```

**Option 3: Hybrid**
```
✅ Pros:
- Text summaries for daily use
- Key frames/clips for important moments
- Balanced storage

❌ Cons:
- Complex indexing
- Which moments to keep raw?

👉 **Most likely choice**
```

#### B. Storage Architecture

**Base: OpenClaw's Markdown**
```
memory/
├── 2026-03-07.md (text summary of physical world)
└── 2026-03-07/ (raw multimodal data)
    ├── frames/ (key frames)
    ├── audio/ (audio clips)
    └── metadata.json
```

**Extended: Vector DB**
```
- Text embeddings from summaries
- Image embeddings from key frames
- Cross-modal retrieval
```

#### C. Abstraction Mechanism

**When to Summarize?**
- Real-time? (battery drain)
- End of day? (memory limit)
- Event-driven? (complex detection)

**What Granularity?**
- "Chris was at gym from 2-4pm" (high-level)
- "Chris did bench press, 3 sets, 10 reps each" (medium)
- [Full video] (raw)

**How to Extract?**
- Vision models (CLIP, BLIP)
- Speech-to-text (Whisper)
- Activity recognition (EgoLog's methods)

#### D. Decay Policy

**What to Keep?**
- High-level patterns (indefinitely)
- Daily summaries (30-90 days)
- Raw data (7-14 days? Or delete immediately?)

**Based on:**
- Importance scores (LLM rating)
- Retrieval frequency (usage-based)
- Storage constraints (practical limits)

---

### ❓ Problem 3: Information Value

**The Fundamental Question:**
> Physical world information到底有没有用？

**Skepticism:**
- "Digital interactions (emails, messages) seem more useful"
- "Do you really need to see my lunch to help me better?"
- "Context windows are limited - prioritize digital data"

**Counter-arguments:**
- Physical activities reveal **emotions** (stress from rushing)
- Environment shapes **cognitive state** (focus in quiet spaces)
- Patterns emerge from **holistic view** (work-life balance)

**Research Strategy:**
1. **Don't assume** utility upfront
2. **Collect data** first (continuous capture)
3. **Analyze post-hoc**: Which physical information was actually queried?
4. **Report honestly**: If limited utility, say so

---

## Methodology: Self-Study (Autoethnography)

### Timeline
- **Duration**: 1-2 weeks (tight deadline: 3-4 weeks total)
- **Approach**: Autoethnography / Self-study
- **Data collection**: Continuous egocentric capture + reflective journaling

### Legitimacy Strategies (Neustaedter & Sengers, 2012)

1. **Depth over breadth**: "I studied myself in depth for 2 weeks"
2. **Insider expertise**: Unique access to subtle experiences
3. **Transparency**: Full documentation of system + process
4. **Rigor**: Daily reflection logs, systematic analysis
5. **Theoretical contribution**: Connect to embodied cognition, agent personalization
6. **Artifact creation**: Open-source system (OpenClaw extension)

### Data Sources

**Quantitative:**
- System logs (capture frequency, retrieval queries)
- Performance metrics (battery, storage, latency)
- Usage statistics (which features used most)

**Qualitative:**
- Daily reflection journal (evening, 15-30 min)
- Critical incident documentation (surprising moments)
- Privacy concerns log (when did I feel uncomfortable?)

### Analysis

**Research Questions → Analysis Methods:**

| RQ | Analysis |
|----|----------|
| RQ1: Information value | Query log analysis, reflection themes |
| RQ2: Memory design | Storage growth, retrieval effectiveness |
| RQ3: Task impact | Digital vs physical task performance |

---

*Framework version: 2.0*
*Last updated: 2026-03-07*
*Based on: Embodied Agent Personalization with Egocentric Vision*
