# Thesis Presentation - Midterm Defense

**Title:** Physical-World Observation for Personal AI Agent Personalization
**Author:** Chris Wu
**Duration:** 15-20 minutes

---

## Title

**Physical-World Observation for Personal AI Agent Personalization**

*Towards More Physical-Aware Personalization*

Chris Wu
March 2026

---

## Motivation

### **Personal AI Agents Are Here**
show how hot OpenClaw is right now

### **Why Personalization Matters**

**Agents That Know You > Agents That Don't**

- **Generic agent:** Similar behavior for everyone
- **Personalized agent:** Adapts, learns, and evolves with you

**Personalization = Effectiveness**
- Know what you like → Better recommendations, adapts to your preferences
- Know what you don't like → Fewer interruptions, avoids what doesn't work for you
- Know what you need, what you want to achieve, even who you want to become → More helpful, even in a proactive way

### **The Blindness Problem**

**Current Personalization is Limited**

- **What agents have:** Digital traces (chats, calendars, files)
- **What agents lack:** Physical context (where you are, what you're doing, your state)

**Result:** Agents personalize from half the picture

---

## Research Gap

### **Current Limitations**

| Dimension | Current Status | Missing |
|-----------|---------------|---------|
| **Personalization** | Digital-only (chats, files, calendars) | Physical-world input |
| **Memory Architectures** | Text-based, symbolic | Entry point for continuous sensing |
| **Egocentric Vision** | Mature technology (Ego4D, VLMs) | Agent integration |
| **Self-Logging** | Captured for human review | Agent memory connection |

**The Gap:**
No work integrates egocentric perception into agent memory for personalization.

---

## Research Questions

### **Three Research Questions**

**RQ1:** What physical-world information becomes visible through egocentric perception that remains invisible through digital traces alone?

**RQ2:** In what contexts does this information improve personalization vs. introduce noise?

**RQ3:** What design requirements emerge for integrating continuous sensing into agent memory?

---

## Approach

### **Exploratory + Autoethnographic**

**Not Assuming—Discovering**

- **Not:** Proving physical context helps
- **But:** Discovering where it helps and where it doesn't

**Autoethnographic Self-Study**

- 2 weeks continuous capture
- Design Science Research (artifact + empirical findings)

---

## Design Decisions

### **Why Egocentric Vision as the primary sensing modality?**

**Three Reasons:**

1. **Mobility**
An egocentric device moves with the wearer, enabling continuous capture across locations throughout the day
This capability is reinforced by a new hardware trend: consumer smart glasses with cameras are going viral

2. **Information density**
A first-person visual perspective captures environment, activity, and object interaction simultaneously within a single sensing channel

3. **Implicit attention signal**
what recurrently appears in the field of view reflects what the user engages with; what is consistently absent suggests disinterest.

4. **Technical maturity**
Vision-language models (VLMs) can now convert egocentric imagery into structured text descriptions of activities, objects, and context

**Other 辅助:** audio, IMU

---

### **Why OpenClaw?**

**Three Reasons:**

1. **Deployed baseline**
OpenClaw is one of the few open-source personal AI agents in sustained real-world use

2. **Integration opportunity**
OpenClaw personalizes through a workspace of plain markdown files

3. **Inspectability and format compatibility**
human-readable markdown

---

## System Design

### **Three-Layer Architecture**

**Layer 1: Capture (continuous)**
- Egocentric capture (iOS app)
- Privacy filtering (on-device)
- Other sensors as trigger + tag maker (audio, IMU)
↓

**Layer 1.5: Pre-Processing (passive consumer, awakened by trigger or timeout)**
- Discard junk
- Importance scoring
- Decide batch boundary for Layer 2

**Layer 2: Inference (batch, awakened by Layer 1.5)**
- VLM API call (cloud) (video → text)
- Output: observation + interpretive annotation

**Layer 3: Memory Integration**
- 3 tiers
   - physical-logs/YYYY-MM-DD.md
   - physical-insights/YYYY-MM.md
   - physical-pattern.md

**Layer 3.5: Memory Retrieval & Context Loading**
- Bootstrap injection (physical-pattern.md)
- AGENT.md instruction (physical-insights/YYYY-MM-DD.md)
- on-demand search (physical-logs/YYYY-MM-DD.md)

---

## Methodology

### **Autoethnographic Self-Study**

**Duration:** 7 days continuous capture

**Data Sources:**
- Egocentric vision (images)
- Perception logs
- Memory files
- Agent interaction transcripts
- Design iteration logs
- Autoethnographic daily reflections

**Analysis:**
- What physical info was captured?
- When was it queried by agent?
- Did it help or hurt personalization?

**Validity Strategies:**
- Transparency of process
- Depth over breadth
- Theoretical grounding

---

## Expected Contributions

### **[Midterm: Expected Contributions]**
### **[Final: Contributions]**

**1. Empirical Findings**
- Where physical context aids personalization
- Where it introduces noise
- Design patterns for effective use

**2. System Artifact**
- Egocentric vision + OpenCLAW integration
- Privacy-preserving capture pipeline
- Open-source implementation

**3. Design Implications**
- Storage granularity (text vs. key frames)
- Privacy trade-offs (retention policies)
- Abstraction mechanisms (real-time vs. nightly)

---


