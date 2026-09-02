# FDM Vision Systems Knowledge

## Purpose

研究摄像头、机器视觉、边缘 AI 和视觉闭环在 FDM 打印机中的作用，并区分监控、检测、诊断与真正的控制反馈。

---

## 1. Vision Architecture

```text
Camera
  ↓
Optics / Lighting
  ↓
ISP / Image Processing
  ↓
Feature Extraction / Model
  ↓
Defect / State Estimation
  ↓
Alert / Decision
  ↓
(Optional) Machine Command
```

只有最后一步真正改变打印参数或机器动作时，才能称为视觉闭环控制。

---

## 2. Function Taxonomy

| Function | Input | Output | Control Level |
|---|---|---|---|
| Remote Monitoring | Video | User view | None |
| Timelapse | Video | Video | None |
| Spaghetti Detection | Image / Video | Failure classification | Usually alert / pause |
| First-Layer Inspection | Bed image | Quality classification | Alert / possible pause |
| Print Progress Detection | Image | State estimate | Monitoring |
| Defect Diagnosis | Image + context | Failure category | Monitoring / service |
| Vision Calibration | Image | Calibration parameter | Closed-loop if applied automatically |
| Vision-guided Printing | Image + model | Machine command | Closed-loop |

---

## 3. Camera Monitoring

Typical uses:

- Remote observation
- Timelapse
- Print progress
- Manual troubleshooting
- Security / access monitoring

Low-cost camera monitoring should not be confused with AI or closed-loop printing.

---

## 4. First-Layer Inspection

Potential defects:

- Poor adhesion
- Missing extrusion
- Under-extrusion
- Over-extrusion
- Warping
- Nozzle drag
- Incorrect Z-offset

Engineering challenges:

- Lighting consistency
- Bed reflection
- PEI texture variation
- Filament color / translucency
- Camera angle
- Model geometry
- False positives

---

## 5. Spaghetti / Failure Detection

Typical pipeline:

```text
Camera
  ↓
Frame Sampling
  ↓
Region / Feature Analysis
  ↓
Classifier / Detection Model
  ↓
Confidence Score
  ↓
Pause / Alert / Continue
```

研究时必须确认：

- Detection target
- Sampling frequency
- Model type
- On-device vs cloud inference
- Confidence threshold
- False-positive / false-negative behavior
- Whether detection automatically pauses the print

---

## 6. Edge AI vs Cloud AI

| Dimension | Edge | Cloud |
|---|---|---|
| Latency | Low | Network dependent |
| Connectivity | Can work offline | Required for inference |
| Privacy | Higher | Lower |
| Compute | Local hardware | Server |
| Update | Firmware/model OTA | Central model update |
| BOM | Higher | Lower local BOM |

不要仅凭“AI camera”判断推理发生位置。

---

## 7. Sensor Fusion

现代打印机可能同时使用：

```text
Camera
 +
Accelerometer
 +
Bed / Z Sensor
 +
Filament Sensor
 +
Temperature Sensor
      ↓
State Estimation
      ↓
Calibration / Detection / Control
```

研究重点是数据是否真正融合，以及融合结果是否影响机器行为。

---

## 8. Closed-Loop Vision

定义：

`Vision Measurement → State / Error → Algorithm → Machine Command → New State`

例如：

- 检测首层异常 → 自动调整 Z / 流量 → 再次测量
- 检测严重失败 → 自动暂停
- 检测打印状态 → 动态修改工艺参数

如果系统只“识别并通知用户”，应标记为 **monitoring / detection**，而不是闭环控制。

---

## 9. Evaluation Dimensions

| Dimension | Questions |
|---|---|
| Image Quality | resolution, frame rate, focus, lighting |
| Detection | accuracy, precision, recall, false alarms |
| Compute | edge / cloud / NPU / CPU |
| Latency | detection-to-action delay |
| Integration | firmware / cloud / app integration |
| Control | 是否真正修改机器状态？ |
| Reliability | 不同模型、颜色、光照下是否稳定？ |
| Privacy | image storage / transmission policy |

---

## 10. Evidence Rules

厂商宣传“AI、智能监测、视觉闭环”时，应至少建立：

`Camera → Data → Model/Algorithm → Decision → Machine Response`

缺失其中关键环节时，不应推断为完整闭环系统。
