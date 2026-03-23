# Weekend Development Plan (Mar 21-22, 2026)

**Goal:** Complete Minimum Viable Pipeline in 2 days (16-20 hours total)
**MVP Definition:** Camera → Preprocessing → VLM → Memory write (end-to-end data flow)

---

## Schedule Overview

| Day | Hours | Focus | Deliverable |
|-----|-------|-------|-------------|
| **Saturday** | 8-10h | Layer 1 + 1.5 | Frame capture + preprocessing |
| **Sunday** | 8-10h | Layer 2 + 3 | VLM inference + memory integration |

---

## Saturday: Layer 1 + 1.5 (Capture & Preprocessing)

### Morning (4-5h): iOS App Foundation

**09:00 - 11:00 (2h) Project Setup**
- [ ] Create iOS app project (Swift, minimum iOS 15)
- [ ] Add permissions: Camera, Microphone, Motion
- [ ] Test basic camera capture (AVCaptureSession)
- [ ] Create data models (Frame + Metadata struct)
- [ ] **Deliverable:** App can capture single frame

**11:00 - 13:00 (2h) Adaptive Interval Capture**
- [ ] Implement capture timer (start with fixed 15s interval)
- [ ] Add frame buffer (array of Frame objects)
- [ ] Write frames to temporary directory
- [ ] Test: capture 10 frames, verify timestamps
- [ ] **Deliverable:** Continuous capture at fixed interval

**13:00 - 14:00: LUNCH BREAK 🍱**

### Afternoon (4-5h): Preprocessing

**14:00 - 16:00 (2h) Frame Filters**
- [ ] Black frame detection (OpenCV or simple pixel check)
- [ ] Blur detection (Laplacian variance threshold)
- [ ] Pixel similarity deduplication (compare adjacent frames)
- [ ] Test filters with sample frames
- [ ] **Deliverable:** Filter pipeline removes junk frames

**16:00 - 18:00 (2h) Batch Boundary**
- [ ] Implement max window timeout (10 min force cut)
- [ ] Simple batch creation: group frames by time window
- [ ] Select top-K frames (K=6, random selection for now)
- [ ] **Deliverable:** Batches of filtered frames ready for VLM

**18:00 - 19:00 (1h) Integration Test**
- [ ] Run app for 30 min test session
- [ ] Verify: capture → filter → batch pipeline
- [ ] Count: how many frames captured, filtered, batched
- [ ] **Deliverable:** Working Layer 1 + 1.5

---

## Sunday: Layer 2 + 3 (Inference & Memory)

### Morning (4-5h): VLM Integration

**09:00 - 11:00 (2h) VLM API Setup**
- [ ] Choose VLM provider (Claude or GPT-4V)
- [ ] Get API key, test connection
- [ ] Create VLM client class
- [ ] Test: send 1 frame with prompt, get response
- [ ] **Deliverable:** VLM API working

**11:00 - 13:00 (2h) Batch Inference**
- [ ] Design prompt (use template from design-space doc)
- [ ] Implement batch → VLM call
- [ ] Parse structured output (activity, location, objects, etc.)
- [ ] Test with 3 sample batches
- [ ] **Deliverable:** Batch → structured text output

**13:00 - 14:00: LUNCH BREAK 🍱**

### Afternoon (4-5h): Memory Integration

**14:00 - 16:00 (2h) Memory Write**
- [ ] Create `memory/physical-logs/` directory structure
- [ ] Write function: append batch output to `YYYY-MM-DD.md`
- [ ] Format: timestamp header + markdown paragraph
- [ ] Test: write 5 batch outputs, verify file format
- [ ] **Deliverable:** VLM output written to memory files

**16:00 - 18:00 (2h) Memory Integration**
- [ ] Verify `memory_search` indexes new files
- [ ] Test retrieval: search for a keyword from captured data
- [ ] Create `agent:bootstrap` hook (inject physical-pattern.md)
- [ ] Extend AGENTS.md (read physical-insights at session start)
- [ ] **Deliverable:** OpenClaw can search physical-world data

**18:00 - 19:00 (1h) End-to-End Test**
- [ ] Run app for 1 hour test session
- [ ] Capture → Filter → Batch → VLM → Memory
- [ ] Query OpenClaw: "What was I doing at [time]?"
- [ ] Verify: agent retrieves relevant physical context
- [ ] **Deliverable:** Working MVP pipeline

---

## MVP Success Criteria

**Must Have (P0):**
- [ ] iOS app captures frames at adaptive intervals
- [ ] Frame filters remove black/blur/duplicate frames
- [ ] Batches created with max window timeout
- [ ] VLM receives batch, returns structured output
- [ ] Output written to `memory/physical-logs/`
- [ ] OpenClaw `memory_search` retrieves physical context

**Nice to Have (P1 - Defer to Next Sprint):**
- [ ] Audio VAD trigger
- [ ] IMU motion state detection
- [ ] SSIM batch boundary verification
- [ ] Frame importance scoring
- [ ] Nightly summarization job
- [ ] physical-insights/ + physical-pattern.md

**Out of Scope This Weekend:**
- [ ] Audio transcription
- [ ] Speaker count
- [ ] Embedding similarity (upgrade from SSIM)
- [ ] Prompt iteration
- [ ] Parameter tuning (max_interval, SSIM threshold, etc.)

---

## Technical Stack

**iOS App:**
- Language: Swift
- Minimum iOS: 15.0
- Frameworks: AVFoundation, CoreMotion, Vision (for blur detection)
- Dependencies: None (pure Swift)

**Preprocessing:**
- Frame filters: Pure Swift or OpenCV (via CocoaPods if needed)
- Start with simple implementations, optimize later

**VLM:**
- Provider: Claude 3.5 Sonnet (via Anthropic API) or GPT-4V (via OpenAI API)
- SDK: Native HTTP or OpenAI/Anthropic Swift SDK

**Memory Integration:**
- Target: `/Users/mia/.openclaw/workspace/memory/`
- Format: Markdown files with timestamp headers
- Integration: Direct file write (no OpenClaw code modification)

**OpenClaw Extensions:**
- Hook location: `~/.openclaw/hooks/agent-bootstrap.ts`
- AGENTS.md: `/Users/mia/.openclaw/workspace/AGENTS.md`

---

## Implementation Notes

### Layer 1: Capture

**Adaptive Interval Logic:**
```swift
class CaptureController {
    var currentInterval: TimeInterval = 15.0  // start at max
    let minInterval: TimeInterval = 3.0
    let maxInterval: TimeInterval = 15.0
    
    func onTimerFired() {
        captureFrame()
        
        // Ramp-up logic
        if noTriggerSinceLastCapture {
            currentInterval = min(currentInterval + 2.0, maxInterval)
        }
        scheduleNextCapture(after: currentInterval)
    }
    
    func onTriggerFired() {
        currentInterval = minInterval
        captureFrame()
        scheduleNextCapture(after: currentInterval)
    }
}
```

**Frame Buffer:**
```swift
struct Frame {
    let timestamp: Date
    let image: UIImage
    let audioTags: AudioTags?
    let imuTags: IMUTags?
    let currentInterval: TimeInterval
}

struct AudioTags {
    let noiseLevel: String  // "quiet" | "moderate" | "loud"
    let speechDetected: Bool
}

struct IMUTags {
    let motionState: String  // "stationary" | "sustained_motion"
}

class FrameBuffer {
    var frames: [Frame] = []
    let maxWindow: TimeInterval = 600  // 10 minutes
    
    func addFrame(_ frame: Frame) {
        frames.append(frame)
        
        // Check max window
        if let firstFrame = frames.first,
           frame.timestamp.timeIntervalSince(firstFrame.timestamp) >= maxWindow {
            createBatch()
        }
    }
    
    func createBatch() {
        let batch = filterAndSelectFrames(frames)
        sendToVLM(batch)
        frames.removeAll()
    }
}
```

### Layer 1.5: Preprocessing

**Filter Pipeline:**
```swift
func filterFrames(_ frames: [Frame]) -> [Frame] {
    return frames
        .filter { !isBlackFrame($0) }
        .filter { !isBlurryFrame($0) }
        .deduplicated(by: pixelSimilarity)
}

func selectTopK(_ frames: [Frame], k: Int = 6) -> [Frame] {
    // For MVP: random selection
    // For later: importance scoring
    return Array(frames.shuffled().prefix(k))
}

func isBlackFrame(_ frame: Frame) -> Bool {
    // Simple check: average pixel brightness < threshold
    guard let cgImage = frame.image.cgImage else { return true }
    // ... pixel analysis
    return averageBrightness < 10  // threshold
}

func isBlurryFrame(_ frame: Frame) -> Bool {
    // Laplacian variance
    guard let cgImage = frame.image.cgImage else { return true }
    // ... OpenCV or Vision framework
    return laplacianVariance < 100  // threshold
}
```

### Layer 2: VLM Inference

**Prompt Template:**
```
You are analyzing key frames from an egocentric camera worn by a user.

Time range: [start_time] to [end_time]
Frames: [4-8 images with timestamps]
Audio tags: [noise_level, speech_detected per frame]
IMU tags: [motion_state per frame]

Task: Describe what the user is doing and what this reveals about their habits, preferences, environment, or current activity that a personal AI agent should know.

Output format (structured, use "not observed" if unsure):
- Activity: [what the user is doing]
- Location: [where they are]
- Objects: [notable objects visible]
- Social context: [alone, small group, crowd, not observed]
- Notable events: [any notable changes or events]
- Additional notes: [other relevant observations]

Be concise. One short paragraph (4-6 sentences).
```

**API Call:**
```swift
func sendBatchToVLM(_ batch: [Frame]) async throws -> VLMResponse {
    let images = batch.map { $0.image }
    let prompt = buildPrompt(from: batch)
    
    let response = try await vlmClient.analyze(
        images: images,
        prompt: prompt
    )
    
    return parseStructuredOutput(response)
}
```

### Layer 3: Memory Write

**File Format:**
```markdown
# 2026-03-21 Physical Logs

## 14:30:00 - 14:40:00

**Activity:** Working at desk
**Location:** Home office
**Objects:** Laptop, coffee cup, notebook, headphones
**Social context:** Alone
**Notable events:** Switched from coding to email around 14:35
**Additional notes:** User appears focused, typing consistently. Coffee cup nearly empty. Natural light from window.

---

## 14:40:00 - 14:50:00

[Next batch...]

```

**Write Function:**
```swift
func writeToMemory(_ response: VLMResponse, for batch: [Frame]) {
    let dateFormatter = ISO8601DateFormatter()
    let date = batch.first!.timestamp
    let fileName = dateFormatter.string(from: date).prefix(10) + ".md"
    let filePath = "/Users/mia/.openclaw/workspace/memory/physical-logs/\(fileName)"
    
    var content = ""
    if !FileManager.default.fileExists(atPath: filePath) {
        content = "# \(fileName.dropLast(3)) Physical Logs\n\n"
    }
    
    let timeRange = "\(formatTime(batch.first!.timestamp)) - \(formatTime(batch.last!.timestamp))"
    content += "## \(timeRange)\n\n"
    content += formatVLMResponse(response)
    content += "\n---\n\n"
    
    // Append to file
    if let fileHandle = FileHandle(forWritingAtPath: filePath) {
        fileHandle.seekToEndOfFile()
        fileHandle.write(content.data(using: .utf8)!)
        fileHandle.closeFile()
    } else {
        try content.write(toFile: filePath, atomically: true, encoding: .utf8)
    }
}
```

---

## Testing Checklist

**Layer 1: Capture**
- [ ] Camera permissions granted
- [ ] Frames captured at correct intervals
- [ ] Timestamps accurate
- [ ] Frame buffer grows as expected
- [ ] Max window triggers batch creation

**Layer 1.5: Preprocessing**
- [ ] Black frames filtered (test: cover camera, verify no black frames in output)
- [ ] Blurry frames filtered (test: walk while capturing, verify sharp frames only)
- [ ] Duplicates removed (test: point at static scene, verify 1 frame per batch)
- [ ] Batch size reasonable (4-8 frames)

**Layer 2: VLM**
- [ ] API key works
- [ ] Prompt format correct
- [ ] Structured output parsed successfully
- [ ] Output quality reasonable (spot check)

**Layer 3: Memory**
- [ ] Files created in correct directory
- [ ] Markdown format valid
- [ ] `memory_search` finds keywords from captured data
- [ ] OpenClaw agent can retrieve context

**End-to-End**
- [ ] Run for 1 hour continuous
- [ ] Verify: no crashes, memory leak, battery drain acceptable
- [ ] Query agent: "What was I doing at [time]?"
- [ ] Agent response includes physical context from captured data

---

## Risk Mitigation

**Risk 1: VLM API rate limits**
- Mitigation: Start with low capture rate (15s max interval)
- Fallback: Switch to lower-cost model for MVP

**Risk 2: Battery drain**
- Mitigation: Test early, optimize capture frequency
- Fallback: Use iPhone plugged in during testing

**Risk 3: Storage bloat**
- Mitigation: Delete raw frames after batch creation
- Keep only: key frames (4-8 per batch) + text output

**Risk 4: OpenClaw integration issues**
- Mitigation: Test with simple example file first
- Fallback: Manual file write, verify search works

**Risk 5: Time overrun**
- Mitigation: Focus on P0 only, defer P1 to next sprint
- Scope: Adaptive interval can start as fixed interval

---

## Post-Weekend Next Steps

**If MVP Complete:**
1. Monday (Mar 23): Test extended session (4-6 hours)
2. Tuesday-Wednesday: Add Audio VAD + IMU triggers
3. Thursday-Friday: Nightly summarization job
4. Weekend (Mar 28-29): Parameter tuning + prompt iteration
5. Monday (Mar 30): Begin 2-week formal experiment

**If MVP Incomplete:**
1. Monday: Finish remaining P0 tasks
2. Tuesday: Integration testing
3. Wednesday-Thursday: Begin Audio/IMU if time permits
4. Friday: Assess readiness for experiment

---

## Success Metrics

**Technical:**
- [ ] Pipeline runs for 1 hour without crash
- [ ] Captures ≥20 frames per hour (after filtering)
- [ ] VLM produces ≥1 batch per 15 min
- [ ] Memory files written successfully
- [ ] Agent retrieves relevant context

**Functional:**
- [ ] Agent can answer "What was I doing at [time]?"
- [ ] Answer includes physical context (location, activity, objects)
- [ ] Information not available from digital traces alone

**Schedule:**
- [ ] Saturday: Layer 1 + 1.5 complete
- [ ] Sunday: Layer 2 + 3 complete
- [ ] Sunday EOD: End-to-end test successful

---

**Created:** 2026-03-20
**Target Completion:** 2026-03-22 19:00 EST
**Total Time Budget:** 16-20 hours
