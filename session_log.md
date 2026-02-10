# Thesis Session Log

## 2026-02-09 - Initial Planning Session

### Discussion Summary
**Chris's thesis vision:**
- Theme: Vision-based daily life understanding to make agents more knowledgeable about users
- Sensors: Visual (phone camera) + auxiliary (mic, IMU)
- Scope: All-day/24/7 coverage
- Hardware: Existing phone (multimodal, easy to develop)
- Integration: OpenClaw agent system

### Decisions Made
1. **Research direction:** System-oriented (end-to-end) + Privacy-preserving
   - Build complete phone → understanding → memory → agent pipeline
   - Integrate with OpenClaw for real utility
   - Focus on practical challenges (battery, privacy, storage)
   - Secondary focus: On-device privacy pipeline

2. **Scope:** All-day life logging
   - Cover: home, work, commute, social, leisure, exercise, sleep
   - Adaptive recording based on context/activity
   - Privacy-aware (face/text blur, user controls)

3. **Data collection strategy:** Hybrid approach
   - Always-collect: IMU, GPS (low cost)
   - Intermittent: Audio/video periodic or triggered
   - On-demand: Continuous video for specific activities

4. **Hardware:** Phone camera
   - Pros: Multimodal sensors, easy development,随身携带
   - Challenges: Background limits, battery, storage, privacy

5. **Success metrics:**
   - System: Battery < 30%/day, Storage < 2GB/day, Latency < 1s, Accuracy > 75% F1
   - Privacy: Face obfuscation > 95%, Text > 90%, Overhead < 10% CPU
   - Agent: Task completion +20-30%, Retrieval > 80%, Satisfaction > 4.0/5.0
   - User: Willingness > 70%, Privacy concern < 2.5/5.0

### Workspace Created
```
thesis/
├── research_problem.md    # Research problem & contribution
├── milestones/plan.md     # 20-week roadmap
├── notes/
│   ├── initial_ideas.md   # Initial brainstorming
│   ├── hardware.md        # Phone-based implementation
│   ├── all_day_scope.md   # All-day coverage analysis
│   └── directions_comparison.md # Direction comparison
├── papers/
│   ├── lit_review_plan.md # Literature review strategy
│   ├── lit_review_plan_updated.md # Updated with privacy focus
│   └── collected.md       # Initial paper list
├── drafts/
│   └── proposal.md        # Full proposal outline
├── session_log.md         # Session records
└── session_summary_2026-02-09.md # Summary
```

### Literature Review Plan (Updated)
**8 categories:**
1. Egocentric vision & activity recognition (baseline models)
2. Multimodal wearable systems (system design)
3. Memory systems for AI agents (memory architecture)
4. Personalized AI assistants (agent integration)
5. **Privacy-preserving wearables** (NEW - secondary focus)
6. Systems & practical challenges (deployment)
7. HCI & user studies (evaluation)
8. Related work (quantified self, lifelogging)

**Key datasets:**
- Ego4D
- EPIC-KITCHENS
- EgoExo4D
- HD-EPIC

**Key systems:**
- MemGPT, Mem0
- Friend AI, Plaud.ai
- SenseCam

**Privacy techniques:**
- Face/text obfuscation
- Voice anonymization
- Location obfuscation
- On-device ML

### Next Steps
1. **Week 1-2:** Intensive paper collection (30-50 papers)
   - Focus: System-oriented + Privacy papers
2. **Week 3:** Summarize key papers
3. **Week 4:** Synthesis → Identify gaps → Position work
4. **Week 5-8:** System design (architecture, modules, integration)

### Research Questions
- **RQ1:** How to design end-to-end pipeline for efficient life logging?
- **RQ2:** How to protect privacy while maintaining utility?
- **RQ3:** How to integrate memories into agents?
- **RQ4:** How do users perceive continuous life logging?

### Questions Still Open
- **Data collection specifics:** Exact intervals, triggers, privacy settings
- **Evaluation:** How many participants? What specific tasks?
- **Technical choices:** Which models? Cloud vs on-device?

---

*Session date: 2026-02-09*
*Duration: ~40 minutes*
*Status: ✅ Direction confirmed, ready for literature review*
