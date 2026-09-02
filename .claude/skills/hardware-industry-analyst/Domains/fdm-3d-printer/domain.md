# FDM 3D Printer Domain Configuration

## Metadata

- **domain_id**: `fdm-3d-printer`
- **name_zh**: 桌面 FDM 3D 打印机
- **name_en**: Desktop FDM 3D Printer
- **category**: Additive Manufacturing / Desktop Fabrication

## Key Subsystems

| Order | Subsystem | Knowledge Module | What It Covers |
|---|---|---|---|
| 1 | Motion System | `knowledge/motion-systems.md` | Bedslinger, CoreXY, CoreXZ, IDEX, Delta — speed, cost, reliability |
| 2 | Extrusion & Hotend | `knowledge/hotends.md` | Flow rate tiers, nozzle materials, heat break, heater types, failure diagnostics |
| 3 | Sensors | `knowledge/sensors.md` | Eddy current, inductive, load cell, strain gauge, LiDAR, AI vision |
| 4 | Firmware | `knowledge/firmware.md` | Marlin, Klipper, RRF, Bambu OS, Creality OS |
| 5 | Electronics | `knowledge/electronics.md` | MCU architectures, motor drivers, communication buses, chipsets |
| 6 | Materials | `knowledge/materials.md` | PLA, PETG, ABS, ASA, Nylon, CF composites — properties & printability |
| 7 | Vision Systems | `knowledge/vision-systems.md` | Camera monitoring, spaghetti detection, AI failure detection |
| 8 | Motion Control | `knowledge/motion-control.md` | Input shaping, pressure advance, S-curve, closed-loop stepper |
| 9 | Manufacturing | `knowledge/manufacturing.md` | Product dev stages, vertical integration, DFM, supply chain |

## Industry Media & Data Sources

1. 公司官网 / Official Wiki
2. 行业媒体：3DPrint.com、All3DP、Tom's Hardware、CNET
3. 社区论坛：Reddit (r/BambuLab, r/Creality, r/3Dprinting)、官方论坛、StackExchange
4. 供应链公开信息
5. 竞品对比评测

## Terminology

| English | 中文 | 说明 |
|---|---|---|
| FDM / FFF | 熔融沉积制造 | 最主流的桌面 3D 打印技术 |
| CoreXY | CoreXY 运动系统 | 固定床面 XY 联动架构，高速打印主流方案 |
| Bedslinger | 平台移动式 | 传统笛卡尔架构，Y 轴移动热床 |
| IDEX | 独立双喷头 | 两个独立 X 轴的 extruder |
| Hotend | 热端 | 熔化并挤出耗材的组件 |
| Heat Break | 喉管/隔热管 | 热端冷热区之间的隔热部件 |
| Nozzle | 喷嘴 | 线材出口，直径 0.2–1.0mm |
| Extruder | 挤出机 | 驱动耗材进给到热端的机构 |
| Build Plate / Bed | 热床/平台 | 打印模型的附着面 |
| PEI Sheet | PEI 弹簧钢板 | 最主流的打印附着表面 |
| Eddy Current Sensor | 涡流传感器 | 高精度非接触位移/压力测量 |
| Load Cell | 力传感器 | 通过喷嘴接触力测量调平 |
| LiDAR | 激光雷达 | 激光测距，用于首层扫描 |
| AMS | 自动材料系统 | Bambu Lab 多色打印系统 |
| CFS | 创想耗材系统 | Creality 多色打印系统 |
| Input Shaping | 输入整形 | 通过预处理指令消除共振 |
| Pressure Advance | 压力提前 | 补偿喷嘴内压力滞后 |
| Flow Rate | 流量 | mm³/s，热端熔化能力的核心指标 |

## Notation

- **Build volumes**: `180³` = 180×180×180 mm；非正方体：`330×320×325 mm`
- **End of Life**: `[EOL]` or `†`；新产品：`🆕`
- **Product names**: 使用官方型号 — `X2D`、`K2 Plus`、`A1 mini`、`SPARKX i7`
- **File names**: `公司名_Brand_报告类型_年份.md`
- **First mention**: `中文官方名（English Name）`；此后使用上下文合适的简称

## Key Players (2026)

| Player | Chinese Name | Role |
|---|---|---|
| Bambu Lab | 拓竹 | Market Leader |
| Creality | 创想三维 | Challenger |
| Prusa Research | — | Niche (Open-Source Premium) |
| Anycubic | 纵维立方 | Follower |
| Elegoo | — | Emerging Challenger |
| Qidi | 启庞 | Niche (Enclosed Mid-Range) |
| Voron | — | Niche (DIY/Open-Source) |
| Snapmaker | 快造 | Niche (3-in-1) |
