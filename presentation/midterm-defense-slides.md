# Thesis Midterm Defense Slides

**Title:** Physical-World Observation for Personal AI Agent Personalization
**Author:** Chris Wu
**Date:** March 2026
**Duration:** 15-20 minutes (8-9 min presentation + 7 min Q&A)
**Slides:** 14 slides

---

# SLIDE 1: Title (30s)

## Physical-World Observation for Personal AI Agent Personalization

### *Towards More Physical-Aware Personalization*

**Chris Wu**
Carnegie Mellon University
March 2026

---

# SLIDE 2: Motivation - Part 1 (15s)

## Personal AI Agents Are Here

**Not Research Demos—Real Deployment**

- Production systems: OpenCLAW, Letta, PAI
- Persistent, multi-domain, long-term assistance
- Already deployed, already used

### **This is happening now**

[Visual: Logos of OpenCLAW, Letta, PAI with deployment numbers if available]

---

# SLIDE 3: Motivation - Part 2 (15s)

## Why Personalization Matters

### **Agents That Know You > Agents That Don't**

- **Generic agent:** Same behavior for everyone
- **Personalized agent:**
  - Adapts to your preferences
  - Learns what works for you
  - Avoids what doesn't

### **Personalization = Effectiveness**

- ✅ Better recommendations
- ✅ Fewer interruptions
- ✅ More relevant help

**Personalization is the key differentiator**

---

# SLIDE 4: Motivation - Part 3 (15s)

## The Blindness Problem

### **Current Personalization is Limited**

**What agents have:**
- Digital traces (chats, calendars, files)

**What agents lack:**
- Physical context (where you are, what you're doing, your state)

**Result:** Agents personalize from half the picture

### **Example:**

| Agent sees | Agent doesn't see | Result |
|------------|-------------------|--------|
| Meeting at 4pm | You're in deep focus | Disrupts productive hour |

**Information without context → Wrong action**

---

# SLIDE 5: Research Gap (30s)

## Current Limitations Across Four Dimensions

| Dimension | Current Status | What's Missing |
|-----------|---------------|----------------|
| **Personalization** | Digital-only | Physical-world input |
| **Memory Architectures** | Text-based, symbolic | Entry point for continuous sensing |
| **Egocentric Vision** | Mature technology | Agent integration |
| **Self-Logging** | For human review | Agent memory connection |

### **The Gap:**

No work integrates egocentric perception into agent memory for personalization

[Visual: Gap highlighted in center with four dimensions around it]

---

# SLIDE 6: Research Questions (15s)

## Three Research Questions

**RQ1:** What physical-world information becomes visible through egocentric perception that remains invisible through digital traces alone?

**RQ2:** In what contexts does this information improve personalization vs. introduce noise?

**RQ3:** What design requirements emerge for integrating continuous sensing into agent memory?

---

# SLIDE 7: Approach (15s)

## Exploratory + Autoethnographic

### **Not Assuming—Discovering**

- **NOT:** Proving physical context helps
- **BUT:** Discovering where it helps and where it doesn't

### **Autoethnographic Self-Study**

- 2 weeks continuous capture
- Design Science Research (artifact + empirical findings)
- Validated methodology (Neustaedter & Sengers, 2012)

---

# SLIDE 8: Design Decisions - Part 1 (20s)

## Why Egocentric Vision?

### **Three Reasons:**

**1. Mobility**
- Egocentric device moves with wearer
- Continuous capture across locations
- Reinforced by new hardware trend: consumer smart glasses going viral

**2. First-Person Perspective**
- Matches user attention
- Captures what user sees and interacts with

**3. Privacy-Utility Balance**
- On-device filtering possible
- Face obfuscation, text redaction
- No cloud dependency

**Alternatives Considered:** Ambient sensors ❌, Third-person cameras ❌, Smartphone logs ❌

---

# SLIDE 9: Design Decisions - Part 2 (20s)

## Why OpenCLAW?

### **Three Reasons:**

**1. Production-Grade Foundation**
- Real-world constraints (battery, storage, latency)
- Not a toy system
- Proven deployment

**2. Transparent Memory**
- Plain markdown files
- Fully inspectable
- Simple to extend

**3. Markdown Alignment**
- VLM text → Markdown memory
- No representation conversion
- Natural pipeline

**Alternatives Considered:** MemGPT ❌ (closed-source), Memoria ❌ (knowledge graph), scratch ❌ (reinventing)

---

# SLIDE 10: System Architecture (45s)

## Three-Layer Architecture

```
┌─────────────────────────────────────┐
│   LAYER 1: PHYSICAL INPUT           │
│   • Egocentric capture (iOS app)    │
│   • Privacy filtering (on-device)   │
│   • Sensor selection                │
└──────────────┬──────────────────────┘
               ↓
┌─────────────────────────────────────┐
│   LAYER 2: PROCESSING               │
│   • VLM extraction (video → text)   │
│   • Activity recognition            │
│   • Semantic summarization          │
└──────────────┬──────────────────────┘
               ↓
┌─────────────────────────────────────┐
│   LAYER 3: MEMORY EXTENSION         │
│   • OpenCLAW integration            │
│   • Markdown format                 │
│   • Cross-modal indexing            │
└─────────────────────────────────────┘
```

### **Key Innovation:**

Physical-world → Text summary → Markdown memory

[Visual: Animated flow diagram showing data flow through layers]

---

# SLIDE 11: Methodology (30s)

## Autoethnographic Self-Study

### **Duration:** 2 weeks continuous capture

### **Data Sources:**

- Egocentric video (continuous)
- Agent interaction logs
- Daily reflections

### **Analysis:**

- What physical info was captured?
- When was it queried by agent?
- Did it help or hurt personalization?

### **Validity Strategies:**

- Transparency of process
- Depth over breadth
- Theoretical grounding (DSR)

---

# SLIDE 12: Expected Contributions (30s)

## [Midterm: Expected Contributions]
## [Final: Contributions]

### **1. Empirical Findings**
- Where physical context aids personalization
- Where it introduces noise
- Design patterns for effective use

### **2. System Artifact**
- Egocentric vision + OpenCLAW integration
- Privacy-preserving capture pipeline
- Open-source implementation

### **3. Design Implications**
- Storage granularity (text vs. key frames)
- Privacy trade-offs (retention policies)
- Abstraction mechanisms (real-time vs. nightly)

---

# SLIDE 13: Timeline & Progress (15s)

## [Midterm Version]

| Phase | Status |
|-------|--------|
| Introduction & Related Work | ✅ Complete |
| Design Rationale | ✅ Complete |
| Methodology | ✅ Complete |
| System Implementation | 🔄 In Progress |
| 2-Week Experiment | ⏳ Planned (Mar 18-31) |
| Analysis & Writing | ⏳ Planned (Apr 1-7) |

**Defense:** March 23, 2026

---

## [Final Version - For Final Defense]

| Phase | Status |
|-------|--------|
| Introduction & Related Work | ✅ Complete |
| Design Rationale | ✅ Complete |
| Methodology | ✅ Complete |
| System Implementation | ✅ Complete |
| 2-Week Experiment | ✅ Complete |
| Analysis & Writing | ✅ Complete |

**Defense:** March 23, 2026

---

# SLIDE 14: Summary & Questions (15s)

## Summary

- **Problem:** Personal AI agents limited to digital traces
- **Solution:** Physical-world observation for better personalization
- **Method:** Exploratory study + system artifact
- **Goal:** Discover where physical context helps

---

## [Midterm: Open Questions]

- Implementation challenges?
- Experimental design feedback?
- Expected contribution validation?

---

## [Final: Conclusions + Future Work]

### **Key Findings:**
- Physical context helps in X scenarios
- Noise introduced in Y scenarios
- Key insight: Z

### **Future Work:**
- Multi-user validation
- Advanced sensing modalities
- Long-term deployment studies

---

# THANK YOU

## Questions?

**Contact:** chriswu@cmu.edu

**Code:** [Will be open-sourced after defense]

---

# APPENDIX SLIDES (If Needed)

## A1: Related Work Summary

### **Personalization for Agents**
- PLLM: Model-level adaptation
- PRIME: Dual-memory system
- Mem0/Memoria: Persistent memory

**Gap:** All use digital traces only

### **Egocentric Vision**
- Ego4D, Ego-Exo4D: Large benchmarks
- VideoAgent, Vinci: Video understanding

**Gap:** Not connected to agent systems

---

## A2: Technical Details - VLM Pipeline

### **Video → Text Extraction**

**Input:** Egocentric video clip (30-60 seconds)

**Processing:**
1. Frame sampling (1 fps)
2. VLM analysis (GPT-4V / Claude Vision)
3. Structured extraction:
   - Activity: "Working at desk"
   - Location: "Home office"
   - Objects: "Laptop, coffee cup, notebook"
   - State: "Focused, typing"

**Output:** Text summary + metadata

**Latency:** ~5 seconds per clip (on-device optimization possible)

---

## A3: Privacy Architecture

### **On-Device Filtering**

**Before storage:**
- Face detection → Blur all non-user faces
- Text detection → Redact sensitive text (emails, passwords)
- Audio → Transcribe only, discard audio

**User Control:**
- Start/stop capture anytime
- Delete specific time ranges
- Review before agent access

**Retention:**
- 14-day default
- User-configurable
- Automatic cleanup

---

## A4: Evaluation Metrics

### **How to Measure Success**

**RQ1 (What's captured):**
- Unique information types
- Coverage over time
- Comparison with digital traces

**RQ2 (Help vs. Hurt):**
- Query success rate
- Self-reported helpfulness (daily journals)
- System metrics (retrieval accuracy)

**RQ3 (Design requirements):**
- Privacy satisfaction
- System usability
- Integration overhead

---

# BACKUP SLIDES (For Q&A)

## B1: Why 2 Weeks Not 1 Week?

**Reasons:**
- Capture weekend + weekday patterns
- Enough data for pattern discovery
- Manageable analysis scope

**Extensible:** Can extend if needed

---

## B2: Comparison with Other Approaches

| Approach | Pros | Cons |
|----------|------|------|
| **User Study (n=10)** | Generalizable | Short-term only, surface-level |
| **Deployment Study** | Real usage | Logistics, privacy hard |
| **Autoethnographic** | Deep, longitudinal | n=1, transferability questions |
| **This Thesis** | Deep + longitudinal | Exploratory (not proving) |

---

## B3: What If Physical Context Doesn't Help?

**Valid Finding!**

- Exploratory approach: discovering value, not proving it
- Negative results still valuable:
  - "Physical context didn't help for X"
  - "Privacy concerns outweigh benefits for Y"
- Shows where NOT to invest engineering effort

**Publication strategy:**
- If helps: "Physical context improves X"
- If doesn't: "Why physical context failed for personalization"

Both are contributions.

---

## B4: Technical Risks

### **Battery Consumption**
- **Risk:** Continuous capture drains battery
- **Mitigation:** Adaptive sampling, low-power mode

### **Storage**
- **Risk:** 2 weeks = lots of video
- **Mitigation:** Text summaries only, discard video after processing

### **VLM Accuracy**
- **Risk:** Misinterpretation of activities
- **Mitigation:** Human review during self-study, confidence thresholds

### **Privacy Leaks**
- **Risk:** Capturing sensitive info
- **Mitigation:** On-device filtering, user control

---

**END OF SLIDES**

---

# Slide Preparation Notes

## Visual Design Tips

1. **Use high-quality images**
   - OpenCLAW screenshot
   - Egocentric vision example
   - Architecture diagram

2. **Keep text minimal**
   - ≤6 bullets per slide
   - 20-30 words per bullet max
   - Font size ≥24pt

3. **Color scheme**
   - Primary: CMU red (#C41E3A)
   - Secondary: Dark gray (#333333)
   - Background: White or light gray

4. **Animation**
   - Build points one at a time
   - Keep animations simple
   - Use for architecture flow only

## Timing Reminders

- **Slide 2-4 (Motivation):** 45s total, don't rush
- **Slide 10 (Architecture):** 45s, this is key slide
- **Slide 14 (Summary):** Leave 2min for Q&A transition

## Practice Schedule

- **Day 1:** Read through all slides, time yourself
- **Day 2:** Practice with notes
- **Day 3:** Practice without notes
- **Day 4:** Full run-through with timer
- **Day 5:** Final practice, polish delivery

---

**Total Preparation Time:** 3-5 hours
**Recommended Practice:** 5+ full run-throughs
