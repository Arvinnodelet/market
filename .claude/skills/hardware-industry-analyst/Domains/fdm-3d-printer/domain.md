# FDM / FFF 3D Printer Domain Model v3

## Metadata

- **Domain:** FDM / FFF 3D Printing
- **Scope:** Consumer / Prosumer / Professional Desktop
- **Primary Focus:** Product, Technology, Software, Materials, Manufacturing, Reliability, Ecosystem
- **Analysis Unit:** System Capability / Technology Cluster

## 1. Domain Definition

FDM/FFF 通过将热塑性材料加热至可流动状态，并沿数字模型生成的路径逐层沉积形成三维实体。

研究必须区分 Machine Capability、Material Capability、Process Capability、Software Capability、Workflow Capability 和 System Capability。

### Included
- Desktop FDM / FFF
- Consumer / Prosumer / Professional Desktop
- CoreXY / Bedslinger / CoreXZ / Delta / IDEX / Toolchanger
- Single / Multi-color / Multi-material
- Printer hardware, firmware, slicer, cloud, sensors, algorithms, materials, reliability

### Excluded
- Industrial-scale FDM market as a separate complete study
- SLA / MSLA / DLP / LCD
- SLS / SLM / DMLS
- Pure CAD software
- General robotics unrelated to FDM

---

# 2. Product Taxonomy

| Segment | Typical User | Main Differentiator |
|---|---|---|
| Entry / Budget | Beginner / Student | Price |
| Consumer | Family / Maker | Ease of use / automation |
| Prosumer | Advanced Maker / Studio | Speed / reliability / materials |
| Engineering Desktop | Engineer / Design Team | Accuracy / materials / stability |
| High-temperature / Enclosed | Engineering users | Chamber / thermal capability |
| Multi-material / Multi-color | Creator / Maker | Material and color workflow |
| Print Farm / Fleet | Small business | Uptime / remote management |

### Motion Architecture
Bedslinger / Cartesian · CoreXY · CoreXZ · H-bot · Delta · IDEX · Toolchanger / Multi-tool

### Material Classes
PLA / PETG · ABS / ASA · TPU / TPE · PA / PC · CF / GF composites · PPA / PPS / PEI and other high-performance polymers

---

# 3. Domain Workflow

```text
CAD / 3D Model
      ↓
Slicer / Profile
      ↓
Toolpath / G-code
      ↓
Firmware / Motion Planner
      ↓
┌───────────────┬────────────────┬────────────────┐
│ Motion        │ Extrusion      │ Thermal        │
└──────┬────────┴───────┬────────┴───────┬────────┘
       └────────────────┼─────────────────┘
                        ↓
                 Physical Process
                        ↓
                 Layer Deposition
                        ↓
                 Cooling / Bonding
                        ↓
                   Finished Part
                        ↓
              Inspection / Feedback
```

任何产品能力都应尽量落到具体流程节点、硬件、控制、算法、软件或材料机制。

---

# 4. System Architecture

```text
User / CAD
    ↓
Slicer / Profiles
    ↓
Host / Application
    ↓
Firmware / Control
    ↓
┌────────────┬────────────┬────────────┐
│ Motion     │ Extrusion  │ Thermal    │
└─────┬──────┴──────┬─────┴──────┬─────┘
      ↓             ↓             ↓
 Mechanics       Filament      Hotend / Bed
      └─────────────┼─────────────┘
                    ↓
               Printed Part
                    ↑
        Sensors / Vision / Feedback
```

研究时区分 data flow、control flow、energy flow、material flow、feedback loop。

---

# 5. Technology Taxonomy

| Layer | Subsystem | Primary Question |
|---|---|---|
| Process | Printing Principle | 材料如何沉积、结合？ |
| Mechanical | Motion System | 如何高速、稳定地运动？ |
| Mechanical | Structure | 如何提供刚度、对齐和热稳定性？ |
| Extrusion | Extruder | 如何稳定输送材料？ |
| Thermal | Hotend / Bed / Chamber | 如何建立稳定热场？ |
| Sensing | Sensors / Vision | 测量什么状态？ |
| Control | Motion / Extrusion / Thermal | 如何根据状态改变动作？ |
| Algorithm | Calibration / Compensation | 如何降低动态、几何和工艺误差？ |
| Compute | MCU / SoC / NPU | 如何执行实时计算？ |
| Software | Firmware / Slicer / Cloud | 如何连接用户与机器？ |
| Materials | Filament / Profiles | 工艺窗口由什么决定？ |
| Reliability | Failure / Recovery | 如何长期稳定运行？ |
| Ecosystem | AMS / ACE / Cloud / Community | 如何扩展 workflow？ |

---

# 6. Core Technology Clusters

FDM 产品研究优先从以下 Cluster 中选择与目标产品相关的 **2–4 个** 深挖：

### A — High-Speed Motion System
CoreXY / Cartesian + frame rigidity + motors/drivers + resonance sensing + input shaping + motion control → usable high-speed motion capability。

### B — Closed-Loop Extrusion
Extrusion pressure/flow + motor/current/position sensing + estimation + control + extruder/hotend → stable material deposition。

### C — Automated Calibration / Sensing
Sensor/vision → state measurement → calibration/estimation → firmware control → reduced manual intervention。

### D — Multi-Material / Multi-Color
Identification/storage + feed + switching/toolhead + purge/waste management + profiles/software → multi-material workflow capability。

### E — Thermal / Engineering Material Platform
Hotend + heater + build plate + enclosure/chamber + airflow + material profiles → validated material process window。

### F — Intelligent Monitoring / Recovery
Camera/sensors + edge compute + detection + firmware/cloud → failure detection / intervention / recovery。

选择 Cluster 必须基于产品证据，而不是机械套用。

---

# 7. Domain Capability Model

```text
Component
 ↓
Subsystem
 ↓
Technology Cluster
 ↓
Physical Capability
 ↓
Process Capability
 ↓
Workflow Capability
 ↓
User / Economic Value
```

例如：

```text
Accelerometer
 + Motion Model
 + Input Shaping
 + High-Rigidity Frame
 ↓
Vibration Compensation Capability
 ↓
Higher Usable Acceleration
 ↓
Shorter Stable Print Cycle
```

因此不能从“装了加速度计”直接得出“高速能力领先”。

---

# 8. Key Benchmarks

## Print Quality
Dimensional accuracy · repeatability · first-layer consistency · surface quality · layer consistency · overhang/bridging · ringing/ghosting · layer adhesion · small-feature reproduction

## Productivity
Maximum motion speed · sustained print speed · volumetric flow · acceleration · cycle time · material throughput · fleet utilization / uptime

> Maximum speed ≠ sustained production speed.

## Thermal
Nozzle temperature · stable volumetric flow · bed temperature · chamber temperature · thermal uniformity · warm-up time · thermal stability

> Maximum temperature ≠ validated material capability.

## Motion
Positioning accuracy · repeatability · acceleration · rigidity · resonance · vibration · usable speed under quality constraints

## Extrusion
Maximum stable flow · extrusion force · retraction · filament path reliability · soft-material handling · switching behavior

## Automation
Auto bed leveling · Z-offset · flow calibration · resonance identification · toolhead calibration · failure detection · recovery · remote monitoring

> Sensor presence ≠ closed-loop control.

## Materials
Nominal support · validated profiles · chamber requirement · drying requirement · environmental sensitivity · long-term reliability

> Supported material ≠ validated workflow.

## Economics
ASP · consumable cost · purge waste · maintenance · labor intervention · cost per printed part · fleet utilization

---

# 9. Domain-Specific Analysis Questions

### Motion
为什么选择该架构？moving mass 如何影响动态性能？主要刚度和共振模式在哪里？input shaping 是补偿还是能力放大器？速度上限受机械、控制还是挤出限制？

### Extrusion / Thermal
最大稳定流量由什么决定？挤出压力如何产生？最大温度是否对应稳定高流量？chamber 是否真正改变材料工艺窗口？

### Sensors / Control
测量对象是什么？传感器在哪里？采样 / 重复性如何？是 monitoring、calibration 还是 closed loop？测量是否改变 actuator command？

### Software / Algorithms
input shaping / pressure advance / flow calibration 如何工作？参数来自测量、估计还是人工输入？vision 是检测还是控制？算法运行在 MCU、SoC、host 还是 cloud？

### Multi-Material
换料路径如何实现？切换时间和 purge waste 如何影响真实 throughput？材料识别是否进入控制闭环？硬件和软件是否形成统一 workflow？

### Reliability
主要 field failure modes 是什么？哪些故障可以被检测？能否自动恢复？维护是否需要拆机？高频故障是否由架构本身产生？

---

# 10. Standard Trade-offs

| Trade-off | Benefit | Cost / Risk |
|---|---|---|
| Higher speed vs quality | Throughput | vibration / thermal / extrusion limits |
| Higher flow vs thermal margin | Productivity | incomplete melting / pressure instability |
| Larger build volume vs rigidity | Application range | mass / stiffness / cost |
| Enclosure vs thermal complexity | Engineering materials | heat management / cost |
| Open architecture vs integration | Modularity | setup burden |
| Multi-material vs waste | Workflow flexibility | purge / switching complexity |
| More sensors vs simplicity | Automation | BOM / calibration / failure modes |
| More compute vs cost | AI / control | power / software complexity |
| Toolchanger vs fixed multi-nozzle | Material separation | mechanism / calibration complexity |

所有核心技术都必须结合具体产品分析 Trade-off。

---

# 11. Competitive Comparison Rules

比较尽量标准化 material、nozzle diameter、layer height、environment、model geometry、print profile、test method、measurement method。

重点比较：

```text
Same Problem
 ↓
Different Architecture
 ↓
Different Mechanism
 ↓
Different Capability
 ↓
Different Trade-off
 ↓
Different User Value
```

不要仅比较 600 mm/s、30 mm³/s 或 350°C 等单一 headline number。

---

# 12. Technology Evolution Model

```text
Previous Limitation
 ↓
Evolution Driver
 ↓
Technology Change
 ↓
New Capability
 ↓
Product Effect
 ↓
Next Bottleneck
```

典型方向：手动校准 → 自动校准 → 闭环控制；低速机械 → 高速机械 → 高速 + 动态补偿；单色 → 多色 → 多材料；单传感器 → 多传感器融合 → 状态估计；监控 → 检测 → 自动干预 / 恢复；独立设备 → 软件平台 → 生态系统。

这些是分析框架，不代表任何公司的已确认 roadmap。

---

# 13. Research Source Priority

Tier 1：官方产品页、用户手册、技术文档、firmware/software repository、release notes、专利、认证、公司/投资者材料。

Tier 2：专业评测、长期测试、工程拆解、benchmark、技术采访。

Tier 3：GitHub discussions、maker 社区、维修报告、OEM / supplier information、用户体验。

Tier 4 — Discovery Only：搜索摘要、aggregator、无来源社交媒体、转载。

搜索结果本身不自动构成最终证据。

---

# 14. Research Quality Rules

1. Maximum parameter ≠ actual capability。
2. Sensor ≠ closed loop。
3. Supported material ≠ validated process。
4. Self-developed ≠ moat。
5. Higher specification ≠ better product。
6. Feature count ≠ system integration depth。
7. Benchmark result ≠ universal capability。
8. Technology novelty ≠ strategic importance。
9. Product evolution timeline ≠ technology evolution logic。
10. Future inference ≠ confirmed roadmap。

最终必须能够回答：

> **这台机器解决了什么问题？通过什么技术系统解决？形成什么能力？用户获得什么价值？为什么竞品难以复制？当前瓶颈是什么？下一代最可能沿什么方向演进？**
