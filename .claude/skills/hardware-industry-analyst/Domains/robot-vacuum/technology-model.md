# Robot Vacuum Technology Model

> 本文件定义扫地机器人的技术架构与关键性能因果关系。具体技术知识见 `knowledge/`；通用评估方法见 `Frameworks/technology.md`。

---

## 1. System Architecture

```text
User / Schedule
      ↓
App / Task Planner
      ↓
Navigation + Mapping + Perception
      ↓
Motion / Cleaning Controller
      ↓
Drive + Fan + Brush + Mop + Pump
      ↓
Floor / Debris / Water Interaction
      ↓
Cleaning Result
      ↑
Sensors / Localization / Feedback
      ↓
Docking
      ↓
Empty / Wash / Dry / Refill
```

核心不是单独比较传感器、吸力或电池，而是判断感知、规划、运动、清洁执行和基站维护如何共同决定无人化程度。

## 2. Technology Layers

| Layer | Domain Module | Core Question | Knowledge Module |
|---|---|---|---|
| Navigation | Localization / SLAM / planning | 能否稳定定位、建图和覆盖？ | `navigation.md`, `mapping.md` |
| Cleaning | Vacuum / brush / mop | 能否有效处理不同地面与污物？ | `cleaning-systems.md` |
| Perception | Obstacle / cliff / surface sensing | 能否识别环境并改变行为？ | `sensors.md` |
| Control | Motion / task orchestration | 感知如何转化为实时动作？ | `firmware.md` |
| Dock | Charging / empty / wash / dry / refill | 能否减少人工维护？ | `base-station.md` |
| Software | App / maps / OTA / cloud | 用户如何配置、监控和恢复任务？ | `mapping.md`, `firmware.md` |
| Reliability | Sealing / wear / recovery | 长期运行是否稳定？ | `firmware.md`, `base-station.md` |

## 3. Performance Causal Model

### Autonomous Cleaning

```text
Sensor Quality
      ↓
Perception / Localization
      ↓
Map + State Estimation
      ↓
Path / Task Planning
      ↓
Motion Execution
      ↓
Coverage + Obstacle Recovery
      ↓
Effective Cleaning Coverage
```

### Cleaning Result

```text
Floor / Debris / Carpet
        ↓
Brush + Airflow + Mop Interaction
        ↓
Energy / Contact / Water Parameters
        ↓
Debris Pickup + Stain Removal + Edge Performance
        ↓
User-perceived Cleaning Quality
```

### Maintenance Autonomy

```text
Robot State
   ↓
Dock Detection
   ↓
Docking
   ↓
Empty / Wash / Dry / Refill
   ↓
Consumable / Water State
   ↓
Next Cleaning Cycle
```

## 4. Key Engineering Models

### Coverage Efficiency

Effective coverage depends on usable cleaning width, route efficiency, obstacle avoidance, recovery behavior and battery/runtime constraints; advertised cleaning area alone is insufficient.

### Airflow / Pickup

Cleaning performance should be decomposed into airflow path, pressure differential, brush agitation, debris characteristics and floor interaction. `Pa` is not a sufficient proxy for pickup performance.

### Energy Budget

```text
Battery Energy
 ├── Drive Motors
 ├── Vacuum Fan
 ├── Brush / Mop Actuation
 ├── Pumps / Heating
 └── Compute / Sensors / Communications
        ↓
Runtime / Covered Area / Return-to-Dock Margin
```

## 5. Subsystem Assessment Map

| Subsystem | Primary Metrics | Secondary Questions | Knowledge |
|---|---|---|---|
| Navigation | localization, coverage, route efficiency | recovery, multi-floor, low-light behavior | `navigation.md`, `mapping.md` |
| Cleaning | pickup, edge cleaning, hair handling | airflow, brush geometry, energy | `cleaning-systems.md` |
| Perception | obstacle detection / classification | false positives, lighting, transparency | `sensors.md` |
| Firmware | control latency, recovery, OTA | safety, fault handling | `firmware.md` |
| Base Station | docking, empty, wash, dry, refill | contamination, water path, noise | `base-station.md` |
| Software | setup, map editing, scheduling | cloud dependence, UX, privacy | `mapping.md`, `firmware.md` |

## 6. System Architecture Patterns

| Architecture | Key Components | Main Advantage | Main Cost / Risk | Typical Use |
|---|---|---|---|---|
| LiDAR-centric | Rotating LiDAR + IMU + wheel odometry | Strong geometric localization | Added height/cost, limited semantic perception | Mainstream/premium |
| Vision-centric | RGB/depth cameras + IMU/odometry | Rich semantic perception | Lighting and compute dependence | Advanced models |
| Hybrid | LiDAR + vision/depth + multiple sensors | Broad operating envelope | Higher BOM and software complexity | Flagship |
| Basic random / reactive | Bump / IR / simple range sensing | Low cost | Poor coverage and recovery | Entry |

## 7. Automation / Feedback Stack

```text
Sensor
  ↓
Measurement
  ↓
Perception / State Estimation
  ↓
Navigation / Cleaning Decision
  ↓
Motor / Fan / Pump Command
  ↓
Machine Response
  ↓
New Sensor State
```

应区分：
- Monitoring：记录状态但不改变控制。
- Adaptive control：测量结果改变实时参数或动作。
- Calibration：通过测量更新模型或参数。
- Closed-loop control：反馈持续参与控制回路。

## 8. Technical Trade-offs

1. **LiDAR vs Vision** → geometric robustness vs semantic richness / compute.
2. **Higher Suction vs Energy / Noise** → pickup potential vs runtime and acoustics.
3. **Rotary Mop vs Roller Mop** → cleaning behavior vs mechanical/fluidic complexity.
4. **More Sensors vs BOM** → broader perception vs cost and failure modes.
5. **Full-service Dock vs Footprint** → autonomy vs size, cost and maintenance complexity.
6. **Larger Battery vs Weight** → runtime vs mobility and charging requirements.

## 9. Technology Research Questions

1. What limits navigation reliability in the target environment?
2. Which sensor signals actually change robot behavior?
3. Which cleaning mechanism dominates performance for the target floor and debris?
4. How are navigation and cleaning policies coupled?
5. Which functions are local, cloud-assisted or cloud-dependent?
6. What is the real maintenance-autonomy ceiling of the base station?
7. Which components dominate BOM, reliability risk and service burden?
8. Which architectural choices are defensible versus rapidly commoditizing?

## 10. Knowledge Mapping

```text
Technology Model
│
├── Navigation → knowledge/navigation.md
├── Mapping / Planning → knowledge/mapping.md
├── Cleaning → knowledge/cleaning-systems.md
├── Perception → knowledge/sensors.md
├── Firmware / Control → knowledge/firmware.md
└── Dock / Maintenance → knowledge/base-station.md
```
