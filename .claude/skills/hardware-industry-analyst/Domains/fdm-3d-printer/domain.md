# FDM 3D Printer Domain Model

## Metadata

- **domain_id**: `fdm-3d-printer`
- **name_zh**: 桌面 FDM 3D 打印机
- **name_en**: Desktop FDM 3D Printer
- **category**: Additive Manufacturing / Desktop Fabrication
- **scope**: Consumer / Prosumer / Professional Desktop FDM/FFF

---

## 1. Domain Definition

### Definition

FDM/FFF 通过将热塑性聚合物加热至可流动状态，并按照数字模型生成的路径逐层沉积，形成三维实体。

研究时应区分：

- **打印机能力**：机器本体能够稳定实现什么
- **材料能力**：耗材在特定热、运动、环境条件下能够实现什么
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

---

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
- TPU / flexible
- PA / PC
- CF/GF composites
- PPA / PPS / PEI / other high-performance polymers

> 产品分类回答“市场上有哪些产品”；Motion、Extrusion、Thermal、Sensors 等属于技术分类，不应与产品层级混为一谈。

---

## 3. Users & Use Cases

| User | Need | Typical Workflow | Purchase Driver | Pain Point |
|---|---|---|---|---|
| Beginner / Family | 易用、低维护 | 模型 → 切片 → 一键打印 | 易用性、价格 | 校准、失败率 |
| Maker | 高自由度、改装 | 模型 → 调参 → 打印 → 优化 | 性能、开放性 | 调试成本 |
| Designer / Creator | 外观、快速迭代 | CAD → 打印 → 验证 | 速度、表面质量 | 细节与可靠性 |
| Engineer | 功能验证、工程材料 | CAD → 参数化切片 → 打印 → 测试 | 精度、材料能力 | 热管理、翘曲、稳定性 |
| Small Business | 小批量生产 | 批量切片 → 多机打印 → 质检 | Uptime、吞吐、成本 | 维护、停机 |
| Print Farm | 高利用率 | 任务调度 → 多机生产 → 远程监控 | Fleet、自动化、可靠性 | 故障恢复、人工介入 |

---

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

---

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
| 9 | Control | 将测量转化为控制动作 | loop response, stability, feedback | `motion-control.md`, `thermal-control.md`, `control-system.md` |
| 10 | Algorithms | 补偿动态、几何和打印误差 | shaping, pressure advance, calibration | `algorithms.md`, `calibration-algorithms.md` |
| 11 | Firmware / Software | 连接用户工作流与机器执行 | compatibility, OTA, UX, cloud | `firmware.md`, `software.md`, `slicer.md` |
| 12 | Materials | 决定打印窗口与最终性能 | temperature, shrinkage, moisture, strength | `materials.md`, `engineering-materials.md` |
| 13 | Reliability / Service | 保证长期稳定运行 | failure rate, recovery, maintenance | `reliability.md` |

---

## 6. Domain-Specific Benchmarks

| Dimension | Core Metrics | Measurement / Comparison Notes |
|---|---|---|
| Print Quality | dimensional accuracy, surface quality, ringing, layer adhesion | 必须说明模型、层高、材料、速度等测试条件 |
| Productivity | usable speed, acceleration, volumetric flow, throughput, uptime | 厂商 Max Speed ≠ 可持续生产速度 |
| Thermal | nozzle temperature, bed temperature, chamber capability, stability | Max Temperature ≠ 实际材料能力 |
| Motion | kinematics, rigidity, resonance, positioning accuracy | 应结合动态工况评价，而非只看理论分辨率 |
| Extrusion | max flow, pressure response, retraction, filament handling | `mm³/s` 应注明材料、喷嘴、层高和温度 |
| Automation | calibration coverage, sensing, failure detection | Sensor presence ≠ closed-loop control |
| Materials | supported material envelope, abrasive / hygroscopic capability | Supported ≠ validated engineering workflow |
| UX | setup time, calibration effort, maintenance, software workflow | 应考虑从开箱到稳定打印的完整流程 |
| Reliability | failure modes, recovery, service interval, uptime | 长期运行比单次 Demo 更有价值 |
| Economics | ASP, BOM, consumables, service cost, ecosystem revenue | BOM / cost estimation必须标注证据等级 |

### Benchmark Principle

- **600 mm/s ≠ 600 mm/s usable printing speed**
- **30 mm³/s ≠ 30 mm³/s sustained production flow**
- 单一 DPI、速度或喷嘴温度不能代表整机能力
- 跨产品比较必须尽量统一材料、喷嘴、层高、环境、模型和测试方法

---

## 7. Technology Questions

### Core Technology

- FDM 的实际打印性能由哪些物理约束决定？
- 最大速度、最大加速度和最大体积流量之间如何区分？
- 层间结合、冷却和沉积宽度如何影响最终性能？

### Motion

- 采用什么运动架构？为什么？
- Frame / Gantry 刚度如何影响共振与精度？
- Input Shaping 如何改善高速运动？
- 厂商宣传速度对应什么测试条件？

### Extrusion / Thermal

- Direct Drive / Bowden 的选择原因是什么？
- Extruder 最大推力与实际压力能力是多少？
- Hotend 的最大温度与最大稳定体积流量分别是多少？
- Melt zone、heat break、nozzle 如何限制材料能力？
- Chamber 对 ABS / ASA / PA / PC / 高温材料有什么实际影响？

### Sensors / Control

- 使用哪些位置、Z、材料、温度和视觉传感器？
- Sensor 的目标、安装位置、采样频率是什么？
- 传感器结果是否真正进入控制闭环？
- 是否存在多传感器融合或在线状态估计？

### Algorithms / Software

- 是否使用 Input Shaping、Pressure Advance、Flow Calibration、Bed Mesh 等算法？
- 校准是规则 / 参数搜索，还是机器学习模型？
- Vision / AI 是监控、分类，还是会改变机器控制参数？
- Firmware、Slicer、Cloud、App 如何协同？

### Materials / Manufacturing / Reliability

- 官方支持材料与真实验证材料是否一致？
- 多材料系统如何处理换料、污染和 purge waste？
- 机器结构、Toolhead、线束、装配和校准流程如何影响成本与可靠性？
- 常见失效模式、维护周期和故障恢复机制是什么？

---

## 8. Industry Media & Data Sources

1. 官方产品页、技术规格、用户手册、Wiki
2. 官方 Firmware / Software 文档、Release Notes
3. 认证、专利、FCC / CE 等公开资料
4. 专业评测、长期测试、拆机与工程分析
5. 3D printing 专业媒体与行业数据
6. Maker / Engineering 社区
7. 供应链、零部件厂商与 OEM 信息

> 搜索引擎结果用于发现来源，不应作为高置信度事实的最终证据。

---

## 9. Terminology

| English | 中文 | Definition | Research Notes |
|---|---|---|---|
| FDM / FFF | 熔融沉积制造 | 热塑性材料逐层挤出成形 | FDM 是商标化术语，FFF 更通用 |
| CoreXY | CoreXY 运动系统 | XY 联动、平台通常固定 | 关注质量、刚度、皮带路径 |
| Bedslinger | 平台移动式 | Y 轴带动打印平台移动 | 高速时平台惯量明显 |
| CoreXZ | CoreXZ 运动系统 | X/Z 联动架构 | 关注 Z 运动与结构设计 |
| Hotend | 热端 | 熔化并挤出材料的组件 | Max Temp ≠ Max Flow |
| Heat Break | 隔热管 | 热端冷热区之间的热隔离部件 | 影响热爬与材料兼容性 |
| Nozzle | 喷嘴 | 材料最终出口 | 材料、孔径影响流量与磨损 |
| Extruder | 挤出机 | 驱动丝材进给的机构 | 关注推力、齿轮、路径 |
| Volumetric Flow | 体积流量 | `mm³/s` | 衡量熔融与挤出能力的重要指标 |
| Input Shaping | 输入整形 | 预处理运动指令以降低共振激励 | 与机械共振特性相关 |
| Pressure Advance | 压力提前 | 补偿挤出压力动态 | 与速度、材料和喷嘴相关 |
| Bed Mesh | 热床网格 | 描述打印面高度变化的补偿模型 | 不等同于机械平面度 |
| Multi-Material | 多材料 | 自动切换不同材料或颜色 | 关注 waste、换料时间和污染 |

---

## 10. Notation & Units

- Length: `mm`
- Speed: `mm/s`
- Acceleration: `mm/s²`
- Volumetric Flow: `mm³/s`
- Temperature: `°C`
- Power: `W`
- Electrical: `V`, `A`
- Weight: `g`, `kg`
- Print volume: `mm × mm × mm`
- Resolution / layer height: `mm`

---

## 11. Key Players

| Player | Chinese Name | Role | Main Products / Ecosystem |
|---|---|---|---|
| Bambu Lab | 拓竹 | Consumer / Prosumer | 高速 FDM、AMS、多材料、软件生态 |
| Creality | 创想三维 | Consumer / Prosumer | Ender、K 系列、K1 / K2 等 |
| Prusa Research | 普鲁萨 | Consumer / Prosumer / Open-source | Original Prusa、PrusaSlicer |
| Anycubic | 纵维立方 | Consumer | Kobra、Vyper 等 FDM 产品 |
| Elegoo | ELEGOO | Consumer | Neptune 等 FDM 产品 |
| QIDI | 奇想科技 | Prosumer / Engineering Desktop | 高温、封闭腔体 FDM |
| Snapmaker | 速客 | Prosumer / Multi-function | FDM + 激光 + CNC |
| Voron ecosystem | Voron 社区 | Open-source / DIY | CoreXY、Klipper、Modular Hardware |
| UltiMaker | Ultimaker | Professional | S 系列等专业桌面设备 |
| Raise3D | 瑞浦 | Professional | 高端桌面 / 工业级桌面 FDM |

> 名单用于研究入口，不代表市场排名；排名与市场份额必须通过证据单独验证。

---

## 12. Common Technical Trade-offs

| Trade-off | Option A | Option B | Typical Impact |
|---|---|---|---|
| Speed vs Quality | 高速运动 | 低速高质量 | 共振、表面质量、周期时间 |
| Flow vs Material Range | 高熔融流量 | 更宽材料窗口 | Hotend 设计与温度窗口 |
| Rigidity vs Cost | 高刚度结构 | 低成本结构 | 精度、振动、BOM |
| Build Volume vs Rigidity | 大体积 | 紧凑结构 | 体积、惯量、框架刚度 |
| Enclosure vs Cost | 封闭腔体 | 开放结构 | 高温材料能力、热管理 |
| Multi-material vs Waste | 自动换料 | 单材料 | purge、换料时间、系统复杂度 |
| Open vs Integrated Ecosystem | 开放固件/耗材 | 深度软硬件整合 | 自由度 vs UX |
| Sensor Coverage vs Complexity | 更多传感器 | 简化传感 | 自动化、BOM、维修 |
| Automation vs Serviceability | 高度自动化 | 可维护、可调试 | 用户门槛与维修复杂度 |
| Proprietary Integration vs Standardization | 专有集成 | 标准组件 | 性能、成本、供应链灵活性 |

---

## 13. Research Boundaries

```text
FDM Printer Domain
        ↓
Printing Physics
        ↓
Motion / Extrusion / Thermal / Structure
        ↓
Sensors / Electronics / Control
        ↓
Algorithms / Firmware / Slicer / Cloud
        ↓
Materials / Environment
        ↓
Print Quality / Productivity / Reliability / Economics
```

### Boundary Rules

- **Domain**：定义桌面 FDM 产品与完整工作流
- **Technology**：解释产品为什么能达到某种性能
- **Knowledge**：深入研究可复用的技术机制
- **Frameworks**：提供跨领域通用研究方法，不在此重复
- **Evidence**：定义事实、推断、估算和证据等级，不在 Domain 中自行降低证据标准

---

## 14. Knowledge Map

```text
FDM 3D Printer Knowledge Map
│
├── Core Technology
│   ├── printing-principle.md
│   ├── motion-system.md
│   ├── extrusion-system.md
│   └── thermal-system.md
│
├── Hardware
│   ├── mechanical-structure.md
│   ├── hotend.md
│   ├── extruder.md
│   ├── build-platform.md
│   └── electronics.md
│
├── Sensors
│   ├── sensors.md
│   └── vision-systems.md
│
├── Control
│   ├── motion-control.md
│   ├── thermal-control.md
│   └── control-system.md
│
├── Algorithms
│   ├── algorithms.md
│   └── calibration-algorithms.md
│
├── Firmware / Software
│   ├── firmware.md
│   ├── software.md
│   └── slicer.md
│
├── Materials
│   ├── materials.md
│   └── engineering-materials.md
│
└── Reliability
    └── reliability.md
```

> Knowledge Map 是导航层，不要求所有领域完全相同。模块只有在会实质影响产品性能、技术判断或研究结论时才应独立存在。

---

## 15. Progressive Knowledge Build-Up

```text
Domain Model
   ↓
Technology Model
   ↓
Knowledge Modules
   ↓
Product Research
   ↓
Cross-product Benchmark
   ↓
Repeated Validation
   ↓
Domain Model refinement
```

只有当某项知识具有跨产品复用价值，并且经过足够证据验证后，才应沉淀到长期 Knowledge 层。

---

## Evidence Requirements

对技术能力的判断应优先使用：

1. 官方产品页、技术规格、Wiki、用户手册
2. 官方固件 / 软件文档与更新记录
3. 认证、专利、拆机及专业测试
4. 高质量长期评测和用户反馈
5. 社区讨论与供应链信息

特别注意区分：

- Advertised speed ≠ usable sustained speed
- Maximum nozzle temperature ≠ practical material capability
- Sensor presence ≠ closed-loop control
- AI monitoring ≠ autonomous control
- Supported material ≠ validated engineering-material workflow
