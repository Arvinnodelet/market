# FDM / FFF 3D Printer Domain Model

## Metadata

- **Domain:** FDM / FFF 3D Printing
- **Scope:** Consumer / Prosumer / Professional Desktop
- **Primary Focus:** Product, Technology, Ecosystem, Manufacturing, Reliability

## 1. Domain Definition

FDM/FFF 通过将热塑性聚合物加热至可流动状态，并按照数字模型生成的路径逐层沉积，形成三维实体。

研究时应区分：

- **机器能力**：运动、挤出、热管理、传感器和结构能够做到什么
- **材料能力**：材料在特定温度、环境和工艺窗口下能够做到什么
- **工艺能力**：机器 + 材料 + 参数共同形成的稳定打印能力
- **软件能力**：切片、校准、监测和算法能够补偿什么
- **系统能力**：硬件、固件、软件、材料和用户工作流共同形成的实际体验

### Included

- 桌面级 FDM / FFF 3D 打印机
- Consumer / Prosumer / Professional Desktop 设备
- CoreXY、Bedslinger、CoreXZ、Delta、IDEX、Toolchanger 等运动架构
- 单材料、多色、多材料和部分工程材料工作流
- 打印机硬件、固件、切片软件、设备软件、云服务、传感器、算法、材料与可靠性

### Excluded

- 工业级大型 FDM / FFF 系统的完整市场研究
- SLA / MSLA / DLP / LCD 光固化打印机
- SLS / SLM / DMLS 等粉末床及金属增材制造
- 纯 CAD / 建模软件研究
- 与 FDM 无关的通用机器人、视觉或运动控制市场

## 2. Product Taxonomy

### Product Segments

| Segment | Typical Positioning | Typical User | Main Differentiator |
|---|---|---|---|
| Entry / Budget | 低成本入门 | 新手 / 学生 | 价格、基础打印能力 |
| Consumer | 易用型消费级 | 家庭 / Maker | 自动化、易用性、生态 |
| Prosumer | 高性能消费级 | 高级 Maker / 小型工作室 | 速度、材料、可靠性 |
| Engineering Desktop | 工程桌面级 | 工程师 / 设计团队 | 精度、材料、稳定性 |
| High-temperature / Enclosed | 高温材料型 | 工程应用 | 腔体、热端、材料能力 |
| Multi-material / Multi-color | 多材料 / 多色 | 创客 / 设计用户 | 自动换料、颜色与材料组合 |
| Print-farm / Fleet | 批量生产型 | 打印农场 | Uptime、远程管理、维护效率 |

### Motion Architecture

- Bedslinger / Cartesian
- CoreXY
- CoreXZ
- H-bot
- Delta
- IDEX
- Toolchanger / multi-tool

### Material Capability

- PLA / PETG
- ABS / ASA
- TPU / TPE
- PA / PC
- CF / GF composites
- PPA / PPS / PEI / other high-performance polymers

> 产品分类回答“市场上有哪些产品”；Motion、Extrusion、Thermal、Sensors 等属于技术分类，不应与产品层级混为一谈。

## 3. Users & Use Cases

| User | Need | Typical Workflow | Purchase Driver | Pain Point |
|---|---|---|---|---|
| Beginner / Family | 易用、低维护 | 模型 → 切片 → 一键打印 | 易用性、价格 | 校准、失败率 |
| Maker | 高自由度、改装 | 模型 → 调参 → 打印 → 优化 | 性能、开放性 | 调试成本 |
| Designer / Creator | 外观、快速迭代 | CAD → 打印 → 验证 | 速度、表面质量 | 细节与可靠性 |
| Engineer | 功能验证、工程材料 | CAD → 参数化切片 → 打印 → 测试 | 精度、材料能力 | 热管理、翘曲、稳定性 |
| Small Business | 小批量生产 | 批量切片 → 多机打印 → 质检 | Uptime、吞吐、成本 | 维护、停机 |
| Print Farm | 高利用率 | 任务调度 → 多机生产 → 远程监控 | Fleet、自动化、可靠性 | 故障恢复、人工介入 |

## 4. Domain Workflow

```text
3D Model / CAD
      ↓
Slicer / Print Profile
      ↓
Toolpath / G-code
      ↓
Firmware / Motion Planner
      ↓
Motion + Extrusion + Thermal Control
      ↓
Filament → Extruder → Hotend → Nozzle
      ↓
Layer Deposition
      ↓
Cooling / Layer Bonding
      ↓
Finished Part
      ↓
Inspection / Calibration / Feedback
```

该流程用于定位研究问题：任何产品能力都应尽量落到具体流程节点、硬件、控制、算法、软件或材料机制上。

## 5. Key Technology / Subsystems

| Order | Subsystem | What It Does | Key Metrics | Knowledge Module |
|---|---|---|---|---|
| 1 | Printing Principle | 材料熔融与逐层沉积 | layer height, line width, bonding | `printing-principle.md` |
| 2 | Motion System | 控制喷嘴 / 平台空间运动 | speed, acceleration, rigidity, resonance | `motion-system.md` |
| 3 | Extrusion System | 输送并控制丝材 | extrusion force, retraction, flow | `extrusion-system.md` |
| 4 | Hotend / Thermal | 熔融与温度控制 | max temp, flow, thermal stability | `hotend.md`, `thermal-system.md` |
| 5 | Mechanical Structure | 提供刚度与运动基准 | stiffness, alignment, vibration | `mechanical-structure.md` |
| 6 | Build Platform | 提供成形基准与附着 | flatness, thermal uniformity, adhesion | `build-platform.md` |
| 7 | Sensors | 测量位置、温度、材料和打印状态 | accuracy, repeatability, sampling | `sensors.md`, `vision-systems.md` |
| 8 | Electronics | 执行计算、驱动和通信 | MCU, SoC, drivers, interfaces | `electronics.md` |
| 9 | Control | 将测量转化为控制动作 | loop response, stability, feedback | `motion-control.md`, `control-system.md` |
| 10 | Algorithms | 补偿动态、几何和打印误差 | shaping, pressure advance, calibration | `algorithms.md`, `calibration-algorithms.md` |
| 11 | Firmware / Software | 连接用户工作流与机器执行 | compatibility, OTA, UX, cloud | `firmware.md`, `software.md` |
| 12 | Materials | 决定打印窗口与最终性能 | temperature, shrinkage, moisture, strength | `materials.md` |
| 13 | Reliability / Service | 保证长期稳定运行 | failure rate, recovery, maintenance | `reliability.md` |

## 6. Domain-Specific Benchmarks

### 6.1 Print Quality

- dimensional accuracy
- first-layer consistency
- surface quality
- layer consistency
- overhang / bridging performance
- ringing / ghosting
- layer adhesion
- small-feature reproduction

### 6.2 Productivity

- maximum motion speed
- sustained print speed
- volumetric flow
- acceleration
- cycle time
- material throughput
- print-farm utilization / uptime

> **Vendor maximum speed ≠ sustained production speed.**

### 6.3 Thermal Capability

- nozzle temperature range
- stable volumetric flow at temperature
- bed temperature
- chamber temperature
- thermal uniformity
- warm-up time
- thermal stability

> **Maximum temperature ≠ actual material capability.**

### 6.4 Motion Capability

- positioning accuracy
- repeatability
- acceleration
- rigidity
- resonance behavior
- vibration
- usable speed under print-quality constraints

### 6.5 Extrusion Capability

- maximum stable flow
- extrusion force
- retraction performance
- filament path reliability
- soft-material handling
- multi-material switching behavior

### 6.6 Automation

- auto bed leveling
- automatic Z-offset
- flow calibration
- resonance identification
- nozzle / toolhead calibration
- automatic recovery
- vision inspection
- remote monitoring

> **Sensor presence ≠ closed-loop control.** Research must identify measurement target, placement, sampling, firmware use and resulting control action.

### 6.7 Materials

Assess separately:

- nominal material support
- validated material profiles
- environmental requirements
- chamber requirements
- drying requirements
- long-term reliability

> **Supported material ≠ validated engineering workflow.**

### 6.8 User Experience

- setup time
- calibration burden
- print preparation
- error recovery
- UI / app / cloud
- multi-material workflow
- maintenance accessibility

### 6.9 Reliability

- failure modes
- failure rate where evidence exists
- uptime
- recovery capability
- maintenance frequency
- consumable replacement
- spare-part accessibility

### 6.10 Economics

- hardware ASP
- consumable cost
- material waste
- maintenance cost
- labor intervention
- cost per printed part
- fleet utilization

### Benchmarking Rule

Cross-product comparison should standardize, where possible:

- material
- nozzle diameter
- layer height
- environment
- model geometry
- print profile
- test method
- measurement method

Do not infer overall machine capability from a single headline number such as 600 mm/s, 30 mm³/s or nozzle temperature.

## 7. Technology Questions

### Core Technology

- What is the actual printing process?
- Where is the dominant physical limitation?
- What determines usable print quality?
- Which specifications are marketing maximums versus sustained capability?

### Motion

- Why was this motion architecture selected?
- How does moving mass affect acceleration?
- Where are the dominant stiffness and resonance modes?
- Is input shaping compensating for mechanical limitations or enabling higher performance?

### Extrusion / Thermal

- Direct drive or Bowden?
- What determines extrusion force?
- What is the maximum stable volumetric flow?
- Is hotend maximum temperature supported by stable high-flow operation?
- Is a heated chamber required for target materials?

### Sensors / Control

- What is measured?
- Where is the sensor located?
- What is its sampling rate / repeatability?
- Is it used for monitoring, calibration or closed-loop control?
- Does measurement change an actuator command or machine parameter?

### Algorithms / Software

- How are input shaping, pressure advance and flow calibration implemented?
- Are parameters measured, estimated or manually tuned?
- Is failure detection rule-based, statistical or ML-based?
- Does vision only monitor, or can it change machine behavior?
- What is implemented in firmware versus host / cloud software?

### Materials / Manufacturing / Reliability

- Which materials are actually validated?
- How much purge waste does multi-material operation create?
- How are structure, wiring and toolhead designed for serviceability?
- What are the dominant field failure modes?
- How does the machine recover from failed or interrupted prints?

## 8. Industry Media & Data Sources

### Tier 1 — Primary

- official product pages
- technical specifications
- manuals and service documentation
- firmware / software repositories
- release notes
- certification documents
- patents
- company presentations / investor materials

### Tier 2 — High-quality Secondary

- professional reviews
- long-term tests
- engineering teardowns
- technical interviews
- specialist 3D-printing media
- independent benchmark studies

### Tier 3 — Community / Supply Chain

- engineering communities
- maker forums
- GitHub discussions
- component / OEM information
- repair reports
- user experience reports

### Tier 4 — Discovery Only

- search snippets
- aggregators
- unsourced social posts
- reposts without primary evidence

Search-engine results should be treated as **discovery mechanisms**, not automatically as final evidence.

## 9. Terminology

| Term | Meaning |
|---|---|
| FDM | Fused Deposition Modeling |
| FFF | Fused Filament Fabrication |
| CoreXY | XY motion architecture with coordinated belt motion |
| Bedslinger | Moving-bed Cartesian architecture |
| CoreXZ | Shared belt architecture for X/Z motion |
| Hotend | Melting and extrusion-end assembly |
| Heat Break | Thermal isolation component between hot and cold zones |
| Nozzle | Melt-extrusion outlet |
| Extruder | Filament drive mechanism |
| Volumetric Flow | Material volume extruded per unit time |
| Input Shaping | Motion-control technique for reducing resonance-induced artifacts |
| Pressure Advance | Compensation for extrusion pressure dynamics |
| Bed Mesh | Measured representation of build-surface height variation |
| Multi-Material | Printing workflow using multiple materials rather than only multiple colors |

## 10. Notation & Units

| Quantity | Typical Unit | Research Note |
|---|---|---|
| Print volume | mm / mm³ | Report X × Y × Z where applicable |
| Layer height | mm | Must be interpreted with nozzle diameter |
| Nozzle diameter | mm | Strongly affects flow and feature resolution |
| Print speed | mm/s | Distinguish travel and extrusion speed |
| Acceleration | mm/s² | Compare with sustained print quality |
| Volumetric flow | mm³/s | More useful than speed alone for extrusion capability |
| Temperature | °C | Distinguish setpoint, measured and material requirement |
| Chamber temperature | °C | Important for engineering materials |
| Positioning accuracy | mm | Separate accuracy from repeatability |
| Repeatability | mm | Define measurement conditions |
| Motor current | A | Depends on driver and operating condition |
| Power | W | Distinguish nominal and peak power |
| Weight | kg | Include machine configuration where possible |
| Throughput | g/h or mm³/s | Prefer measured conditions |

### Unit Interpretation Rules

- **mm/s** does not directly equal productivity.
- **mm³/s** is a better indicator of extrusion capability but still depends on material, temperature and pressure.
- **DPI-like concepts should not be imported from other printing technologies without physical equivalence.**
- Accuracy and repeatability must not be treated as interchangeable.

## 11. Key Players

### Consumer / Prosumer

- Bambu Lab
- Creality
- Anycubic
- Prusa Research
- Elegoo
- FlashForge
- QIDI Tech
- Snapmaker

### Open / Community Ecosystem

- Voron Design
- Klipper
- RepRap / Marlin ecosystem

### Industrial / Engineering Reference

- UltiMaker
- Raise3D
- Stratasys

When researching a company, separate **company-level positioning** from individual product-level capability.

## 12. Common Technical Trade-offs

| Trade-off | Benefit | Cost / Risk |
|---|---|---|
| Higher speed vs quality | Shorter cycle time | vibration, ringing, thermal / extrusion limits |
| Higher flow vs thermal margin | Higher productivity | incomplete melting, pressure instability |
| Larger build volume vs rigidity | More application space | frame stiffness, mass, cost |
| Open architecture vs integration | Modularity, lower lock-in | more configuration burden |
| Automation vs complexity | Lower user effort | sensors, software and failure modes |
| Multi-material vs waste | More capability | purge waste, mechanism complexity |
| High-temperature capability vs cost | Engineering materials | chamber, heater, sealing, component cost |

## 13. Research Boundaries

```text
Digital Model / CAD
        ↓
Slicer / Toolpath
        ↓
Motion Planning
        ↓
Motion + Extrusion + Thermal
        ↓
Material Deposition
        ↓
Cooling / Layer Bonding
        ↓
Part Geometry / Surface
        ↓
Mechanical / Functional Performance
        ↓
User / Production Outcome
```

Use the following capability chain to avoid collapsing machine specifications into application claims:

```text
Machine Capability
        ↓
Material Capability
        ↓
Process Capability
        ↓
Part Capability
        ↓
Application / Production Capability
```

## 14. Knowledge Map

```text
Printing Principle
├── Motion System
├── Extrusion System
├── Hotend / Thermal System
├── Mechanical Structure
├── Build Platform
├── Sensors / Vision
├── Electronics
├── Control
├── Algorithms / Calibration
├── Firmware / Software
├── Materials
├── Reliability
└── Manufacturing
```

## 15. Progressive Knowledge Build-Up

Start with the causal chain before drilling into individual components:

1. Printing principle
2. Motion + extrusion + thermal system
3. Mechanical structure and build platform
4. Sensors + control + algorithms
5. Firmware + software workflow
6. Materials + process window
7. Reliability + manufacturing
8. Product / competitive implications

The goal is not to maximize the number of files, but to cover the technologies that materially determine product capability.
