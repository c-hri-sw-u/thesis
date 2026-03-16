**Path B: All Decision Points**

**Layer 1: Capture**

- 🔒 Primary modality: egocentric vision via smartphone
- Vision
  - 👉 Capture mode: hybrid (timer + trigger)
  - 🧪 Timer interval N — 3s / 5s / 8s
- Audio
  - 👉 Audio as trigger: VAD → triggers extra frame capture + preprocess
  - 
  - 👉 Audio as data: labels + speaker count (attached to each frame)
  - 🧪 Audio transcription — on / off
- IMU
  - 🔒 IMU as trigger: motion state change → triggers extra frame capture + preprocess
  - 👉 IMU as data: activity classification (attached to each frame)

**Layer 1.5: Preprocessing**

- 👉 Preprocess trigger: 
  - scene change (IMU/Audio) fires a preprocess; 
  - max window (e.g. 10 min) forces one if no trigger
- 🧪 Max window size — 5 / 10 / 15 min
- 👉 Frame filters: black + blur + similarity + multimodal prioritization
- 🧪 Similarity threshold — tune during study
- 🧪 Target key frames per batch — 4-8 range

**Layer 2: Inference**

- 👉 Inference batch: 1:1 with preprocess batch
- 🧪 Merge / split — add if 1:1 fails
- ❓ VLM provider — Claude / GPT-4V
- 👉 Cross-batch context: prior batch summary (1 paragraph)
- 👉 Output format: structured with optional fields
- 🧪 Prompt wording — iterate across study
- 🧪 Output length constraint — 4-6 sentences per batch

**Layer 3: Memory Integration**

- 👉 Strategy: hybrid (silent session + perception log)
- 👉 Nightly summarization: enabled
- 🧪 Nightly on/off comparison — across phases
- 🔒 Retention: 14-day rolling

**Layer 4: Application**

- 🔒 Primary: passive observation (autoethnographic journal)
- 🧪 Proactive cron — add in Phase 2 if needed

---

🔒 Locked (4) · 👉 Recommended (10) · 🧪 Experiment variable (9) · ❓ Open (1)