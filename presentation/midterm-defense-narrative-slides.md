# Thesis Midterm Defense - Narrative Slides

**Created with:** /narrative-slides skill
**Duration:** 8-9 minutes + Q&A
**Slides:** 14 slides

---

## SLIDE 1: Title

# Physical-World Observation for Personal AI Agent Personalization

**Chris Wu**
Carnegie Mellon University
March 2026

**VISUAL:** 
- Clean title slide
- CMU logo
- Thesis title in large font

---

## SLIDE 2: Opening

# Personal AI Agents Are Here

**Deployed. Persistent. Real.**

---

**SPEAKER CUE:**
"Personal AI agents aren't research demos anymore. OpenCLAW, Letta, PAI—these are production systems running continuously, assisting real users in real workflows. This is happening now."

**VISUAL:**
- Logos of 3 systems
- "Production" badge
- Timeline: "2023-2026: From demos to deployment"

---

## SLIDE 3: Tension Point

# But They're Blind

**Personalization = Digital Traces Only**

- Chats
- Calendars  
- Files

**VISUAL:**
- Icon of agent with blindfold
- Digital trace icons on left side
- Empty right side (physical world missing)

---

**SPEAKER CUE:**
"These agents personalize based only on what you type and schedule. Your chats, your calendar, your files. They know your digital life—but nothing about where you are, what you're doing, or what you see."

---

## SLIDE 4: Concrete Example

# When Blindness Breaks Trust

**Example: 3pm Focus Work**

---

**Agent sees:**
- Meeting at 4pm

**Agent doesn't see:**
- Deep focus state
- No break in 3 hours

**Agent action:**
- Sends recommendation

**Result:**
- ❌ Disrupts most productive hour

---

**SPEAKER CUE:**
"Here's what happens. Agent sees a meeting on your calendar. What it doesn't see: you've been in deep focus for three hours. So it sends a non-urgent message and breaks your flow. It had information—but not context."

**VISUAL:**
- Timeline showing 3pm
- Agent notification popup
- User expression: frustrated

---

## SLIDE 5: Research Gap

# The Missing Piece

---

**Current State:**

| Dimension | Status |
|-----------|--------|
| Personalization | Digital-only ✅ |
| Memory Architectures | Text-based ✅ |
| Egocentric Vision | Mature tech ✅ |
| Self-Logging | Human review ✅ |

---

**But No One Has Connected Them**

**VISUAL:**
- Four islands (personalization, memory, ego-vision, self-logging)
- No bridges between them
- Gap in center

---

**SPEAKER CUE:**
"We have four mature pieces: personalization systems, memory architectures, egocentric vision technology, and self-logging methods. Each works well alone. But no one has connected them—no work integrates egocentric perception into agent memory for personalization. That's the gap."

---

## SLIDE 6: Research Questions

# What I'm Exploring

---

**RQ1:** What physical-world information becomes visible that digital traces miss?

**RQ2:** When does it help vs. hurt personalization?

**RQ3:** What design requirements emerge?

---

**SPEAKER CUE:**
"I ask three questions. First, what physical information can we actually capture that agents don't currently see? Second, where does that information help personalization, and where does it introduce noise? And third, what do we learn about designing these systems?"

**VISUAL:**
- Three questions stacked
- Icons for each (eye, scale, gears)

---

## SLIDE 7: Approach

# Not Proving—Discovering

---

**Exploratory Autoethnography**

- 2-week self-study
- Continuous egocentric capture
- Agent interaction logs
- Daily reflections

---

**SPEAKER CUE:**
"I take an exploratory approach. I'm not assuming physical context helps—I'm discovering where it does and doesn't. I use autoethnographic self-study: two weeks of continuous capture, analyzing my own experience. This is validated methodology for systems research."

**VISUAL:**
- Timeline: 2 weeks
- Data sources icons (camera, logs, journal)
- "Exploratory" badge

---

## SLIDE 8: Design Decision 1

# Why Egocentric Vision?

---

**Three Reasons:**

1. **Mobility**
   - Moves with wearer
   - Continuous capture anywhere

2. **First-Person Perspective**
   - Matches user attention
   - What user sees and does

3. **Privacy-Utility Balance**
   - On-device filtering
   - No cloud dependency

---

**SPEAKER CUE:**
"Why egocentric vision? Three reasons. First, mobility—it captures continuously across locations. Second, first-person perspective—it matches what you actually attend to. Third, privacy—we can filter on-device without cloud. No other modality gives us all three."

**VISUAL:**
- Smart glasses icon
- 3-column comparison vs alternatives (ambient ❌, third-person ❌, logs ❌)

---

## SLIDE 9: Design Decision 2

# Why OpenCLAW?

---

**Three Reasons:**

1. **Production-Grade**
   - Real constraints
   - Not a toy system

2. **Transparent Memory**
   - Plain markdown
   - Fully inspectable

3. **Markdown Alignment**
   - VLM → Text → Markdown
   - No conversion

---

**SPEAKER CUE:**
"Why OpenCLAW? Again three reasons. It's production-grade, so I work with real constraints. Memory is transparent markdown I can inspect. And the pipeline is simple: VLM outputs text, OpenCLAW stores text—no representation gymnastics."

**VISUAL:**
- OpenCLAW logo
- Markdown file icon
- Simple flow: "Video → Text → Markdown"

---

## SLIDE 10: Architecture (KEY SLIDE)

# System Architecture

**Three Layers, One Pipeline**

---

```
[CAPTURE] → [PROCESS] → [MEMORY]
   ↓            ↓           ↓
 Video      VLM → Text   Markdown
```

---

**LAYER 1: Capture**
- Egocentric video
- Privacy filtering (on-device)
- Sensor selection

**LAYER 2: Process**
- VLM extraction
- Activity recognition
- Text summarization

**LAYER 3: Memory**
- OpenCLAW integration
- Markdown storage
- Cross-modal indexing

---

**SPEAKER CUE:**
"Here's how it works. Capture layer records video with privacy filtering. Processing layer uses VLMs to extract activities and generate text summaries. Memory layer stores these as markdown in OpenCLAW. The key innovation: physical world becomes text that agents can already work with."

**VISUAL:**
- Animated flow diagram
- Show data moving through layers
- Color code each layer

**ANIMATION SUGGESTION:**
- Build layers one at a time
- Show data flow with arrows
- Final state: complete pipeline

---

## SLIDE 11: Methodology

# How I'll Answer

---

**Autoethnographic Self-Study**

**Duration:** 2 weeks

**Data:**
- Egocentric video
- Agent interaction logs
- Daily reflections

**Analysis:**
- What was captured?
- When was it queried?
- Did it help or hurt?

---

**SPEAKER CUE:**
"I'll run a two-week self-study. I capture egocentric video, log all agent interactions, and keep daily reflections. Then I analyze: what physical info was captured, when did the agent use it, and did that help or hurt personalization?"

**VISUAL:**
- 2-week calendar
- Data source icons
- Question mark → findings flow

---

## SLIDE 12: Contributions

# Expected Contributions

---

**1. Empirical Findings**
- Where physical context aids
- Where it introduces noise
- Design patterns

**2. System Artifact**
- Egocentric + OpenCLAW integration
- Privacy-preserving pipeline
- Open-source

**3. Design Implications**
- Storage granularity
- Privacy trade-offs
- Abstraction mechanisms

---

**SPEAKER CUE:**
"I expect three contributions. First, empirical findings showing where physical context helps and hurts. Second, an open-source system artifact integrating egocentric vision with OpenCLAW. Third, design implications for storage, privacy, and abstraction."

**VISUAL:**
- Three columns
- Icons for each contribution type
- "Open-source" badge

---

## SLIDE 13: Timeline

# [Midterm: Progress & Plan]
# [Final: Completed]

---

**[MIDTERM VERSION]**

| Phase | Status |
|-------|--------|
| Introduction & Related Work | ✅ |
| Design Rationale | ✅ |
| Methodology | ✅ |
| System Implementation | 🔄 |
| 2-Week Experiment | ⏳ Mar 18-31 |
| Analysis & Writing | ⏳ Apr 1-7 |

**Defense:** March 23

---

**[FINAL VERSION]**

| Phase | Status |
|-------|--------|
| Introduction & Related Work | ✅ |
| Design Rationale | ✅ |
| Methodology | ✅ |
| System Implementation | ✅ |
| 2-Week Experiment | ✅ |
| Analysis & Writing | ✅ |

**Defense:** March 23

---

**SPEAKER CUE (Midterm):**
"Currently, introduction, related work, design, and methodology are complete. System implementation is in progress. The two-week experiment runs March 18-31, with analysis the following week. Defense is March 23rd."

**VISUAL:**
- Gantt chart or timeline
- Check marks for completed
- In-progress highlighted

---

## SLIDE 14: Closer

# [Midterm: Summary & Questions]
# [Final: Conclusions & Future]

---

**[MIDTERM VERSION]**

## Summary

- Personal agents limited to digital traces
- Physical-world observation could bridge gap
- Exploratory study to discover value
- System artifact for integration

---

### **Open Questions:**

- Implementation challenges?
- Experimental design feedback?
- Expected contribution validation?

---

**[FINAL VERSION]**

## Conclusions

- Physical context helps [X]
- Introduces noise in [Y]
- Key insight: [Z]

---

### **Future Work:**

- Multi-user validation
- Advanced sensing
- Long-term deployment

---

**SPEAKER CUE (Midterm):**
"To summarize: personal AI agents are blind to the physical world. I'm exploring whether egocentric vision can bridge that gap, through exploratory study and system artifact. I'm happy to take questions on implementation, experimental design, or contributions."

**VISUAL:**
- Simple recap diagram
- Open question mark or "Thank You"
- Contact info

---

# APPENDIX (If Needed)

---

## A1: Related Work Detail

### Personalization

- PLLM Survey (Liu et al., 2025)
- PRIME (Wang et al., 2025)
- Mem0, Memoria (2025)

**Gap:** All digital-only

### Egocentric Vision

- Ego4D, Ego-Exo4D
- VideoAgent, Vinci

**Gap:** Not agent-connected

---

## A2: Technical Details

### VLM Pipeline

**Input:** 30-60 sec video

**Process:**
1. Frame sample (1 fps)
2. VLM analysis
3. Structured extraction:
   - Activity
   - Location
   - Objects
   - State

**Output:** Text + metadata

**Latency:** ~5 sec/clip

---

## A3: Privacy Mechanisms

### On-Device Filtering

**Before Storage:**
- Face detection → Blur
- Text detection → Redact
- Audio → Transcribe only

**User Control:**
- Start/stop anytime
- Delete time ranges
- Review before agent access

**Retention:**
- 14-day default
- User-configurable

---

## A4: Evaluation Metrics

### Measuring Success

**RQ1 (What's captured):**
- Info type coverage
- Uniqueness vs digital

**RQ2 (Help vs Hurt):**
- Query success rate
- Self-reported helpfulness
- Retrieval accuracy

**RQ3 (Design):**
- Privacy satisfaction
- System usability
- Integration overhead

---

# BACKUP (Q&A)

---

## B1: Why 2 Weeks?

**Not 1 week because:**
- Weekend + weekday patterns
- Sufficient for pattern discovery
- Manageable analysis scope

**Can extend if needed**

---

## B2: Why Autoethnographic?

**vs User Study (n=10):**
- Short-term only
- Surface-level data

**vs Deployment:**
- Logistics hard
- Privacy hard

**Autoethnographic:**
- Deep, longitudinal
- Validated methodology
- Exploratory = appropriate

---

## B3: What If It Doesn't Help?

**Valid finding!**

- Exploratory = discovering, not proving
- Negative results valuable:
  - "Physical context didn't help for X"
  - "Privacy concerns outweigh benefits"

**Publication strategy:**
- If helps: "Physical context improves X"
- If doesn't: "Why physical context failed"

Both are contributions.

---

## B4: Technical Risks

| Risk | Mitigation |
|------|-----------|
| Battery drain | Adaptive sampling |
| Storage bloat | Text-only retention |
| VLM errors | Human review, confidence |
| Privacy leaks | On-device filtering |

---

**END OF SLIDES**

---

# Presentation Notes

## Timing Guide

| Slide | Duration | Cumulative |
|-------|----------|------------|
| 1 | 0:30 | 0:30 |
| 2-4 | 0:45 | 1:15 |
| 5 | 0:30 | 1:45 |
| 6 | 0:15 | 2:00 |
| 7 | 0:15 | 2:15 |
| 8-9 | 0:40 | 2:55 |
| 10 | 0:45 | 3:40 |
| 11 | 0:30 | 4:10 |
| 12 | 0:30 | 4:40 |
| 13 | 0:15 | 4:55 |
| 14 | 0:15 | 5:10 |

**Total:** ~5 minutes content
**With pauses:** 8-9 minutes
**Q&A buffer:** 6-7 minutes

## Animation Plan

**Slide 10 (Architecture):**
1. Show Layer 1
2. Show Layer 2 (with arrow)
3. Show Layer 3 (with arrow)
4. Highlight "Physical → Text → Markdown"

**Other slides:** Keep simple, no animation needed

## Visual Checklist

- [ ] OpenCLAW, Letta, PAI logos
- [ ] Agent blindfold icon
- [ ] Timeline with disruption moment
- [ ] Four-island gap diagram
- [ ] Architecture flow diagram
- [ ] 2-week calendar
- [ ] Progress timeline (✅/🔄/⏳)

## Practice Tips

1. **Day 1:** Read all slides aloud, time yourself
2. **Day 2:** Practice with notes
3. **Day 3:** Practice without notes
4. **Day 4:** Full run-through with timer
5. **Day 5:** Polish delivery, practice Q&A

---

**Created:** 2026-03-16
**Skill Used:** /narrative-slides
**Status:** Ready for practice
