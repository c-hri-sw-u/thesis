---

## 📊 Reuse Strategy: Midterm → Final

| Slide | Midterm | Final | Change |
|-------|---------|-------|--------|
| 1 | Title | Title | None |
| 2-4 | Motivation (3 slides) | Same | None |
| 5-6 | Gap + RQs | Same | None |
| 7 | Approach | Same | None |
| 8-9 | Design Decisions | Same | None |
| 10 | Architecture | Same | None |
| 11 | Methodology | Same | None |
| 12 | **Expected** Contributions | Contributions | Remove "Expected" |
| 13 | Timeline (in progress) | Timeline (complete) | Change 🔄→✅ |
| 14 | Open Questions | Conclusions + Future Work | Change content |

**Reuse rate:** 11/14 slides = 79%

---

## ⏱️ Timing Breakdown

| Section | Slides | Time | Purpose |
|---------|--------|------|---------|
| Title | 1 | 0.5min | Introduction |
| Motivation | 3 | 1min | Why this matters |
| Gap + RQs | 2 | 1min | What + Why now |
| Approach | 1 | 0.5min | How |
| Design | 2 | 1min | Technical decisions |
| Architecture | 1 | 1min | System overview |
| Methodology | 1 | 0.5min | Validity |
| Contributions | 1 | 0.5min | Impact |
| Timeline | 1 | 0.5min | Status |
| Summary + Q&A | 1 | 2min | Wrap up |
| **Total** | **14** | **8-9min** | **+ 7min Q&A = 15-16min** |

---

## 🎤 Oral Scripts

### Slide 2: Personal AI Agents Are Here (15s)

```
Personal AI agents aren't research demos anymore—they're real 
systems in production. OpenCLAW, Letta, PAI—these are deployed, 
used, and running continuously. This is happening now.
```

### Slide 3: Why Personalization Matters (15s)

```
And personalization is what makes them effective. A generic agent 
treats everyone the same. A personalized agent adapts to your 
preferences, learns what works, avoids what doesn't. Personalization 
is the key differentiator between a tool and an assistant.
```

### Slide 4: The Blindness Problem (15s)

```
But current personalization is limited. Agents build user models 
from digital traces—chats, calendars, files—while staying blind 
to the physical world. Your location, your activity, your focus 
state. An agent sees a meeting on your calendar, but doesn't know 
you're in deep focus—and disrupts your most productive hour.

That's the blindness I'm trying to fix.
```

### Slide 5: Research Gap (30s)

```
[15s] Let me show you the gap across four dimensions. Current 
personalization is digital-only—chats, files, calendars. Memory 
architectures are text-based with no entry point for continuous 
sensing. Egocentric vision technology is mature, but not connected 
to agents. And self-logging captures data for humans, not agents.

[15s] The gap is clear: no work integrates egocentric perception 
into agent memory for personalization. That's where this thesis 
comes in.
```

### Slide 6: Research Questions (15s)

```
I ask three questions. First, what physical-world information 
becomes visible through egocentric perception that digital traces 
miss? Second, where does this information help personalization 
and where does it hurt? And third, what design requirements 
emerge for memory integration?
```

### Slide 7: Approach (15s)

```
I take an exploratory approach. I'm not assuming physical context 
helps—I'm discovering where it helps and where it doesn't. I use 
autoethnographic self-study: 7 days of continuous capture, building 
a system artifact, analyzing empirical findings. This is validated 
methodology for systems research.
```

### Slide 8-9: Design Decisions (40s)

```
[20s] Two key design decisions. First, why egocentric vision? 
Three reasons: it matches user attention with first-person 
perspective, the technology is mature with working VLMs, and 
privacy-utility can be balanced with on-device filtering.

[20s] Second, why OpenCLAW? Again three reasons: it's 
production-grade so I work with real constraints, memory is 
transparent markdown files I can inspect, and VLM text outputs 
align naturally with markdown memory. No representation conversion 
needed.
```

### Slide 10: Architecture (45s)

```
[15s] The system has three layers. Physical Input captures 
egocentric video with privacy filtering on iOS. Processing uses 
VLMs to extract activities and generate text summaries. Memory 
Extension integrates these summaries into OpenCLAW's markdown 
format with cross-modal indexing.

[15s] [Point to diagram] The key innovation is this pipeline: 
physical-world video goes in, VLM produces text summaries, text 
becomes markdown memory. No complex sensor fusion, no new 
representation languages—just text that agents already understand.

[15s] This design is intentional: I want to discover whether 
simple text summaries capture enough physical context for 
personalization, or if richer representations are needed.
```

### Slide 11: Methodology (30s)

```
[15s] I run a 7-day autoethnographic self-study. Data sources: 
egocentric video, agent interaction logs, daily reflections. 
I analyze what physical info was captured, when the agent 
queried it, and whether it helped or hurt.

[15s] Validity comes from transparency, depth over breadth, 
and theoretical grounding in Design Science Research. This 
isn't proving a hypothesis—it's discovering patterns.
```

### Slide 12: Expected Contributions (30s)

```
[15s] I expect three contributions. Empirical findings showing 
where physical context helps—like activity-aware scheduling—and 
where it doesn't—like email drafting.

[15s] A system artifact that integrates egocentric vision with 
OpenCLAW, with privacy-preserving capture. And design implications: 
how granular should storage be, how to handle retention, what 
abstraction mechanisms work.
```

### Slide 13: Timeline (15s)

```
[Midterm] Introduction, Related Work, Design Rationale, and 
Methodology are complete. System implementation is in progress. 
The 7-day experiment runs March 20-26, with analysis and writing 
the following week. Defense is March 23rd.
```

### Slide 14: Summary & Questions (15s)

```
[Midterm] To summarize: Personal AI agents are blind to the 
physical world. This thesis explores whether egocentric vision 
can bridge that gap, through exploratory study and system 
artifact. I'm happy to take questions on implementation 
challenges, experimental design, or expected contributions.
```

---

## 💡 Q&A Preparation

### Expected Questions

**Q1: Why autoethnographic instead of user study?**

A:
- Longitudinal deployment (7+ days) impractical with external participants
- Deep system understanding requires insider access to debug and iterate
- Validated methodology for systems research (Neustaedter & Sengers, 2012)
- Future work: multi-user validation

**Q2: How do you measure personalization improvement?**

A:
- Query success rate: Did agent find relevant physical context?
- Self-reflection: Daily journals on helpfulness
- System metrics: Retrieval accuracy, response relevance
- Not proving improvement, discovering patterns

**Q3: What about privacy?**

A:
- On-device filtering (faces, text redaction)
- 14-day retention policy
- User control over capture (start/stop)
- This is part of RQ3 (design requirements)

**Q4: What if physical context doesn't help?**

A:
- That's a valid finding! Exploratory approach means discovering value, not proving it
- Negative results still valuable: "Physical context didn't help for X"
- Shows where NOT to invest engineering effort

**Q5: Why 7 days? Is that enough?**

A:
- Balance between longitudinal data and feasibility
- Enough to capture diverse scenarios (work, home, weekend)
- Consistent with autoethnographic literature (Neustaedter & Sengers)
- Can extend if needed

**Q6: How is this different from existing lifelogging?**

A:
- Lifelogging captures for human review
- This captures for agent memory
- Key difference: agent autonomously uses the data, not human browsing

**Q7: What's the technical contribution vs. empirical?**

A:
- Technical: Integration pipeline, memory format design
- Empirical: Where physical context helps/hurts
- Both contributions, but exploratory focus

---

## 📋 Checklist Before Presentation

### Day Before
- [ ] Test slides on presentation laptop
- [ ] Practice full run-through with timer
- [ ] Prepare backup PDF version
- [ ] Review Q&A answers

### 30 Min Before
- [ ] Arrive early, test AV
- [ ] Load slides, check formatting
- [ ] Have water ready
- [ ] Review opening lines

### During Presentation
- [ ] Start with confidence
- [ ] Make eye contact
- [ ] Don't rush—pause after key points
- [ ] Point to visuals on architecture slide
- [ ] End on time, leave room for Q&A

---

**Status:** Ready for midterm defense
**Reuse potential:** 79% slides reusable for final
**Preparation time:** 2-3 hours practice recommended
