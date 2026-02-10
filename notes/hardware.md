# Hardware: Phone-Based Life Logging

## Device Choice: Smartphone
**Rationale:** 现有设备、多模态传感器、易开发、随身携带

## Available Sensors

### Visual (Camera)
- **Front camera:** Self-view (face expression, engagement)
- **Back camera:** World view (activities, environment)
- **Considerations:**
  - Battery drain
  - Privacy (blurring faces/text?)
  - Storage (video is large)
  - Background access restrictions (iOS/Android)

### Audio (Mic)
- **Ambient audio:** Context detection (office, cafe, home)
- **Speech recognition:** Conversations, commands
- **Considerations:**
  - Always-on vs triggered
  - Privacy (voice data)
  - Noise robustness

### Motion Sensors (IMU)
- **Accelerometer:** Movement patterns (walking, sitting, running)
- **Gyroscope:** Orientation, gestures
- **Considerations:**
  - Battery efficient (always OK)
  - Useful for activity detection
  - Limited semantic info alone

### Location (GPS/Location Services)
- **Place recognition:** Home, office, gym, cafe
- **Context:** Routine detection, commute patterns
- **Considerations:**
  - Battery drain
  - Privacy (sensitive info)

## Technical Implementation

### iOS (Swift/Combine)
- Background modes: `Background processing`, `Audio`, `Location updates`
- Camera capture: `AVFoundation`
- Sensor access: `CoreMotion`, `CLLocationManager`
- Challenges: Background execution limits, app lifecycle

### Android (Kotlin/Coroutines)
- Foreground service for continuous capture
- Camera2 API / CameraX
- SensorManager for IMU
- Advantages: More flexible background execution

## Data Collection Strategies

### Option 1: Continuous Recording
- Pros: No missing data
- Cons: Battery, storage, privacy concerns

### Option 2: Periodic Snapshots
- Capture every N minutes for M seconds
- Tradeoff: Less data, might miss events

### Option 3: Triggered Recording
- Trigger on motion, voice, location change
- Pros: Context-aware, efficient
- Cons: Complex logic, might miss slow events

### Option 4: Hybrid
- Always collect IMU (low cost)
- Periodic/triggered video+audio
- Best balance?

## Battery & Storage Estimates

### Battery (rough estimates)
- Continuous video: ~10-20% per hour
- Continuous audio: ~5-10% per hour
- IMU only: ~1-2% per hour

### Storage (rough estimates)
- Video (1080p@30fps): ~1-2 GB/hour
- Audio (128kbps): ~50-100 MB/hour
- IMU: ~1-5 MB/hour

### Compression Needs
- Video → keyframes + embeddings
- Audio → transcripts + embeddings
- IMU → activity summaries

## Privacy & Ethics

### User Control
- What to record (toggle per sensor)
- When to record (time windows, locations)
- Data deletion (local only)

### Data Minimization
- Blur faces, text
- On-device processing
- No cloud upload

## Prototype Plan

### Phase 1: MVP (Week 1-2)
- Simple app: periodic photo capture
- Local storage
- Basic activity tagging

### Phase 2: Multi-modal (Week 3-4)
- Add IMU logging
- Add audio capture
- Basic fusion

### Phase 3: Integration (Week 5+)
- Connect to understanding pipeline
- Connect to memory system
- Connect to agent

---

*Last updated: 2026-02-09*
