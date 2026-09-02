# Robot Vacuum Domain Configuration

## Metadata

- **domain_id**: `robot-vacuum`
- **name_zh**: 扫地机器人
- **name_en**: Robot Vacuum
- **category**: Home Service Robot

## Key Subsystems

| Order | Subsystem | Knowledge Module | What It Covers |
|---|---|---|---|
| 1 | Navigation | `knowledge/navigation.md` | LiDAR SLAM, vSLAM, dToF, hybrid — accuracy, speed, reliability |
| 2 | Cleaning System | `knowledge/cleaning-systems.md` | Main brush, side brush, suction power, mopping, roller design |
| 3 | Sensors | `knowledge/sensors.md` | Obstacle avoidance, cliff, dirt detection, carpet recognition |
| 4 | Mapping & Software | `knowledge/mapping.md` | Map building, room segmentation, multi-floor, app UX |
| 5 | Base Station | `knowledge/base-station.md` | Auto-empty, mop washing, water tank, heated drying |
| 6 | Firmware | `knowledge/firmware.md` | RTOS, navigation stack, OTA, voice assistant integration |

## Industry Media & Data Sources

1. 公司官网 / Official Wiki
2. 行业媒体：Vacuum Wars、Robot Report、什么值得买、知乎科技、CNET Smart Home
3. 社区论坛：Reddit (r/RobotVacuums, r/homeautomation)、什么值得买、小红书
4. 供应链公开信息
5. 竞品对比评测（Vacuum Wars YouTube 频道为首选基准）

## Terminology

| English | 中文 | 说明 |
|---|---|---|
| LiDAR SLAM | 激光导航 | 360° 旋转激光测距 + 同步定位建图 |
| vSLAM | 视觉导航 | 单目/双目摄像头 + 特征点匹配建图 |
| dToF | 3D 结构光/飞行时间 | 红外激光阵列深度测距 |
| LDS | 激光测距传感器 | Laser Distance Sensor 的简称 |
| Base Station | 基站 | 多功能底座：充电 + 集尘 + 洗拖布 + 烘干 + 补水 |
| Auto-Empty | 自动集尘 | 基站将尘盒吸入集尘袋 |
| Mop Lifting | 拖布抬升 | 识别地毯后自动抬升拖布模块 |
| Pa | 帕斯卡 | 吸力单位 |
| m² | 平方米 | 单次清扫面积覆盖 |
| mAh / Wh | 电池容量 | 续航能力指标 |
| Obstacle Avoidance | 避障 | 识别并避开电线/袜子/宠物粪便等障碍物 |
| Carpet Boost | 地毯增压 | 识别地毯后自动增强吸力 |
| Multi-Floor | 多楼层 | 保存多张地图，自动识别楼层 |

## Notation

- **Suction power**: `Pa` (Pascal)，常见范围 2000–22000 Pa
- **Battery**: `mAh` 或 `Wh`，常见范围 3200–6400 mAh
- **Coverage**: `m²`，单次清扫面积
- **Noise**: `dB(A)`，工作面噪声
- **End of Life**: `[EOL]` or `†`；新产品：`🆕`
- **Product names**: 使用官方型号 — `X40 Ultra`、`S8 MaxV`、`Qrevo Master`
- **File names**: `公司名_Brand_报告类型_年份.md`
- **First mention**: `中文官方名（English Name）`；此后使用上下文合适的简称

## Key Players (2026)

| Player | Chinese Name | Role |
|---|---|---|
| Roborock | 石头科技 | Market Leader (premium segment) |
| Ecovacs | 科沃斯 | Challenger (broad portfolio) |
| Dreame | 追觅科技 | Challenger (tech-driven) |
| iRobot | — | Legacy / Declining |
| Narwal | 云鲸 | Niche (mopping-first) |
| Xiaomi | 小米 | Value Leader |
| Samsung | 三星 | Niche (premium, Jet Bot series) |
| SharkNinja | — | Niche (mid-range, US market) |
