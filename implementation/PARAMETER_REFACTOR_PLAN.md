# SpaceSelfLog 参数重构计划

## 当前状态：Experiment 1/2/3

| Experiment | 功能 | Prompt |
|------------|------|--------|
| **Exp 1** | 单词 -ing | "What am I doing? Single -ing word." |
| **Exp 2** | 带历史continuity | "Considering previous labels: [...], continue the sequence." |
| **Exp 3** | JSON schema | `{objects, location, handsInTheView, activityLabel}` |

**问题：** 这些是AI分析模式，不是真正的**实验参数**

---

## 新设计：基于 Thesis Implementation Plan

### **核心理念：三层参数体系**

```
Layer 1: Capture (采集)
  ↓
Layer 1.5: Preprocess (预处理)
  ↓
Layer 2: Inference (推理)
  ↓
Layer 3: Memory (存储)
```

---

## 新参数设计

### **Layer 1: Capture Parameters**

| 参数 | 类型 | 默认值 | 可选值 | 说明 |
|------|------|--------|--------|------|
| `captureMode` | enum | `.adaptive` | `.fixed`, `.adaptive` | 采集模式 |
| `maxInterval` | Int | 15 | 10, 15, 20, 30 | 最大间隔（秒） |
| `minInterval` | Int | 3 | 1, 2, 3, 5 | 最小间隔（秒） |
| `rampUpSteps` | [Int] | [3, 5, 8, 15] | 自定义 | Ramp-up曲线（秒） |

**行为：**
- **Fixed mode:** 固定间隔采集（例如每15秒1帧）
- **Adaptive mode:**
  - 默认：maxInterval (15s)
  - 触发（VAD/motion）→ minInterval (3s)
  - 无触发 → 逐步ramp up: 3s → 5s → 8s → 15s

---

### **Layer 1.5: Preprocessing Parameters**

| 参数 | 类型 | 默认值 | 可选值 | 说明 |
|------|------|--------|--------|------|
| `maxWindow` | Int | 600 | 300, 600, 900 | 批次窗口（秒） |
| `targetFramesPerBatch` | Int | 6 | 4, 6, 8 | 每批次目标帧数 |
| `enableBlackFilter` | Bool | true | - | 黑帧过滤 |
| `enableBlurFilter` | Bool | true | - | 模糊帧过滤 |
| `blurThreshold` | Double | 100.0 | 50-200 | 模糊阈值 |
| `enableDeduplication` | Bool | true | - | 去重 |
| `similarityThreshold` | Double | 0.95 | 0.8-0.99 | 相似度阈值 |

**批次逻辑：**
1. 触发或max window超时 → 创建批次
2. 应用filters (black → blur → dedup)
3. Importance scoring (MVP阶段可选)
4. Select top-K frames

---

### **Layer 2: Inference Parameters**

| 参数 | 类型 | 默认值 | 可选值 | 说明 |
|------|------|--------|--------|------|
| `vlmProvider` | enum | `.gemini` | `.gemini`, `.openRouter`, `.claude`, `.gpt4v` | VLM提供商 |
| `batchInference` | Bool | true | - | 批量推理（4-8帧）|
| `includePriorBatch` | Bool | true | - | 包含上一批次摘要 |
| `structuredOutput` | Bool | true | - | 结构化输出 |

**Prompt设计（基于design-space-updated.md）：**

```
You are analyzing key frames from an egocentric camera.

Time range: [start] to [end]
Frames: [4-8 images with timestamps]
Audio tags: [noise_level, speech_detected]
IMU tags: [motion_state]

Task: Describe what the user is doing and what this reveals about
their habits, preferences, environment, or current activity that
a personal AI agent should know.

Output format (structured, use "not observed" if unsure):
{
  "activity": "[what the user is doing]",
  "location": "[where they are]",
  "objects": ["notable objects"],
  "social_context": "[alone, small group, crowd, not observed]",
  "notable_events": "[changes or events]",
  "additional_notes": "[other observations]"
}

Be concise. 4-6 sentences.
```

---

### **Layer 3: Memory Parameters**

| 参数 | 类型 | 默认值 | 可选值 | 说明 |
|------|------|--------|--------|------|
| `memoryPath` | String | `/Users/mia/.openclaw/workspace/memory/physical-logs/` | - | 存储路径 |
| `retentionDays` | Int | 14 | 7, 14, 30 | 保留天数 |
| `enableNightlySummary` | Bool | true | - | 每晚摘要 |
| `enablePatternFile` | Bool | true | - | 模式文件 |

**文件结构：**
```
memory/
├── physical-logs/
│   ├── 2026-03-21.md
│   └── 2026-03-22.md
├── physical-insights/
│   ├── 2026-03-21.md
│   └── 2026-03-22.md
└── physical-pattern.md
```

---

## UI 重构方案

### **当前 UI (Experiment 1/2/3)**

```
┌─────────────────────────┐
│  Select Experiment      │
│  [1] [2] [3]           │
│                         │
│  AI Settings            │
│  API Key: [________]   │
│  Interval: [30] sec    │
└─────────────────────────┘
```

### **新 UI (三层参数)**

```
┌─────────────────────────────────────┐
│  Capture Settings                    │
│  Mode: [Fixed | Adaptive]           │
│  Max Interval: [15] sec             │
│  Min Interval: [3] sec              │
│                                      │
│  Preprocessing Settings              │
│  Batch Window: [10] min             │
│  Target Frames: [6] per batch       │
│  Filters:                            │
│    ☑ Black frame filter             │
│    ☑ Blur filter (threshold: 100)  │
│    ☑ Deduplication (0.95)          │
│                                      │
│  Inference Settings                  │
│  VLM Provider: [Gemini ▼]          │
│  ☑ Batch inference (4-8 frames)    │
│  ☑ Include prior batch context     │
│  ☑ Structured output               │
│                                      │
│  Memory Settings                     │
│  Path: /Users/.../physical-logs/    │
│  Retention: [14] days               │
│  ☑ Nightly summary                  │
│  ☑ Pattern file                     │
└─────────────────────────────────────┘
```

---

## 数据模型

### **新 Swift Structs**

```swift
// MARK: - Capture Settings
struct CaptureSettings {
    var mode: CaptureMode = .adaptive
    var maxInterval: TimeInterval = 15.0
    var minInterval: TimeInterval = 3.0
    var rampUpSteps: [TimeInterval] = [3, 5, 8, 15]
}

enum CaptureMode: String, CaseIterable {
    case fixed = "Fixed"
    case adaptive = "Adaptive"
}

// MARK: - Preprocessing Settings
struct PreprocessingSettings {
    var maxWindow: TimeInterval = 600.0  // 10 min
    var targetFramesPerBatch: Int = 6
    var enableBlackFilter: Bool = true
    var enableBlurFilter: Bool = true
    var blurThreshold: Double = 100.0
    var enableDeduplication: Bool = true
    var similarityThreshold: Double = 0.95
}

// MARK: - Inference Settings
struct InferenceSettings {
    var vlmProvider: VLMProvider = .gemini
    var batchInference: Bool = true
    var includePriorBatch: Bool = true
    var structuredOutput: Bool = true
}

enum VLMProvider: String, CaseIterable {
    case gemini = "Gemini"
    case openRouter = "OpenRouter"
    case claude = "Claude"
    case gpt4v = "GPT-4V"
}

// MARK: - Memory Settings
struct MemorySettings {
    var basePath: String = "/Users/mia/.openclaw/workspace/memory/physical-logs/"
    var retentionDays: Int = 14
    var enableNightlySummary: Bool = true
    var enablePatternFile: Bool = true
}
```

---

## 实施计划

### **Step 1: 删除 Experiment 1/2/3**

**要删除：**
- `ExperimentModes.swift` (整个文件)
- `AppViewModel` 中的 `experimentNumber` 属性
- `ContentView` 中的 Experiment 选择 UI
- `AIAnalysisManager` 中的 Experiment 相关逻辑

**要保留：**
- `FormattedOutput` struct (依然有用)
- 基础 prompt 模板逻辑

---

### **Step 2: 新增 Settings Models**

**新文件：**
- `CaptureSettings.swift`
- `PreprocessingSettings.swift`
- `InferenceSettings.swift`
- `MemorySettings.swift`

**集成到 AppViewModel：**
```swift
@Published var captureSettings = CaptureSettings()
@Published var preprocessingSettings = PreprocessingSettings()
@Published var inferenceSettings = InferenceSettings()
@Published var memorySettings = MemorySettings()
```

---

### **Step 3: 新增 UI**

**新文件：**
- `CaptureSettingsView.swift`
- `PreprocessingSettingsView.swift`
- `InferenceSettingsView.swift`
- `MemorySettingsView.swift`

**修改 ContentView：**
- 替换 Experiment 选择为 TabView
- 每个 tab 对应一个 settings view

---

### **Step 4: 更新 Web Dashboard**

**新增 API endpoints：**
- `GET /settings` - 获取所有设置
- `POST /settings/capture` - 更新 capture 设置
- `POST /settings/preprocessing` - 更新 preprocessing 设置
- `POST /settings/inference` - 更新 inference 设置
- `POST /settings/memory` - 更新 memory 设置

**修改 HTML UI：**
- 添加 settings 控制面板
- 实时更新参数

---

## MVP 阶段优先级

### **P0 (This Weekend)**

- [x] 删除 Experiment 1/2/3
- [ ] 创建新 Settings models
- [ ] 实现 basic UI (capture + inference settings)
- [ ] 更新 CameraManager (adaptive interval)
- [ ] 更新 AIAnalysisManager (batch inference)
- [ ] 实现 MemoryWriter

### **P1 (Next Week)**

- [ ] 完整 preprocessing settings
- [ ] Web dashboard 更新
- [ ] Import/export settings
- [ ] Preset profiles (快速切换配置)

### **P2 (Future)**

- [ ] Audio VAD trigger
- [ ] IMU motion trigger
- [ ] Nightly summarization
- [ ] Pattern file

---

## 测试计划

### **单元测试**

- [ ] CaptureSettings 默认值
- [ ] Adaptive interval logic
- [ ] Frame filtering pipeline
- [ ] Batch creation logic
- [ ] VLM prompt generation
- [ ] Memory file writing

### **集成测试**

- [ ] Capture → Preprocess → Batch
- [ ] Batch → VLM → Memory
- [ ] End-to-end (1 hour session)

### **UI 测试**

- [ ] Settings persistence
- [ ] Real-time updates
- [ ] Web dashboard control

---

**下一步：你想要我：**
1. ✅ **先删除 Experiment 1/2/3 代码**
2. 🆕 **创建新 Settings models**
3. 🎨 **设计新的 UI mockup**
4. 🚀 **直接开始实现**

**选哪个？** 🦞
