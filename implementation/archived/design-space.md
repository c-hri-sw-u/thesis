# System Design Space: Egocentric Perception Pipeline for OpenClaw

> This document maps every design decision in the pipeline, discusses trade-offs for each option, and marks which choices are **locked**, which are **recommended defaults**, and which are **design variables to explore during the experiment**.

---

## Overview: The Core Coupling

This system is not a linear pipeline. The central design tension is that **capture rate, preprocessing strategy, and inference strategy are mutually constrained**. A decision at any layer restricts or enables options at adjacent layers. The document is organized by layer, but cross-references between layers are marked with → arrows.

**Two architecture paths** structure the entire design space:

- **Path A (per-frame inference):** Each captured frame is sent individually to the VLM. Simpler pipeline, but capture rate is bounded by API latency, and each VLM call lacks cross-frame context.
- **Path B (batch inference):** Frames are accumulated into batches, preprocessed to extract key frames, then sent to the VLM as a group. More complex, but enables higher capture rates, lower API cost, and native cross-frame reasoning.

Path A and Path B share the same Layer 1 (capture hardware + modalities), Layer 3 (memory integration), and Layer 4 (application/evaluation). They diverge at Layer 1.5 (preprocessing) and Layer 2 (inference).

---

## Layer 1: Capture

**Output:** Raw timestamped frames + continuous Audio/IMU streams

### 1.1 Vision Capture

**🔒 Locked:** Egocentric vision is the primary modality. Smartphone worn on body as hardware proxy for smart glasses.

| Option | Description | Pros | Cons | Notes |
|--------|-------------|------|------|-------|
| **Timer-based, every N seconds** | Fixed-interval frame grab | Simple, predictable data rate; already implemented | Misses transient events; captures redundant frames during static scenes | N is coupled to inference strategy: Path A needs N≥12s; Path B allows N=3-5s |
| **Trigger-based only** | Frames captured only when IMU/Audio detects scene change | Maximally efficient; every frame is information-rich | Misses gradual changes; no baseline coverage during stable scenes; depends entirely on trigger quality | Not recommended as sole strategy |
| **Hybrid: timer + trigger** | Fixed-interval baseline + extra frames on scene change | Best coverage; captures both stable patterns and transitions | Higher raw data volume; needs preprocessing to manage | **Recommended default** |

**→ Coupling to Layer 2:** If using Path A (per-frame inference), timer interval must be ≥12s to allow API round-trip. If using Path B (batch inference), timer can be 3-5s because frames are batched before API call.

**🧪 Experiment variable:** Timer interval N. Start with 5s for Path B, observe whether preprocessing adequately filters redundancy. If API costs are too high, increase to 8-10s.

### 1.2 Audio Channel

**🔒 Locked:** Supplementary modality. Audio never competes with vision as the primary data source.

Audio serves **two distinct roles** in the pipeline:

#### 1.2a Audio as Trigger (→ feeds Layer 1 capture + Layer 1.5 batch boundary)

| Option | Description | Pros | Cons |
|--------|-------------|------|------|
| **Voice activity detection (VAD)** | Detect onset/offset of human speech | Captures social context transitions (alone → conversation); lightweight | Doesn't distinguish user speech from background TV/radio |
| **Ambient noise level change** | Detect significant dB shift | Captures environment transitions (quiet office → noisy café) | High false positive rate from transient sounds |

**Recommended:** VAD as primary audio trigger. Noise level change as secondary signal fed to preprocessing (1.5), not directly triggering capture.

#### 1.2b Audio as Data (→ feeds Layer 2 VLM prompt as metadata tag)

| Option | Description | Pros | Cons |
|--------|-------------|------|------|
| **Hardcoded labels only** | Classify into {silent, quiet, moderate, loud} + {no_speech, speech_detected} | Zero API cost; fast; deterministic | Loses speech content; coarse |
| **Labels + speech transcription** | Above labels + ASR on detected speech segments | Captures conversation topics, which are rich personalization signals | ASR API cost; privacy concerns with recording others; latency |
| **Labels + speaker count** | Above labels + estimate number of distinct voices | Captures social context (alone, 1-on-1, group) without content | Less informative than transcription but more privacy-preserving |

**Recommended default:** Labels + speaker count. This gives the VLM useful social context ("user is in a conversation with 2 others in a loud environment") without the cost and privacy burden of full transcription.

**🧪 Experiment variable:** Whether to enable speech transcription for a subset of the study period to compare personalization quality with vs. without conversation content.

### 1.3 IMU Channel

**🔒 Locked:** Supplementary modality.

#### 1.3a IMU as Trigger (→ feeds Layer 1 capture + Layer 1.5 batch boundary)

| Option | Description | Pros | Cons |
|--------|-------------|------|------|
| **Motion state change** | Detect transitions: stationary→walking, walking→stationary, etc. | Strong scene change proxy (user left desk, arrived somewhere) | Misses scene changes without movement (someone enters the room) |
| **Orientation change** | Detect significant device orientation shift | May indicate user looking at something new | Very noisy; frequent false positives from normal body movement |

**Recommended:** Motion state change only. Orientation change is too noisy for triggering.

#### 1.3b IMU as Data (→ feeds Layer 2 VLM prompt as metadata tag)

| Option | Description | Pros | Cons |
|--------|-------------|------|------|
| **Binary: stationary / moving** | Simplest possible tag | Trivial to implement; always useful context | Loses transportation mode |
| **Activity classification** | Classify into {stationary, walking, running, cycling, in_vehicle} | Richer context for VLM | Requires more sophisticated classifier; some states hard to distinguish |

**Recommended default:** Activity classification if a reliable off-the-shelf classifier is available (e.g., iOS Core Motion); otherwise binary.

### 1.4 Layer 1 Combined Output

Each captured frame carries attached metadata:

```
{
  timestamp: ISO-8601,
  image: raw frame (JPEG),
  audio_tags: {
    noise_level: "quiet" | "moderate" | "loud",
    speech_detected: bool,
    speaker_count: int,
    transcript?: string  // optional, experiment variable
  },
  imu_tags: {
    motion_state: "stationary" | "walking" | "running" | "cycling" | "in_vehicle",
    is_scene_change: bool  // state transition detected
  }
}
```

---

## Layer 1.5: Preprocessing

> **This layer only exists in Path B.** Path A skips directly to Layer 2.

Preprocessing serves two functions: **define batch boundaries** and **filter frames within each batch**. These produce the "preprocess batch"—distinct from the "inference batch" defined in Layer 2.

### 1.5a Preprocess Batch Boundary

The preprocess batch boundary determines which raw frames are grouped together for filtering.

| Option | Description | Pros | Cons |
|--------|-------------|------|------|
| **Fixed time window** | Every T minutes, collect all frames since last batch | Predictable; simple to implement | May split a coherent scene across batches or merge distinct scenes into one |
| **Dynamic: IMU/Audio triggered** | Cut batch when scene change signal fires (motion state change, VAD onset/offset, noise level shift) | Batches align with natural scene boundaries; each batch = one coherent context | Variable batch size; very short scenes produce tiny batches; quiet periods produce huge batches |
| **Hybrid: dynamic + max window** | Scene change triggers cut, but also force a cut at max T minutes | Best of both: scene-aligned when possible, bounded when not | Slightly more complex; need to tune max T |

**Recommended default:** Hybrid with max window = 10 minutes. Scene changes (from IMU motion state change + Audio VAD transitions) trigger early cuts. This ensures no batch is incoherently long while respecting natural scene boundaries.

**🧪 Experiment variable:** Max window size T. Compare 5 min vs. 10 min vs. 15 min in terms of inference quality and API cost.

### 1.5b Frame Filtering Within Batch

Given a preprocess batch of N raw frames, select the K most informative ones.

| Filter | What it does | Why it matters |
|--------|-------------|----------------|
| **Black frame detection** | Discard frames that are mostly black (phone in pocket, camera covered) | Saves tokens; these frames carry zero information |
| **Blur detection** | Discard frames with high blur score (motion blur during walking) | Blurred frames confuse VLM; waste tokens |
| **Pixel similarity / deduplication** | Compare adjacent frames; drop near-duplicates | During static scenes (sitting at desk), consecutive frames are nearly identical |
| **Multimodal-informed prioritization** | Boost retention of frames captured during audio/IMU events (speech onset, motion change) | These frames are more likely to contain information-rich context transitions |

**Recommended:** Apply all four filters in sequence. Order: black → blur → deduplication → multimodal prioritization. The first three are pure subtraction (discard junk). The fourth is reranking (among surviving frames, prefer those near scene transitions).

**Target output:** From a 10-minute batch captured at 5s intervals (~120 raw frames), produce 4-8 key frames with their attached metadata.

**Implementation note:** All four filters are lightweight local computation (OpenCV pixel operations + threshold comparisons). No API calls. Cost ≈ negligible.

---

## Layer 2: Inference

**Output:** Structured text descriptions with timestamps and metadata

### 2.1 Inference Batch Definition (Path B only)

The inference batch may or may not match the preprocess batch 1:1.

| Option | Description | When to use |
|--------|-------------|-------------|
| **1:1 mapping** | Inference batch = preprocess batch | Default; simplest. Works when preprocess batches are well-scoped |
| **Merge** | Combine multiple small preprocess batches into one inference call | When consecutive batches share the same scene (e.g., three 2-minute batches all at the same desk) |
| **Split** | Break a preprocess batch into multiple inference calls | When a large batch contains a mid-batch scene change that preprocessing missed |

**Recommended default:** Start with 1:1 mapping. Merging and splitting add complexity that may not be justified until you observe failure modes during the experiment.

**🧪 Experiment variable:** Whether 1:1 is sufficient, or whether merge/split improves output quality. Log cases where 1:1 produces incoherent summaries.

### 2.2 VLM Call Design

**🔒 Locked:** Cloud API (Claude or GPT-4V). Local models insufficient for the structured reasoning required.

#### Path A: Per-Frame Prompt

```
Input:  1 image + audio tags + IMU tags + [optional: prior k frame summaries]
Output: Structured text description of this moment
```

| Design choice | Options | Trade-off |
|---------------|---------|-----------|
| **Context chaining** | (a) Stateless: each frame described independently | Simple, but no continuity ("user is in kitchen" repeated every 12s without recognizing it as a sustained activity) |
| | (b) Rolling summary: include last k frame summaries in prompt | Maintains narrative continuity; increases prompt length and cost per call |
| | (c) Accumulated status: maintain a running "current status" document, update with each frame | Most coherent output; highest prompt cost; status can drift from reality if VLM makes an error |
| **k value (if rolling)** | k=1 to k=5 | Higher k = more context but more tokens. k=3 is a reasonable default |

#### Path B: Batch Prompt

```
Input:  4-8 key frames + audio tags + IMU tags per frame + batch time range
Output: Scene summary covering the batch period
```

| Design choice | Options | Trade-off |
|---------------|---------|-----------|
| **Frame ordering in prompt** | (a) Chronological with timestamps | VLM can reason about temporal sequence naturally |
| | (b) Chronological + explicit "describe the transition between frames" instruction | Better at capturing change, but longer prompt |
| **Cross-batch context** | (a) No context from prior batches | Each batch is self-contained; may miss ongoing activities |
| | (b) Include prior batch summary (1 paragraph) | Maintains continuity across batches; small token overhead |
| **Output format** | (a) Free-form paragraph | Flexible; VLM chooses what to emphasize |
| | (b) Structured fields: {activity, location, objects, social_context, notable_events} | Consistent; easier to parse for memory integration; may force VLM to hallucinate fields it can't observe |

**Recommended defaults:**
- Path B with chronological frames + timestamps
- Include prior batch summary (1 paragraph) for continuity
- Structured output with optional fields (VLM can mark fields as "not observed" rather than hallucinate)

### 2.3 Prompt Design Principles

Regardless of path, the VLM prompt should:

1. **Prioritize personalization-relevant information.** Not "describe what you see" but "what does this reveal about the user's habits, preferences, environment, and current activity that a personal AI agent should know?"
2. **Include multimodal tags as context.** "The IMU indicates the user is stationary. Audio detects 2 speakers in a quiet environment." This grounds the VLM's interpretation.
3. **Request explicit uncertainty.** "If you cannot determine the activity, say so rather than guessing."
4. **Constrain output length.** Per-frame: 2-3 sentences. Per-batch: 1 short paragraph (4-6 sentences).

**🧪 Experiment variable:** Prompt wording. Iterate across the study period. Log which prompt versions produce the most useful memory entries.

---

## Layer 3: Memory Integration

**Output:** Physical-world observations written into OpenClaw's memory system

### 3.1 Integration Strategy

| Option | Description | Pros | Cons |
|--------|-------------|------|------|
| **3a: Silent session** | Open a dedicated OpenClaw session. Feed VLM output as user messages. Set to silent mode (no output needed). OpenClaw's existing memory pipeline processes the input: writes to daily logs, extracts persistent facts to MEMORY.md | Zero new code for memory logic; leverages OpenClaw's existing memory curation; directly tests thesis claim that text-native interface enables seamless integration | Relies on OpenClaw's memory heuristics to correctly identify what's worth remembering from physical observations; less control over what gets stored |
| **3b: Direct write** | Build a new module that parses VLM output and writes directly to OpenClaw's markdown files (daily log entries, MEMORY.md updates) | Full control over storage format and granularity; can enforce specific schemas | Bypasses OpenClaw's own intelligence about what to remember; more code to write and maintain; weakens thesis argument about integration simplicity |
| **3c: Hybrid** | Silent session as default path + a separate "perception log" markdown file that stores all raw VLM outputs regardless of what OpenClaw's memory pipeline chooses to retain | Preserves inspectability for research (RQ1: what did perception capture?); still leverages OpenClaw's memory for actual agent use (RQ2: what was useful?) | Two storage locations; need to reconcile during analysis |

**Recommended default:** **3c (Hybrid).** The perception log is essential for answering RQ1 (you need the full record of what was captured to assess coverage), while the silent session path is essential for RQ2 and RQ3 (you need to observe how OpenClaw's existing memory pipeline handles physical-world input).

**🧪 Experiment variable:** Compare what the perception log contains vs. what OpenClaw's memory pipeline actually retained. The gap between them is a direct finding for RQ3.

### 3.2 Nightly Summarization

| Option | Description | Pros | Cons |
|--------|-------------|------|------|
| **No nightly summary** | Rely entirely on real-time (Path A) or batch (Path B) outputs | Simpler; avoids redundant processing | Misses longitudinal patterns that only emerge from a full day's data |
| **Nightly summary** | End-of-day job that reads the perception log, produces a 1-paragraph daily summary of physical-world patterns, and feeds it to OpenClaw | Captures day-level patterns ("user cooked dinner at 6pm, then worked at desk until 10pm"); enables weekly/monthly pattern detection over time | Additional API cost; one more pipeline component to build |

**Recommended default:** **Nightly summary enabled.** Personalization depends on longitudinal patterns (RQ2). A per-batch summary captures "user is cooking right now." A nightly summary captures "user cooks every evening around 6pm." Only the latter is a durable personalization signal.

**🧪 Experiment variable:** Compare agent behavior with vs. without nightly summaries during different phases of the study.

### 3.3 Retention Policy

**🔒 Locked:** 14-day rolling retention for raw frames and perception logs. After 14 days, raw data is deleted; only the memory entries that OpenClaw chose to retain persist.

This is both a privacy measure and a practical constraint (storage). It also creates a natural experimental boundary: after 14 days, the agent must rely on its own memory abstractions, not raw data.

---

## Layer 4: Application / Evaluation

### 4.1 Passive Observation (Primary)

**🔒 Locked as primary evaluation method.** This is the autoethnographic core of the thesis.

During normal daily use of OpenClaw, observe:
- Does the agent reference physical-world information in its responses?
- Does this information improve response relevance compared to a digital-only baseline?
- Are there cases where physical-world memory introduces noise or irrelevance?

**Method:** Daily journal entries documenting interactions where physical context was or was not surfaced, annotated with assessment of helpfulness.

### 4.2 Proactive Cron Job (Secondary, Conditional)

| Option | Description | Pros | Cons |
|--------|-------------|------|------|
| **No proactive check** | Agent only uses physical context when user initiates interaction | Simpler; isolates personalization variable from proactive agency variable | May undercount the value of physical context (agent "knows" but never gets a chance to use it) |
| **Periodic self-check** | Cron job triggers OpenClaw to review recent physical observations and decide: "Is there something I should proactively tell the user?" If yes, push a message via IM | Tests a stronger personalization claim (agent not only knows more, but acts on it); closer to the cooking example in the Introduction | Introduces proactive agency as a confounding variable; harder to isolate whether improvement is from perception or from proactivity |

**Recommended:** **Start without proactive cron (Phase 1, Week 1-2).** If passive observation reveals that physical context enters memory but rarely surfaces in interactions, **add proactive cron as Phase 2 design iteration.** This way, the need for proactivity becomes a research finding rather than a presupposition.

**🧪 Experiment phases:**
- **Phase 1 (Week 1-2):** Pipeline running, no proactive cron. Assess whether physical context surfaces organically.
- **Phase 2 (Week 3-4, if needed):** Add proactive cron. Compare with Phase 1 journal entries.

---

## Recommended Implementation Path

Given the two-week initial development window, here is a phased build order:

### Sprint 1 (Days 1-3): Minimum Viable Pipeline
1. Timer-based capture at 5s intervals (already partially implemented)
2. Basic preprocessing: black frame + blur detection + pixel similarity deduplication
3. Per-batch VLM inference with 1:1 preprocess→inference batch mapping, fixed 10-min window
4. Silent session integration into OpenClaw
5. Perception log (raw VLM outputs saved as markdown)

**Goal:** End-to-end data flow from camera to OpenClaw memory. Quality doesn't matter yet. Prove the path works.

### Sprint 2 (Days 4-7): Multimodal + Dynamic Batching
6. Add IMU motion state classifier + Audio VAD + noise level classifier
7. Attach tags to each frame
8. Implement hybrid batch boundary (scene change trigger + max window)
9. Multimodal-informed frame prioritization in preprocessing
10. Include tags in VLM prompt

**Goal:** Full multimodal pipeline with dynamic batching. Start wearing the device daily.

### Sprint 3 (Days 8-10): Nightly + Prompt Iteration
11. Nightly summarization job
12. Iterate VLM prompt based on observed output quality
13. Tune preprocessing parameters (similarity threshold, batch max window)

**Goal:** Pipeline stable enough for sustained daily use. Begin formal study period.

### Sprint 4 (Days 11-14): Observation + Iteration
14. Daily autoethnographic journal
15. Review perception log vs. OpenClaw memory retention
16. Identify failure modes and iterate

**Goal:** Collect data for thesis analysis. Document design decisions and their outcomes.

---

## Decision Summary Table

| Decision | Options | Recommended | Status | Experiment? |
|----------|---------|-------------|--------|-------------|
| Architecture path | A (per-frame) / B (batch) | B | Recommended | Compare in thesis discussion |
| Capture interval | 3s / 5s / 8s / 12s | 5s (Path B) | Recommended | Tune during Sprint 3 |
| Capture mode | Timer / Trigger / Hybrid | Hybrid | Recommended | — |
| Audio trigger | VAD / Noise change | VAD | Recommended | — |
| Audio data | Labels only / +transcription / +speaker count | Labels + speaker count | Default | Test transcription in Phase 2 |
| IMU trigger | Motion state change / Orientation | Motion state change | Locked | — |
| IMU data | Binary / Activity classification | Activity classification | Recommended | Fall back to binary if classifier unavailable |
| Preprocess batch boundary | Fixed / Dynamic / Hybrid | Hybrid (max 10 min) | Recommended | Tune max window |
| Frame filter | Black+Blur+Similarity+Multimodal | All four | Recommended | — |
| Inference batch | 1:1 / Merge / Split | 1:1 | Default | Log failures, add merge/split if needed |
| VLM provider | Claude / GPT-4V | TBD | Open | Compare if budget allows |
| Context chaining (Path B) | No context / Prior batch summary | Prior batch summary | Recommended | — |
| Output format | Free-form / Structured | Structured with optional fields | Recommended | Iterate prompt |
| Memory integration | Silent session / Direct write / Hybrid | Hybrid (3c) | Recommended | Compare perception log vs. retained memory |
| Nightly summarization | Yes / No | Yes | Recommended | Compare with/without across phases |
| Proactive cron | Yes / No / Phased | Phased (add in Phase 2 if needed) | Recommended | Phase 1 vs. Phase 2 comparison |
| Retention policy | 14-day rolling | 14-day | Locked | — |
