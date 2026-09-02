# FDM Materials Knowledge

## Purpose

研究 FDM 材料的热学、机械、流变、吸湿、收缩、磨蚀和打印窗口，并判断打印机是否真正具备对应材料的稳定加工能力。

---

## 1. Material Capability Model

```text
Material Chemistry
      ↓
Thermal Window + Rheology
      ↓
Extrusion / Hotend
      ↓
Bed + Chamber + Cooling
      ↓
Layer Bonding / Shrinkage
      ↓
Part Properties
      ↓
Application Fit
```

材料研究不能只记录“支持 PLA / PA / PPS”，而应研究完整 process window。

---

## 2. Material Families

| Family | Typical Examples | Main Challenge | Typical Application |
|---|---|---|---|
| Easy | PLA | heat resistance | models / prototypes |
| General-purpose | PETG | stringing / moisture | functional parts |
| Enclosure-grade | ABS / ASA | warping / emissions | housings / outdoor |
| Flexible | TPU / TPE | feeding / deformation | seals / dampers |
| Engineering | PA / PC | moisture / thermal management | mechanical parts |
| Composite | PLA-CF / PA-CF / GF | abrasion / nozzle wear | stiff structural parts |
| High-performance | PPA / PPS / PEI | high temperature / crystallinity | demanding engineering |
| Support | PVA / BVOH / breakaway | moisture / interface | complex geometry |

---

## 3. Material Research Dimensions

### Thermal

- Nozzle temperature window
- Bed temperature
- Chamber temperature
- Melt stability
- Heat deflection temperature
- Glass transition / melting / crystallization behavior where relevant

### Mechanical

- Tensile strength
- Modulus / stiffness
- Elongation
- Impact resistance
- Creep
- Layer-direction anisotropy

### Processability

- Volumetric flow limit
- Stringing
- Bridging
- Overhang behavior
- Shrinkage / warping
- Cooling requirement
- Adhesion

### Environmental

- Moisture sensitivity
- UV resistance
- Chemical resistance
- Temperature aging

### Hardware Interaction

- Abrasion
- Nozzle compatibility
- Extruder feed reliability
- Dry-box requirement
- Chamber requirement

---

## 4. Printer-to-Material Capability

Use the following chain before claiming compatibility:

```text
Material Requirement
      ↓
Nozzle Temperature
      ↓
Bed Temperature
      ↓
Chamber Requirement
      ↓
Hotend / Extruder Capability
      ↓
Nozzle Wear Resistance
      ↓
Drying / Storage
      ↓
Validated Print Profile
      ↓
Stable Part Quality
```

因此：

- `Max nozzle temperature` ≠ high-temperature material capability
- `Open chamber` ≠ engineering-material readiness
- `Can extrude` ≠ can print dimensionally stable parts
- `Officially supported` ≠ guaranteed performance across all geometries

---

## 5. Multi-Material Systems

研究 AMS / CFS / MMU / toolchanger 时关注：

- Material path geometry
- Filament stiffness range
- Feed / retract reliability
- Cutting mechanism
- Purge strategy
- Drying / humidity control
- RFID / NFC identification
- Profile management
- Cross-contamination

多材料能力应同时评价：

`Color Count + Material Compatibility + Change Time + Purge Waste + Reliability`。

---

## 6. Composite Materials

CF/GF 填充材料重点研究：

- Fiber length and loading
- Nozzle wear
- Extruder wear
- Flow calibration
- Fiber orientation
- Strength anisotropy
- Surface finish

推荐将 nozzle 材料与 composite capability 一起研究，而不是单独评价。

---

## 7. Material × Machine Matrix

报告中可建立：

| Material | Thermal Need | Chamber | Abrasion | Moisture | Typical Machine Requirement |
|---|---|---|---|---|---|
| PLA | Low | No | Low | Low-Medium | Basic heated bed |
| PETG | Medium | Usually No | Low | Medium | Heated bed |
| ASA | Medium-High | Recommended | Low | Medium | Enclosed / heated bed |
| TPU | Medium | No | Low | Medium | Reliable direct-drive path |
| PA | High | Recommended | Medium | High | High-temp hotend + drying |
| PA-CF | High | Recommended | High | High | Hardened nozzle + drying |
| PPA/PPS | Very High | Required | Often High | High | Engineering thermal system |

具体温度和性能数据必须以材料厂商 TDS / 打印配置为证据，不应把表格中的典型区间当成 universal specification。

---

## 8. Ecosystem Strategy

### Open Material Ecosystem

任何合规耗材都可以使用。

优点：选择多、价格竞争充分、用户自由度高。

### Profile-Certified Ecosystem

第三方材料可使用，但厂商提供经过验证的 profile / certification。

### Integrated / Identified Ecosystem

通过 RFID / NFC / 云端 profile 管理材料参数。

研究其商业意义：

```text
Printer Installed Base
        ↓
Material Profiles
        ↓
Consumables Convenience
        ↓
Recurring Revenue / Lock-in
```

---

## 9. Evidence Requirements

材料参数优先级：

1. 材料厂商 TDS / SDS / 官方打印指南
2. 打印机官方材料兼容矩阵与 profile
3. 独立测试
4. 用户长期反馈

必须记录测试条件，因为拉伸强度、HDT、流量和打印速度高度依赖材料配方、打印方向、层高、冷却和测试标准。
