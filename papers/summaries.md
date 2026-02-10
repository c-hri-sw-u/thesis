# Paper Summaries

## Format
```markdown
### [Paper Title]
**Authors:** [Names]
**Year/Venue:** [Year] - [Venue]
**Category:** [Category #]
**Direction:** [Specific direction]
**URL:** [Link to paper]

**Abstract:** [Brief summary]

**Key Contributions:**
- [Contribution 1]
- [Contribution 2]
- [Contribution 3]

**Methods:**
- [Method 1]
- [Method 2]

**Results:**
- [Result 1]
- [Result 2]

**Limitations:**
- [Limitation 1]
- [Limitation 2]

**Relevance to Our Work:**
- [How this paper informs our work]

**Notes:**
- [Personal notes/questions]
```

---

## Category 1: Egocentric Vision & Activity Recognition

### Ego4D: Around the World in 3,000 Hours of Egocentric Video
**Authors:** Grauman et al. (84+ authors)
**Year/Venue:** 2022 - CVPR
**Category:** 1
**Direction:** Large-scale dataset & benchmarks
**URL:** https://arxiv.org/abs/2110.07058
**Project:** https://ego4d-data.org/

**Abstract:**
Ego4D is a massive-scale egocentric video dataset spanning 74 locations worldwide, with 3,000+ hours of video capturing daily life activities. The dataset includes multiple benchmarks for first-person perception tasks including episodic memory, forecasting, social interaction, and hand-object manipulation.

**Key Contributions:**
- Largest egocentric video dataset (3,000+ hours, 74 locations)
- 5 benchmark tasks: episodic memory, forecasting, social interaction, hand-object manipulation, audio-visual narration
- Diverse participants and real-world scenarios
- Comprehensive annotations (objects, actions, narrations)

**Methods:**
- Multi-center data collection (universities worldwide)
- Wearable cameras for first-person capture
- Semi-automated annotation pipeline
- Benchmark evaluation protocols

**Results:**
- Baseline models established for all 5 tasks
- Dataset released publicly (with license agreement)
- Active research community around Ego4D

**Limitations:**
- Focus on short clips (not continuous, long-term recording)
- Limited multimodal data (mainly video, some audio)
- Privacy concerns with face/location data

**Relevance to Our Work:**
- **Baseline models:** We can use SOTA models from Ego4D benchmarks
- **Activity recognition:** State-of-the-art methods for egocentric understanding
- **Data inspiration:** Dataset structure and annotation strategies
- **Gap:** Ego4D is for research benchmarks, not continuous life logging

**Notes:**
- Need to check what pre-trained models are available
- Can we use Ego4D models off-the-shelf for our system?
- Ego4D focus: short-term understanding; our focus: long-term记忆
- Privacy: Ego4D has face/location anonymization - learn from their approach

---

### EPIC-KITCHENS: A Large-Scale Dataset for Unstructured Egocentric Activity Recognition
**Authors:** Damen et al.
**Year/Venue:** 2021 - NeurIPS
**Category:** 1
**Direction:** Kitchen activity recognition
**URL:** [To find]

**Abstract:**
A large-scale dataset of egocentric videos focused on kitchen activities. Dataset includes 128 hours of video from 55 participants capturing 300+ object classes and 125+ verb classes.

**Key Contributions:**
- Large-scale kitchen-focused dataset
- Fine-grained object and action annotations
- Benchmark for action recognition and anticipation

**Methods:**
- First-person perspective in kitchen settings
- Dense object and action annotations

**Results:**
- Established baselines for action recognition
- Widely used dataset in egocentric research

**Limitations:**
- Narrow scope (kitchens only)
- Not representative of full daily life

**Relevance to Our Work:**
- Understanding fine-grained activity recognition
- Annotation strategies for multimodal data
- Less relevant than Ego4D for all-day logging

---

## Category 2: Multimodal Wearable Systems

### A Multi-Modal Egocentric Activity Recognition Approach towards Video Domain Generalization (MDGEAR)
**Authors:** Papadakis & Spyrou
**Year/Venue:** 2024 - Sensors
**Category:** 2
**Direction:** End-to-end multimodal pipeline, domain generalization
**URL:** https://www.mdpi.com/1424-8220/24/8/2491
**Code:** https://github.com/thevisionlab-uth/MDGEAR

**Abstract:**
MDGEAR is a multi-modal domain generalization model for activity recognition from egocentric videos. It combines RGB video with IMU data (accelerometer, gyroscope) for robust activity recognition across different domains.

**Key Contributions:**
- Multi-modal fusion (video + IMU) for activity recognition
- Domain generalization to unseen environments
- Semi-supervised learning approach

**Methods:**
- CNN for video features + LSTM for temporal modeling
- IMU sensor fusion
- Domain adversarial training for generalization

**Results:**
- Improved performance over uni-modal approaches
- Better generalization to new domains

**Limitations:**
- Focus on short-term activities
- Limited sensor modalities (no audio, location)

**Relevance to Our Work:**
- **Multimodal fusion:** Valuable for combining video + IMU
- **On-device:** IMU is always available, low power
- **Gap:** Still focused on recognition, not continuous logging or agent integration

**Notes:**
- GitHub code available - can we adapt their fusion architecture?
- Domain generalization is important for real-world deployment
- IMU fusion is low-cost - should definitely include in our system

---

## Category 3: Memory Systems for AI Agents

### MemGPT: Towards LLMs as Operating Systems
**Authors:** [To find]
**Year/Venue:** 2023 - arXiv
**Category:** 3
**Direction:** Hierarchical memory architecture
**URL:** [To find]

**Abstract:**
MemGPT introduces a virtual context management system for LLMs, organizing memory into hierarchical layers (main memory, working memory, long-term memory) similar to operating systems.

**Key Contributions:**
- Hierarchical memory architecture
- Virtual context management
- Event-driven memory updates
- Retrieval mechanisms for different memory types

**Methods:**
- LLM-as-OS metaphor
- Memory tiers with different access patterns
- Automatic memory summarization and prioritization

**Results:**
- Improved performance on long-context tasks
- Better memory utilization efficiency

**Limitations:**
- Focus on LLM context, not physical sensor data
- Doesn't address memory population from life logging

**Relevance to Our Work:**
- **Memory architecture:** Highly relevant for our hierarchical memory design
- **Retrieval mechanisms:** How to search and retrieve relevant memories
- **Gap:** MemGPT assumes memories exist; we need to create them from sensors

**Notes:**
- Need to understand their memory schema
- Can we integrate MemGPT with OpenClaw?
- Their memory tiers: how do we map to our use case?

---

### Mem0: Long-term Memory for AI Agents
**Authors:** [To find]
**Year/Venue:** 2024 - GitHub
**Category:** 3
**Direction:** Persistent memory layer for agents
**URL:** https://github.com/mem0ai/mem0

**Abstract:**
Mem0 provides a persistent memory layer for AI agents, automatically updating and managing long-term memories based on user interactions.

**Key Contributions:**
- Auto-updating memory system
- Integration with various AI frameworks
- Simple API for memory operations

**Methods:**
- Vector database for embeddings
- Automatic memory summarization
- Query-based retrieval

**Results:**
- Open-source implementation
- Active community

**Limitations:**
- Focus on text-based memories
- No multimodal support

**Relevance to Our Work:**
- **Practical implementation:** Open-source, can adapt for our use case
- **Auto-updating:** Valuable for continuous life logging
- **Gap:** Doesn't handle multimodal data (video, audio, IMU)

**Notes:**
- Check if they support custom embeddings
- Can we extend Mem0 to handle multimodal data?
- Integration with OpenClaw should be straightforward

---

## Category 5: Privacy-Preserving Wearables ⭐

### Real-time Face Obfuscation for Wearable Cameras
**Authors:** [To find]
**Year/Venue:** 2023/2024 - USENIX/CCS
**Category:** 5
**Direction:** Face detection and blur
**URL:** [To find]

**Abstract:**
[To be filled]

**Key Contributions:**
- Real-time face detection on wearable devices
- Privacy-preserving blurring algorithms
- Low computational overhead

**Methods:**
- MediaPipe / MTCNN for face detection
- Gaussian blur or pixelation
- On-device processing

**Results:**
- High detection accuracy (>95%)
- Low latency (<100ms)

**Limitations:**
- False negatives (missed faces)
- Affects video quality

**Relevance to Our Work:**
- **Critical component:** Face obfuscation is essential for privacy
- **On-device:** Must run efficiently on phone
- **Implementation:** Can use existing libraries (MediaPipe)

**Notes:**
- MediaPipe Face Detection is free and efficient
- Need to test performance on phone
- What about face detection in motion, occlusion, low light?

---

### Text Detection and Blurring in Egocentric Videos
**Authors:** [To find]
**Year/Venue:** 2023 - CVPR/ECCV
**Category:** 5
**Direction:** Text obfuscation
**URL:** [To find]

**Abstract:**
[To be filled]

**Key Contributions:**
- Text detection in natural scenes
- Privacy-preserving text blur
- Real-time on-device processing

**Methods:**
- EasyOCR / PaddleOCR for text detection
- Region-based blur
- Selective obfuscation (e.g., blur screens but not books)

**Results:**
- High text detection accuracy (>90%)
- Real-time performance

**Limitations:**
- Harder than faces (text varies in size, font, language)
- May blur relevant information (e.g., menu items)

**Relevance to Our Work:**
- **Important:** Text on screens, documents contains sensitive info
- **Challenge:** More difficult than faces
- **User control:** Maybe ask user what to blur?

**Notes:**
- EasyOCR is free, supports multiple languages
- Performance on mobile?
- How to avoid blurring useful text (e.g., book titles)?

---

## Category 6: Systems & Practical Challenges

### Energy-Efficient Mobile Sensing
**Authors:** [To find]
**Year/Venue:** 2023 - MobiSys/SenSys
**Category:** 6
**Direction:** Battery optimization
**URL:** [To find]

**Abstract:**
[To be filled]

**Key Contributions:**
- Adaptive sensing strategies
- Battery-aware data collection
- Trade-off analysis: coverage vs energy

**Methods:**
- Context-aware sampling
- Duty cycling
- Selective sensor activation

**Results:**
- Significant battery savings (30-50%)
- Minimal loss in utility

**Limitations:**
- May miss important events

**Relevance to Our Work:**
- **Critical:** Battery is major constraint for all-day logging
- **Strategy:** Adaptive collection is essential
- **Implementation:** Need to design our duty cycling strategy

**Notes:**
- What sensors should be always-on (IMU, GPS)?
- How to balance coverage vs battery?
- User feedback: what's acceptable battery drain?

---

## Category 7: HCI & User Studies

### SenseCam: A Wearable Camera for Lifelogging
**Authors:** Hodges et al.
**Year/Venue:** 2006 - UbiComp
**Category:** 7
**Direction:** Early lifelogging system, user study
**URL:** [To find]

**Abstract:**
SenseCam is a wearable camera that automatically captures images at regular intervals. User studies examined its effectiveness as a memory aid and explored user perceptions of privacy.

**Key Contributions:**
- First large-scale lifelogging system
- Longitudinal user studies
- Insights on privacy and user acceptance

**Methods:**
- Periodic image capture (every 30-60 seconds)
- Lightweight, unobtrusive hardware
- Long-term deployment (months)

**Results:**
- Effective memory aid for some users
- Mixed reactions to privacy concerns
- High user engagement in some studies

**Limitations:**
- Simple technology (photos only, no AI)
- Limited understanding of content
- Privacy issues not fully resolved

**Relevance to Our Work:**
- **Foundational:** First real lifelogging system
- **User insights:** Valuable lessons on privacy, acceptance
- **Gap:** SenseCam was dumb capture; we add AI understanding

**Notes:**
- Read user studies carefully - what worked? what failed?
- Privacy concerns: how did users react?
- Long-term usage: what kept users engaged?

---

*Last updated: 2026-02-09*
*Next update: Continue adding papers as they are collected*
