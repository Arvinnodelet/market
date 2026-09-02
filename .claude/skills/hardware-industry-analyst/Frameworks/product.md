# Product Research & Analysis Framework

## Objective

研究并评价单个硬件产品，回答四个核心问题：

1. 它是什么、面向谁、在产品线中扮演什么角色？
2. 它如何工作，核心技术和子系统如何实现？
3. 它的用户价值、制造逻辑和经济性如何？
4. 与直接竞品相比，它的技术、产品和战略位置是什么？

本框架先建立事实与证据，再形成评价。购买建议不是默认输出，只有用户明确要求时才加入。

---

# 1. Product Definition & Positioning

| Attribute | Data | Evidence / Source | Confidence |
|---|---|---|---|
| Manufacturer | | | |
| Product / Model | | | |
| Series / Tier | | | |
| MSRP | | | |
| Street Price | | | |
| Release Date | | | |
| Status | Active / EOL / Announced | | |
| Target User | | | |
| Primary Use Cases | | | |
| Predecessor | | | |
| Successor | | | |

### Positioning Questions

- 产品解决什么问题？
- 与同品牌其他产品的边界是什么？
- 它位于入门、中端、高端还是专业市场？
- 定价是否与其性能、功能、生态和品牌定位匹配？

---

# 2. Product Portfolio Role

分析该产品在公司产品矩阵中的角色，而不是孤立评价单品。

| Dimension | Analysis |
|---|---|
| Product Line | |
| Price Position | |
| Performance Position | |
| Feature Position | |
| Technology Role | |
| Platform / Shared Architecture | |
| Ecosystem Role | |
| Cannibalization Risk | |
| Upgrade Path | |

---

# 3. Users & Use Cases

| User Group | Core Need | Typical Workflow | Product Fit | Evidence |
|---|---|---|---|---|
| | | | | |

区分：
- Primary user
- Secondary user
- Professional / commercial user
- Edge cases

重点分析用户为什么选择该产品，而不是仅描述“适合谁”。

---

# 4. Specifications

建立完整参数表。公开参数与推导参数分开。

| Category | Parameter | Value | Source | Status |
|---|---|---|---|---|
| Physical | | | | Confirmed / Reported / Inferred / Estimated |
| Performance | | | | |
| Electrical | | | | |
| Connectivity | | | | |
| Environmental | | | | |
| Materials | | | | |
| Software | | | | |

不要为了填满表格而猜测缺失参数；未知写 `Unknown / 未公开`。

---

# 5. System Architecture

使用领域技术模型建立系统架构图。

```text
                 ┌──────────────────────┐
                 │      User Input      │
                 └──────────┬───────────┘
                            ↓
                 ┌──────────────────────┐
                 │ Software / Control   │
                 └──────────┬───────────┘
                            ↓
          ┌─────────────────┼─────────────────┐
          ↓                 ↓                 ↓
      Sensing           Actuation          Processing
          ↓                 ↓                 ↓
          └─────────────────┼─────────────────┘
                            ↓
                 ┌──────────────────────┐
                 │ Physical Output     │
                 └──────────────────────┘
```

根据具体领域替换模块，并说明数据流、能量流、控制流和关键接口。

---

# 6. Core Subsystems

从领域技术模型中选择与本产品相关的核心子系统。

| Subsystem | Key Components | Key Parameters | Self-developed / Outsourced | Competitive Position | Evidence |
|---|---|---|---|---|---|
| | | | | | |

对真正影响产品性能的子系统进行深拆，避免平均用力。

### Recommended Deep-Dive Structure

#### 6.x Technology / Subsystem Name

1. Working principle
2. System architecture
3. Hardware implementation
4. Key components and materials
5. Installation / mechanical arrangement
6. Control / algorithm
7. Key parameters
8. Reliability and failure modes
9. Manufacturing implications
10. Cost implications
11. Evolution across generations
12. Cross-model comparison
13. Competitor architecture comparison
14. Advantages
15. Limitations

---

# 7. Software / Algorithms

| Layer | Implementation | Capability | Proprietary? | Evidence |
|---|---|---|---|---|
| Firmware | | | | |
| Control | | | | |
| Algorithm | | | | |
| Mobile / Desktop App | | | | |
| Cloud | | | | |
| API / Integration | | | | |

重点分析软件是否改变硬件能力，而不是仅列出 App 功能。

---

# 8. Materials / Consumables

适用于存在耗材、介质或材料的硬件品类。

| Material / Consumable | Compatibility | Performance | Cost | Lock-in | Source |
|---|---|---|---|---|---|
| | | | | | |

对于不适用的产品，删除该章节或明确说明 N/A。

---

# 9. User Experience

| Dimension | Assessment | Evidence |
|---|---|---|
| Out-of-Box Experience | | |
| Setup / Calibration | | |
| First Use | | |
| Software Experience | | |
| Noise / Comfort | | |
| Maintenance | | |
| Reliability | | |
| Troubleshooting | | |
| Support | | |
| Documentation | | |

重点区分厂商设计意图与用户实际体验。

---

# 10. Reliability & Service

分析：

- Known failure modes
- Wear parts
- Maintenance intervals
- Calibration drift
- Thermal / mechanical / electrical stress
- Serviceability
- Spare parts availability
- Warranty / support
- Community repairability

| Failure / Risk | Mechanism | Impact | Detection | Mitigation | Evidence / Confidence |
|---|---|---|---|---|---|
| | | | | | |

---

# 11. Manufacturing Perspective

| Dimension | Assessment | Confidence |
|---|---|---|
| Estimated BOM | | |
| Major Cost Drivers | | |
| Assembly Complexity | | |
| Harness / Wiring Complexity | | |
| Calibration Steps | | |
| DFM / DFA | | |
| Serviceability | | |
| Supply Chain Risk | | |
| Manufacturing Scale | | |

BOM、毛利和成本必须标记为 `Estimated`，除非有公开财务或供应链证据。

---

# 12. Cost & Economics

区分消费者价格与企业经济性。

| Item | Estimate / Data | Basis | Confidence |
|---|---|---|---|
| MSRP | | | |
| Street Price | | | |
| Estimated BOM | | | |
| Consumable Cost | | | |
| Service Cost | | | |
| Upgrade Cost | | | |
| Estimated Gross Margin | | | |

如果缺少可靠数据，不计算伪精确的毛利率。

---

# 13. Competitive Benchmark

选择 2–4 个真正直接的竞品。优先同价位、同用户、同工作流，而不是仅凭品牌知名度选择。

| Dimension | This Product | Competitor A | Competitor B | Competitor C |
|---|---|---|---|---|
| Price | | | | |
| Core Spec | | | | |
| Key Technology | | | | |
| Setup / Calibration | | | | |
| Software | | | | |
| Materials / Consumables | | | | |
| Ecosystem | | | | |
| Maintenance | | | | |
| Service | | | | |
| Estimated Cost | | | | |

### Competitive Position

明确回答：

- 哪些指标领先？
- 哪些指标只是参数领先但用户价值有限？
- 哪些地方落后？
- 差异来自架构、器件、算法、软件、生态还是价格？

---

# 14. Product Evolution

| Generation | Release | Major Change | Technical Change | Strategic Meaning |
|---|---|---|---|---|
| | | | | |

重点判断产品变化是：

- incremental upgrade
- architecture change
- platform change
- ecosystem expansion
- cost-down / manufacturing optimization

---

# 15. Strategic Assessment

### Product Strengths

1.
2.
3.

### Product Weaknesses

1.
2.
3.

### Technical Position

Leading / Competitive / Behind，并说明依据。

### User Value

分析性能、体验、生态和价格共同形成的实际价值。

### Manufacturing Position

分析 BOM、装配、校准、供应链和服务能力。

### Competitive Position

说明相对于主要竞品的结构性优势与劣势。

### Strategic Role

说明该产品对公司产品线、技术平台、生态和竞争防御的意义。

### Overall Assessment

用 1–3 个段落给出综合判断，避免空泛总结。

> 购买建议仅在用户明确要求时输出。若需要购买建议，再增加 Buy / Consider / Skip 以及明确的 decision rule。

---

# 16. Evidence & Confidence

重要结论建议使用以下状态：

| Status | Meaning |
|---|---|
| Confirmed | 官方或一手资料明确确认 |
| Verified | 多个可靠来源交叉验证 |
| Reported | 可靠第三方报道，但未被官方确认 |
| Inferred | 基于结构、照片、拆机、接口或规格推断 |
| Estimated | 基于计算、行业 benchmark 或成本模型估算 |
| Unknown | 当前没有足够可靠证据 |

结论不得把 `Inferred / Estimated` 写成 `Confirmed`。

---

# 17. Sources

每条独立列出来源，优先官方资料、技术文档、用户手册、Wiki、行业媒体、深度评测和工程社区。

```markdown
## Sources
- [Source description](URL)
- [Source description](URL)
```
