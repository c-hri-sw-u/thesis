# Scope: All-Day Life Logging

## Scope Definition
**Full 24/7 coverage of daily life**

### Activity Categories

#### Home Activities
- Morning routine (wake up, shower, breakfast)
- Chores (cleaning, cooking, laundry)
- Leisure (TV, reading, hobbies)
- Social (family, visitors)
- Sleep (bedtime, waking)

#### Work Activities
- Office work (meetings, focused work)
- Remote work (video calls, coding/writing)
- Commuting (driving, walking, transit)
- Work-related social (lunch, coffee with colleagues)

#### Social/Leisure
- Dining out
- Shopping
- Exercise (gym, running, climbing)
- Social gatherings (friends, events)
- Entertainment (movies, concerts)

#### Transitions
- Moving between locations
- Context changes (entering/leaving spaces)
- Activity transitions

## Challenges

### 1. Battery & Device
- Phone needs to charge overnight
- Continuous recording drains battery fast
- Solution: Intermittent recording + smart scheduling

### 2. Privacy Sensitivity
- Some activities are private (bathroom, intimate moments)
- Social contexts with others (others in frame)
- Work settings (confidential info on screen)
- Solution: User-defined privacy zones, automatic blur, user review

### 3. Data Volume
- 24 hours = potentially 24-48 GB of video
- Storage space limits
- Solution: Aggressive compression, on-device filtering

### 4. Annotation Difficulty
- Hard to label ground truth for full day
- Solution: Self-annotation, partial labeling, unsupervised methods

## Technical Feasibility

### Recording Strategy

#### Always-Collect Sensors (Low cost)
- ✅ IMU (accelerometer, gyroscope) - ~1-2% battery/day
- ✅ GPS/Location - ~3-5% battery/day
- ✅ Simple activity detection (standing, walking, driving)

#### Intermittent Sensors (Medium cost)
- ⚡ Audio: Record 30s every 5 minutes OR on voice detected
- ⚡ Video: Capture 10s every 10 minutes OR on motion/scene change

#### On-Demand Sensors (High cost)
- 🔴 Continuous video: Only during specific activities (work, exercise)

### Adaptive Recording

#### Context-Aware
- At home: More privacy, less frequent capture
- At work: More frequent (meetings), blur sensitive info
- Commuting: Motion-triggered capture
- Social: Ask permission before recording

#### Activity-Aware
- Sleeping: No video, minimal sensors
- Exercise: Continuous video (short duration)
- Work: Periodic screenshots (desktop activity)
- Social: User-controlled

## Privacy Strategy

### User Control
- Per-activity privacy settings
- "Privacy mode" toggle
- Review & delete before upload

### Automatic Protections
- Face blur (real-time)
- Text blur (screens, documents)
- Location obfuscation
- No audio in private spaces

### Ethical Considerations
- Informed consent for others in recordings
- Data deletion requests
- Transparency about what's recorded

## Success Metrics

### Coverage
- % of waking hours captured
- % of activity types represented
- % of locations visited

### Utility
- Activity recognition accuracy
- Memory retrieval relevance
- Agent improvement (task completion rate)

### Usability
- Battery impact (< 30% per day)
- Storage usage (< 2 GB/day after compression)
- User acceptance (survey/feedback)

---

*Last updated: 2026-02-09*
