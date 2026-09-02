# FDM Reliability Knowledge

## Purpose

研究 FDM 3D 打印机在长期运行、不同材料、不同环境和异常状态下的稳定性，并把可靠性从“用户反馈”提升为可分析的工程模型。

---

## 1. Reliability Model

```text
Design
  ↓
Manufacturing / Assembly
  ↓
Calibration
  ↓
Normal Operation
  ↓
Wear / Contamination / Drift
  ↓
Failure Detection
  ↓
Recovery / Service
```

可靠性不是单一的 MTBF，而是：

`Failure Prevention + Failure Detection + Failure Recovery + Serviceability`。

---

## 2. Major Failure Domains

| Domain | Typical Failures | Root Causes |
|---|---|---|
| Motion | layer shift, belt slip, skipped steps | tension, overload, resonance, wear |
| Extrusion | clog, jam, under-extrusion | heat creep, debris, gear wear, moisture |
| Hotend | leakage, clog, temperature fault | assembly, thermal design, contamination |
| Bed | adhesion failure, warping | surface, Z-offset, flatness, thermal uniformity |
| Thermal | overheating, unstable temperature | heater, sensor, PID, wiring |
| Electronics | reset, driver failure, communication loss | thermal stress, power, wiring, EMI |
| Sensors | false trigger, missed detection | contamination, alignment, noise |
| Software | crash, profile error, failed update | software defects, configuration, compatibility |
| Multi-material | failed load/unload, jams | path friction, material properties, cutter/feed mechanism |
| Vision | false alarm / missed defect | lighting, model limits, camera contamination |

---

## 3. Reliability by Lifecycle

### Setup

- Assembly correctness
- Factory calibration
- First-layer success
- Firmware initialization

### Normal Printing

- Temperature stability
- Extrusion consistency
- Motion repeatability
- Filament handling

### Long-Run Printing

- Belt / bearing / lead-screw wear
- Hotend contamination
- Fan degradation
- Sensor drift
- Cable fatigue

### Recovery

- Power-loss recovery
- Filament runout recovery
- Pause / resume
- Failure detection
- Safe shutdown

### Service

- Nozzle replacement
- Hotend replacement
- Belt tensioning
- Build plate replacement
- Toolhead / sensor replacement
- Firmware recovery

---

## 4. Reliability Engineering Chain

For each failure, investigate:

```text
Failure Mode
   ↓
Trigger / Stress
   ↓
Physical Root Cause
   ↓
Detection Method
   ↓
Protection / Mitigation
   ↓
Recovery
   ↓
Service Cost / Downtime
```

避免只记录“用户说容易堵头”，而应追踪到可能的热设计、材料、装配、公差或控制因素，并区分证据等级。

---

## 5. Reliability Metrics

可关注：

- Failure rate
- MTBF / MTTF（若有可靠数据）
- First-print success rate
- Long-duration print success rate
- Calibration drift
- Recovery success rate
- Service interval
- Replacement frequency
- Downtime
- Warranty return rate

社区样本可以作为 **Reported** evidence，但不能直接当作统计意义上的 failure rate。

---

## 6. Reliability vs Automation

自动化可能同时提升和降低可靠性：

```text
More Sensors / More Automation
          ↓
Less Manual Calibration
          ↓
Better OOBE

BUT

More Components / More Software Dependencies
          ↓
More Failure Modes
```

因此应同时评价：

- User-facing reliability
- System complexity
- Diagnostic capability
- Serviceability

---

## 7. Reliability Evaluation Matrix

| Dimension | Question |
|---|---|
| Mechanical | 长期运动后是否保持精度？ |
| Thermal | 长时间高温运行是否稳定？ |
| Extrusion | 不同材料下是否容易堵塞/打滑？ |
| Electrical | 电源、驱动和连接是否可靠？ |
| Sensor | 是否存在误报、漏报或漂移？ |
| Software | 更新、断电、异常状态是否稳定？ |
| Recovery | 故障后能否安全恢复？ |
| Serviceability | 用户能否快速定位并更换故障件？ |
| Ecosystem | 材料、profile、云服务依赖是否产生额外故障？ |

---

## 8. Evidence Rules

可靠性证据按优先级：

1. 厂商维修手册、可靠性数据、召回/服务公告
2. 长期专业测试与多台样机测试
3. 大规模用户反馈
4. 社区单点案例

特别注意：

- 单个失败案例 ≠ 普遍故障
- 没有用户投诉 ≠ 高可靠性
- 保修政策 ≠ 可靠性数据
- “24/7 printing” ≠ 已证明的长期可靠性
