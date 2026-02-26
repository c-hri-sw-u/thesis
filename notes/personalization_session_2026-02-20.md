# Personalization Research - Session Notes

## Date
2026-02-20

## Discussion Topic
Chris expressed strong interest in AI agent personalization, viewing it as the "下半场" (second half) of AI development.

## Key Insight from Chris
"AI的下半场，是个性化和个人化。只有AI agent/assistant真正了解你这个人，了解你的习惯，了解你的目标，了解你的性格，才能最好地帮助你。这是我使用 openclaw得到的启示"

Translation: "The second half of AI is personalization. Only when AI agents truly understand you - your habits, goals, personality - can they best help you. This is what I learned from using OpenClaw."

## Three Research Directions Discussed

### 1. Technical: Memory + Pattern Detection
**Question:** How to implement memory systems and detect user patterns?

**Key Papers:**
- MemGPT (2023) - Hierarchical memory architecture
- Mem0 (2024) - Production-ready memory with auto-updating
- O-Mem (2025) - Characteristic identification + event recording
- Pattern detection literature (temporal, contextual, RLHF)

**Key Challenges:**
- Memory hierarchy: short/medium/long-term
- Pattern extraction from long-term data
- Contradiction detection and resolution
- Uncertainty quantification

---

### 2. HCI: User Perceptions of Being Understood
**Question:** How do users feel when AI deeply understands them?

**Key Findings:**
- **Creepy threshold:** Personalization becomes creepy when too granular
- **Transparency paradox:** Users want personalization but don't want to know how it works
- **Trust dynamics:** Trust increases over time, but decreases after mistakes
- **Emotional connection:** "Feeling understood" predicts long-term engagement

**Key Challenges:**
- Defining boundaries: what's "too much" personalization?
- Balancing transparency with simplicity
- Building trust after mistakes
- Expressing empathy without being creepy

---

### 3. Theoretical: What Does "Deep Understanding" Mean?
**Question:** What is the theoretical foundation of deep user understanding?

**Key Concepts:**
- **Theory of mind:** Understanding user's beliefs, desires, intentions
- **Shallow vs deep understanding:** Facts vs motivations vs complex interactions
- **Personal identity:** How to handle user changes over time
- **Personalization paradox:** More data ≠ better understanding

**Key Challenges:**
- Measuring "depth" of understanding
- Handling preference drift and identity shifts
- Detecting and resolving contradictions
- Ethical use of deep understanding (power imbalance, manipulation risk)

---

## Connection to Thesis

### RQ3: Agent Integration
This lit review directly informs RQ3 on how to integrate memories into agents.

**Approach:**
1. **Memory Architecture:** Adapt MemGPT/Mem0 for multimodal data
2. **Pattern Detection:** Temporal + contextual pattern learning
3. **Personalized Prompting:** Inject relevant memories
4. **Contradiction Handling:** Detect and resolve
5. **Uncertainty Quantification:** Explicit confidence

---

### RQ4: User Acceptance
This lit review directly informs RQ4 on user perceptions.

**Study Design:**
1. **Longitudinal:** 2-4 weeks (longer than most studies)
2. **Emotional tracking:** Detect and respond to emotions
3. **Boundary exploration:** Test "creepy threshold"
4. **Trust measurement:** Track trust over time

---

## Research Gaps Identified

### Technical
1. Multimodal memory systems (most are text-based)
2. Long-term pattern detection (most focus on short-term)
3. Contradiction resolution (no systematic approach)
4. Uncertainty quantification (most pretend certainty)

### HCI
1. Long-term relationships (most studies are short)
2. Emotional understanding (focus on functional preferences)
3. Boundary definition (no systematic "creepy" threshold)

### Theoretical
1. Metrics for "deep understanding" (no clear metrics)
2. Identity & continuity (no framework for user changes)
3. Ethical guardrails (no systematic ethical approach)

---

## Next Steps

### Immediate (This Week)
1. **Deep dive into key papers:**
   - Read O-Mem paper (2025) - characteristic identification
   - Read MemGPT paper - hierarchical memory
   - Read O-Mem code if available

2. **Design memory architecture:**
   - Define memory hierarchy (short/medium/long-term)
   - Define data schema (what to store?)
   - Define update mechanisms (when to update?)

3. **Design pattern detection:**
   - Define patterns to detect (temporal, contextual, emotional)
   - Define detection methods (time-series, clustering, anomaly detection)

### Medium (Next 2 Weeks)
4. **Implement prototype:**
   - Memory system prototype (vector DB + metadata)
   - Pattern detection prototype (on simulated data)
   - Agent integration prototype (inject memories into prompts)

5. **User study design:**
   - Define "creepy threshold" experiment
   - Define trust measurement protocol
   - Define emotional response evaluation

---

## Questions for Chris

1. **Which direction is most interesting?**
   - Technical: Implementing memory + pattern detection?
   - HCI: Understanding user perceptions?
   - Theoretical: Defining "deep understanding"?

2. **Specific personalization scenarios:**
   - What personalization would you find most useful?
   - What personalization would you find creepy?
   - Are there scenarios where you'd want the agent to be proactive?

3. **Thesis RQ refinement:**
   - Should we narrow RQ3 to focus on "deep understanding"?
   - Should RQ4 specifically test "emotional connection" and trust?
   - Are there other RQs we should add?

---

*Session date: 2026-02-20*
*Status: Lit review complete, ready for next phase*
