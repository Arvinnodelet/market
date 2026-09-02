# UV Printer Domain Model

## Metadata

- **domain_id**: `uv-printer`
- **name_zh**: UV 打印机
- **name_en**: UV Printer
- **category**: Fabrication Tool

## 1. Domain Definition

UV Printer 是通过喷墨方式将 UV 固化型墨水沉积到基材表面，并利用 UV 光源即时或分阶段固化形成图文/颜色/纹理的数字印刷设备。

### Included
- Desktop UV printers
- A3/A4/A2/A1 class UV flatbed printers
- UV roll-to-roll / hybrid printers when relevant
- UV DTF printers when the printing process is part of the research scope

### Excluded
- Traditional solvent / eco-solvent printers
- Pure UV curing chambers without printing
- Conventional FDM / SLA / DLP 3D printers unless used as a comparison

## 2. Product Taxonomy

| Segment | Product Type | Typical Differentiator | Primary User |
|---|---|---|---|
| Desktop | A4/A3 UV flatbed | Size / price / ease of use | Maker / small business |
| Prosumer | A2/A1 flatbed | Throughput / color / materials | Studio / print shop |
| Professional | Large-format UV | Productivity / reliability | Commercial printer |
| Hybrid | Flatbed + roll | Substrate flexibility | Sign / graphics business |
| UV DTF | Film transfer | Irregular surfaces / low setup | Customization business |

## 3. Users & Use Cases

| User | Need | Workflow | Purchase Driver | Pain Point |
|---|---|---|---|---|
| Maker | Small custom objects | Design → print → cure | Ease of use | Calibration |
| Small business | On-demand customization | Artwork → RIP → print | Cost / throughput | Maintenance |
| Print shop | Continuous production | RIP → print → curing | Productivity | Reliability |
| Brand / studio | Premium graphics | Color management → print | Color / texture | Consistency |

## 4. Printing Workflow

```text
Artwork / CAD
     ↓
Color Management / RIP
     ↓
Rasterization
     ↓
Printhead Jetting
     ↓
Ink Droplet Deposition
     ↓
UV Exposure / Curing
     ↓
Finished Surface
     ↓
Inspection / Maintenance
```

## 5. Key Subsystems

| Order | Subsystem | What It Does | Key Metrics |
|---|---|---|---|
| 1 | Printhead | Generates ink droplets | Nozzle count, drop size, frequency |
| 2 | Ink System | Stores, filters, supplies ink | Pressure, filtration, circulation |
| 3 | UV Curing | Polymerizes UV ink | Wavelength, irradiance, dose |
| 4 | Motion System | Positions printhead/material | Accuracy, repeatability, speed |
| 5 | Media / Vacuum Platform | Holds substrate flat | Flatness, vacuum, work area |
| 6 | RIP / Color Management | Converts artwork to jetting data | ICC, screening, channel control |
| 7 | Control Electronics | Drives printhead/motion/UV | Timing, synchronization |
| 8 | Sensors | Monitor position, ink, temperature, safety | Resolution, repeatability |

## 6. Domain-Specific Benchmarks

| Metric | Entry | Mid | High-end | Professional | Notes |
|---|---|---|---|---|---|
| Print area | Small | Medium | Large | Large-format | Compare usable area |
| Resolution | Basic | High | Very high | Application dependent | Vendor DPI is not always optical resolution |
| Color channels | CMYK | CMYK + W | CMYK + W + LC/LM/spot | Application dependent | Channel count affects gamut and workflow |
| Drop size | Larger | Medium | Small / variable | Application dependent | Depends strongly on printhead |
| UV wavelength | Common 365–405 nm classes | Common 365–405 nm classes | Application dependent | Application dependent | Verify actual lamp/LED spectrum |
| Throughput | Low | Medium | High | Very high | Test condition must be specified |

## 7. Technology Questions

重点研究：

- Piezo inkjet vs other jetting architectures
- Printhead architecture and replacement strategy
- Variable drop / grayscale jetting
- Ink formulation and viscosity management
- White ink circulation / anti-settling strategy
- UV LED curing architecture
- Pinning vs full curing
- Multi-layer / texture / varnish printing
- RIP and color-management pipeline
- Media flatness and vacuum table
- Head height / collision protection
- Motion synchronization
- Nozzle detection and compensation
- Environmental control

## 8. Industry Media & Data Sources

1. Manufacturer technical documentation and manuals
2. Printhead manufacturer documentation
3. Ink manufacturer technical data sheets
4. Professional printing industry media
5. Engineering forums and teardown communities
6. Distributor / service documentation

## 9. Terminology

| English | 中文 | Definition |
|---|---|---|
| UV Ink | UV 墨水 | UV 固化型喷墨墨水 |
| Printhead | 打印头 | 喷射墨滴的核心器件 |
| Drop Size | 墨滴大小 | 单个墨滴体积/等效体积 |
| Grayscale | 灰度喷墨 | 通过改变墨滴体积实现不同覆盖量 |
| White Ink | 白墨 | 用于底色、遮盖或多层打印 |
| Varnish | 光油 | 用于表面光泽、纹理和局部效果 |
| UV Curing | UV 固化 | 通过紫外光引发墨水聚合固化 |
| Pinning | 预固化 | 使墨滴先部分固定，控制扩散 |
| RIP | 光栅图像处理 | 将设计文件转换为打印数据 |
| ICC Profile | ICC 色彩配置文件 | 描述设备色彩特性的配置文件 |
| Pass | 打印遍数 | 打印头相对介质完成一次覆盖的过程 |

## 10. Common Technical Trade-offs

| Trade-off | Option A | Option B | Impact |
|---|---|---|---|
| Print speed vs quality | Fewer passes | More passes | Throughput vs detail |
| UV dose vs surface appearance | Strong cure | Lower / staged cure | Cure completeness vs gloss / adhesion |
| White ink | Circulation | Agitation / periodic purge | Reliability vs complexity |
| Drop size | Fixed | Variable / grayscale | Simplicity vs image quality |
| Printhead | Low-cost | High-performance | BOM vs productivity |
| Work area | Larger | Smaller | Capability vs machine size |
| Ink viscosity | Higher | Lower | Material compatibility vs jetting stability |

## 11. Key Players

| Player | Representative Products / Role |
|---|---|
| Roland DG | Professional UV printers |
| Mimaki | Professional UV printing |
| Mutoh | Large-format UV |
| Epson | Industrial inkjet / UV-related technologies |
| Canon | Professional / industrial digital printing |
| Ricoh | Industrial printheads / printing systems |
| Fujifilm | Industrial inkjet / UV printing |
| xTool | Desktop / maker-oriented printing ecosystem |
| Procolored | Desktop UV printing |
| Anycubic | Consumer / maker digital fabrication ecosystem |

## 12. Research Boundaries

UV Printer reports must distinguish at least four layers:

```text
Printer Hardware
     ↓
Printhead / Ink / UV Curing
     ↓
RIP / Color Management
     ↓
Material / Surface Interaction
     ↓
Final Print Quality
```

“DPI 高”或“速度快”不能单独代表打印质量。应尽量结合墨滴体积、pass 数、介质、墨水、UV dose、图像模式和测试条件分析。
