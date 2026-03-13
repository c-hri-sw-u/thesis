# Thesis Writing Style Guide

**Created:** 2026-03-13
**Based on:** Introduction v6 + Related Works v4
**Purpose:** Guide future thesis writing (Methods, System, Evaluation, Discussion)

---

## 🎯 Core Principle

**Academic writing is NOT about demonstrating knowledge.**

**It's about:**
1. **Creating urgency** - Why this problem matters NOW
2. **Revealing limitations** - What's missing in current work
3. **Positioning contribution** - How this thesis fills the gap

**Every sentence should have a purpose. Delete filler.**

---

## 📚 Document Structure Patterns

### **Pattern A: Introduction (Problem → Approach)**

```
Paragraph 1: Define + Problem
- Define key term ("what this thesis terms personal AI agent")
- Immediately state problem (blindness to physical world)
- Concrete example (focus work interruption)

Paragraph 2: Approach + Questions
- Methodology (exploratory, autoethnographic)
- Research questions (RQ1, RQ2, RQ3)

Paragraph 3: Contributions
- Explicit numbered list (1, 2, 3...)
```

**Example from Introduction v6:**

```markdown
A growing class of AI system—what this thesis terms the personal AI 
agent—is designed for long-term, personalized, diverse-scenario 
assistance to individual users. Unlike task-bounded agents that 
terminate after a workflow, personal AI agents maintain a persistent 
relationship with a single user across domains, adapting over weeks 
and months. As these agents move from demonstrations to persistent 
deployment, personalization becomes critical... But current personal 
AI agents build these models entirely from digital traces... while 
remaining blind to the physical world...
```

**Key techniques:**
- ✅ Define term immediately
- ✅ Contrast with existing (task-bounded vs persistent)
- ✅ "But" transition to problem
- ✅ No "In this paper, we will..." (waste of space)

---

### **Pattern B: Related Work (Urgency → Limitation → Gap)**

```
Opening Principle:
"Related Work enriches the problem, not demonstrates knowledge."

Every section follows:
1. History/Status (What exists)
2. BUT (What's missing)
3. Bridge (Why this matters)

Structure:
- 2.1: Define space → Pressure point
- 2.2: Current approaches → BUT digital-only
- 2.3: Architecture analysis → BUT no entry point
- 2.4: Technology exists → BUT wrong objectives
- 2.5: Long tradition → BUT never connected to agents
- 2.6: Synthesize gaps → This thesis bridges
```

**Example from Related Works v4:**

```markdown
### 2.2 Personalization for personal AI Agents

Personalization—adapting a system to increase its personal relevance—
has been a persistent challenge throughout the evolution of AI systems.

At the model level, researchers have explored how to modify an LLM's 
outputs to reflect individual preferences (Liu et al., 2025; Qiu et al., 
2025), establishing that user-specific adaptation significantly improves 
task performance. At the agent level, personalization becomes a design 
problem spanning an agent's entire pipeline (Xu et al., 2026)... Memory 
has received particular attention as the architectural foundation for 
this richer knowledge (Mem0, 2025; Memoria, 2025; Westhäußer et al., 2025).

Yet whether personalization operates at the model level or the system 
level, the data source remains the same: digital traces. Personalized 
prompts draw on chat histories; memory systems extract facts from 
conversations; user profiles aggregate patterns from tool usage... No 
current approach captures the physical world...
```

**Key techniques:**
- ✅ Dense citations (multiple per statement)
- ✅ "Yet" transition to BUT
- ✅ Don't explain each paper's details
- ✅ Group by topic, not by paper

---

## ✍️ Sentence-Level Techniques

### **1. Use "BUT" Strategically (Not Every Paragraph)**

**✅ Good usage:**
```
Related Works:
- 2.2: "Yet whether personalization operates at model or system level, 
  the data source remains the same..."
- 2.3: "But its ingestion interface contains no entry point..."
- 2.4: "But this work pursues two objectives, neither of which is 
  personalization."

Total: 3 BUTs in 5 sections (strategic)
```

**❌ Bad usage (too many):**
```
BUT current systems don't... BUT they also lack... BUT we don't know...
```

**Rule:**
- Use BUT only when revealing **critical limitations**
- Not every paragraph needs BUT
- Use alternatives: "Yet", "However", "This creates..."

---

### **2. Citation Density**

**✅ Good (dense but readable):**
```
Recent systems—spanning scalable memory extraction (Mem0 (Chhikara et al., 
2025)), knowledge-graph-based user modeling (Memoria (Sarin et al., 2025)), 
and evolving user profiles (Enabling Personalized Long-term Interactions 
(Westhäußer et al., 2025))—demonstrate that persistent memory improves...
```

**Pattern:**
```
Topic — (Paper1 (Author, Year)), (Paper2 (Author, Year)), and (Paper3 
(Author, Year)) — demonstrate/show/establish that...
```

**❌ Bad (sparse, explaining each paper):**
```
Mem0 (He et al., 2024) achieves 91% lower latency through graph-based 
memory representation. Memoria (Sarin et al., 2025) organizes experiences 
hierarchically across multiple time scales. These systems show...
```

**Rule:**
- **2-5 citations per key statement**
- Don't explain each paper's methods
- Group by topic, not chronologically
- Use em-dashes for dense lists

---

### **3. Concrete Examples**

**✅ Good (specific, relatable):**
```
For instance, when an agent proactively sends a non-urgent recommendation 
based on your manually-set schedule, it doesn't know you're in deep focus 
work, disrupting your most productive hour.
```

**Why it works:**
- Specific scenario (sending recommendation)
- Specific failure mode (disrupting focus work)
- Reader can imagine themselves in the situation

**❌ Bad (abstract, generic):**
```
Current systems have limitations in understanding user context, which 
can lead to suboptimal performance in personalization tasks.
```

**Rule:**
- Always use **specific examples** from daily life
- Not "user context" → "deep focus work at 3pm"
- Not "suboptimal performance" → "disrupts productive hour"

---

### **4. Transitions**

**✅ Good transitions:**
```
Introduction:
"As these agents move from demonstrations to persistent deployment, 
personalization becomes critical... But current personal AI agents build 
these models entirely from digital traces..."

Related Works:
"As these agents move to persistent deployment, the pressure on 
personalization intensifies—an agent that runs continuously must infer 
what the user needs..."

"Yet whether personalization operates at the model level or the system 
level, the data source remains the same..."
```

**Pattern:**
- **As X → Y** (temporal evolution)
- **Yet/But** (reveal limitation)
- **This creates/exposes/reveals** (connect to problem)

**❌ Bad transitions:**
```
"In this section, we discuss..." (waste of space)
"Next, we will examine..." (filler)
"Several approaches have been proposed..." (passive, weak)
```

---

## 🚫 What to AVOID

### **1. Definition-First Openings**

**❌ Bad:**
```
Personal AI agents are defined as systems that provide long-term 
assistance to individual users. They have several characteristics: 
persistent memory, adaptation, and context-awareness...
```

**✅ Good:**
```
A growing class of AI system—what this thesis terms personal AI agent—is 
designed for long-term, personalized assistance to individual users. As 
these agents move from demonstrations to deployment, personalization 
becomes critical...
```

**Difference:**
- Bad: Definition → Description (boring)
- Good: Definition → Urgency (engaging)

---

### **2. Literature Summaries**

**❌ Bad:**
```
Wang et al. (2023) proposed a system for X. Zhang et al. (2024) improved 
on this by doing Y. Liu et al. (2025) extended the framework to Z.
```

**✅ Good:**
```
Recent systems—spanning X (Wang et al., 2023), Y (Zhang et al., 2024), 
and Z (Liu et al., 2025)—demonstrate that [general finding].
```

**Difference:**
- Bad: Paper-by-paper summary
- Good: Topic-driven synthesis

---

### **3. Filler Words**

**❌ Delete these:**
```
"In order to..." → "To..."
"It is important to note that..." → (delete, just state it)
"We can see that..." → (delete, it's obvious)
"There are several approaches..." → (weak opening)
```

**✅ Every word should earn its place:**
```
"Personalization becomes critical" (not "It is important to note that 
personalization becomes critical")
```

---

### **4. Passive Voice for Important Claims**

**❌ Bad:**
```
It has been shown that memory improves personalization.
```

**✅ Good:**
```
Recent systems demonstrate that persistent memory improves personalization 
(Mem0, 2025; Memoria, 2025).
```

**Difference:**
- Passive: no actor, no citation
- Active: clear actor + evidence

---

## 📏 Length Guidelines

### **Paragraph Length**

**✅ Optimal:**
- Introduction: 3-4 paragraphs total
- Related Work: 1-2 paragraphs per section
- Each paragraph: 4-8 sentences

**Rule:**
- If paragraph > 10 sentences → split
- If paragraph < 3 sentences → merge or expand

---

### **Sentence Length**

**✅ Mix it up:**
```
Short (stress): "This creates a critical limitation for personalization."
Medium (flow): "As these agents move to persistent deployment, the 
pressure on personalization intensifies."
Long (elaborate): "Unlike task-bounded agents that terminate after 
completing a workflow, personal AI agents maintain a persistent 
relationship with a single user across domains, adapting to evolving 
preferences over weeks and months."
```

**Rule:**
- Not all same length (boring rhythm)
- Use short for emphasis
- Use long for complex ideas

---

## 🎨 Section-Specific Guidelines

### **Introduction Checklist**

- [ ] Define key terms immediately (not in Section 2)
- [ ] State problem in first paragraph
- [ ] Use concrete example (not abstract)
- [ ] Explicit RQ list (RQ1, RQ2, RQ3)
- [ ] Explicit contributions (numbered list)
- [ ] No "In this paper..." or "The rest of this paper..."

---

### **Related Work Checklist**

- [ ] Opening principle (why related work matters)
- [ ] Each section has narrative arc
- [ ] Use BUT strategically (2-3 times total)
- [ ] Dense citations (2-5 per key statement)
- [ ] No detailed paper summaries
- [ ] Final section synthesizes all gaps
- [ ] Every section points to thesis gap

---

### **Methods Checklist (Upcoming)**

- [ ] Justify methodology choice
- [ ] Not just "we did X" but "why X"
- [ ] Connect to research questions
- [ ] Acknowledge limitations honestly

---

### **System Design Checklist (Upcoming)**

- [ ] Design rationale (why this architecture)
- [ ] Not just "what" but "why"
- [ ] Connect to Related Work findings
- [ ] Diagrams where helpful

---

### **Evaluation Checklist (Upcoming)**

- [ ] Connect back to RQs explicitly
- [ ] Not just metrics, but insights
- [ ] What did we learn? (not just what happened)
- [ ] Honest about limitations

---

### **Discussion Checklist (Upcoming)**

- [ ] Synthesize findings (not just repeat)
- [ ] Design implications (actionable)
- [ ] Theoretical contributions
- [ ] Limitations (honest, not defensive)
- [ ] Future work (specific, not generic)

---

## 💡 Quick Reference

### **Before You Write**

1. **What's the ONE key message?**
2. **Why should reader care?**
3. **What's the BUT?**
4. **What concrete example can I use?**

### **After You Write**

1. **Delete filler words** (In order to, It is important to note)
2. **Check every sentence has purpose**
3. **Add dense citations** (2-5 per key claim)
4. **Verify BUT usage** (2-3 times in Related Work)
5. **Find concrete examples** (replace abstract statements)

### **Final Polish**

1. **Read aloud** (does it flow?)
2. **One-sentence summary** (can you summarize each paragraph?)
3. **Check transitions** (does each paragraph connect?)
4. **Count citations** (dense enough?)

---

## 📊 Style Comparison

| Aspect | This Thesis Style | Traditional Academic Style |
|--------|------------------|---------------------------|
| **Opening** | Define + Problem immediately | Background + Context |
| **Citation** | Dense (2-5 per statement) | Sparse (1-2 per paper) |
| **BUT usage** | Strategic (2-3 times) | Frequent (every paragraph) |
| **Paper descriptions** | Minimal (topic only) | Detailed (methods) |
| **Examples** | Concrete (daily life) | Abstract (user context) |
| **Transitions** | Content-driven | Section markers ("Next...") |
| **Filler words** | Deleted | Often present |
| **Length** | Compact (~900w) | Verbose (~1500w) |

---

## 🎯 Golden Rules

1. **Every sentence earns its place or gets deleted**
2. **Related Work serves the problem, not knowledge demonstration**
3. **Use concrete examples, not abstractions**
4. **Dense citations, sparse explanations**
5. **Strategic BUTs, not constant negativity**
6. **Define + Problem in one paragraph**
7. **No filler words, no passive voice for claims**
8. **Transitions show logical flow, not section markers**

---

**Use this guide for:**
- Methods chapter
- System Design chapter
- Evaluation chapter
- Discussion chapter

**Maintain consistency across all chapters.**
