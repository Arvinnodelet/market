# Product Report Template v3

> **Purpose:** 将产品研究从“参数说明书”转化为“系统能力 → 用户价值 → 竞争差异 → 战略意义 → 未来演进”的证据驱动报告。

## 1. Product Definition & Positioning

- Product / generation:
- Launch timing:
- Target users:
- Primary use cases:
- Core problem solved:
- Market / price position:
- Positioning evidence:

## 2. Portfolio Role

说明产品在公司产品矩阵中的角色，以及共享的平台、技术、零件、软件和生态。

| Dimension | Analysis | Evidence |
|---|---|---|
| Product Line | | |
| Price Position | | |
| Performance Position | | |
| Technology Role | | |
| Shared Platform | | |
| Ecosystem Role | | |
| Upgrade Path | | |

## 3. User Problem & Workflow

```text
User Problem
 ↓
Current Workflow / Pain Point
 ↓
Product Intervention
 ↓
New Capability
 ↓
Workflow Improvement
 ↓
User / Economic Value
```

必须解释“用户为什么需要”，而不仅是“适合谁”。

## 4. Core Specifications

| Category | Specification | Value | Source | Status |
|---|---|---|---|---|

缺失数据使用 `Unknown / 未公开`。

## 5. System Architecture

```text
User / Input
     ↓
Software / Workflow
     ↓
Planning / Algorithms
     ↓
Control
     ↓
┌──────────┬──────────┬──────────┐
│ Sensing  │Actuation │Processing│
└────┬─────┴────┬─────┴────┬─────┘
     └──────────┼──────────┘
                ↓
        Physical Process
                ↓
              Output
                ↑
             Feedback
```

说明 data flow、control flow、energy/material flow、feedback loop。

## 6. Product Capability Map

| Technology / Subsystem | Mechanism | System Capability | Product Effect | User Value | Evidence |
|---|---|---|---|---|---|

使用：

```text
Component → Subsystem → Technology Cluster → System Capability → Workflow Capability → User Value
```

## 7. Core Technology System

选择 **2–4 个 Technology Clusters** 深挖，不按零件目录平均展开。

### 7.x [Technology Cluster]

1. Problem
2. Legacy limitation
3. Architecture
4. Mechanism
5. Hardware / sensors / actuators
6. Software / algorithms
7. Closed loop
8. Key parameters
9. Capability created
10. Product / user effect
11. Reliability / failure modes
12. Manufacturing / cost effect
13. Trade-offs
14. Competitor difference
15. Copyability / defensibility
16. Next constraint
17. Strategic significance

推荐使用：

```text
Problem
 ↓
Technology Cluster
 ↓
Mechanism
 ↓
Closed Loop
 ↓
Capability
 ↓
Product / User Value
 ↓
Competitive Difference
 ↓
Strategic Value
```

## 8. Software & Algorithms

| Layer | Implementation | Sensing / Computation | Capability | Effect on Hardware | Evidence |
|---|---|---|---|---|---|
| Firmware | | | | | |
| Control | | | | | |
| Calibration | | | | | |
| Algorithm / AI | | | | | |
| App | | | | | |
| Cloud | | | | | |

区分 monitoring / calibration / closed-loop control。

## 9. Materials / Consumables / Process

| Material | Machine Requirement | Validated Workflow | Performance | Cost | Lock-in | Evidence |
|---|---|---|---|---|---|---|

必须区分 `Supported / Validated / Optimized`。

## 10. UX & Workflow

| Dimension | Evidence | Mechanism | User Effect | Assessment |
|---|---|---|---|---|
| Setup | | | | |
| Calibration | | | | |
| Operation | | | | |
| Error Recovery | | | | |
| Maintenance | | | | |
| Software | | | | |
| Support | | | | |

## 11. Reliability & Service

| Failure / Risk | Physical Mechanism | Detection | Mitigation | User Impact | Confidence |
|---|---|---|---|---|---|

## 12. Manufacturing & Economics

| Dimension | Analysis | Confidence |
|---|---|---|
| BOM Structure | | |
| Major Cost Drivers | | |
| Assembly Complexity | | |
| Wiring / Harness | | |
| Calibration | | |
| DFM / DFA | | |
| Automation Potential | | |
| Serviceability | | |
| Supply Chain Risk | | |

所有成本、BOM、毛利等推算必须标记 `Estimated` 并写明假设。

## 13. Competitive Benchmark

选择 2–4 个直接竞品。

| Dimension | Product | Competitor A | Competitor B | Underlying Difference | Capability Effect | Trade-off |
|---|---|---|---|---|---|---|
| Architecture | | | | | | |
| Motion / Process | | | | | | |
| Sensing | | | | | | |
| Control | | | | | | |
| Materials | | | | | | |
| Software | | | | | | |
| Ecosystem | | | | | | |
| Reliability | | | | | | |
| Economics | | | | | | |

### Competitive Defensibility

回答：

> Why can the competitor not simply copy the visible feature?

```text
Visible Feature
 ↓
Underlying Capability
 ↓
Complementary Assets
 ↓
Replication Difficulty
 ↓
Defensibility
```

## 14. Product / Technology Evolution

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
Next Constraint
```

| Generation | Limitation | Technology Change | New Capability | Strategic Meaning | Next Constraint |
|---|---|---|---|---|---|

## 15. Strategic Assessment

### Technology Strategy
- 核心技术平台是什么？
- 哪些能力可跨产品复用？

### Product Strategy
- 产品如何把技术能力转成定位？

### Competitive Position
- 结构性优势是什么？
- 哪些优势只是短期执行优势？

### Defensibility
- 技术、制造、数据、软件、供应链和生态分别提供什么复制门槛？

### Economic / Manufacturing Implication
- 技术是否改善 BOM、良率、装配、校准、服务或单位产出？

## 16. Future Outlook

未来必须从当前瓶颈推导，不写泛化趋势：

```text
Current Capability
 ↓
Remaining Bottleneck
 ↓
Why It Matters
 ↓
Technology Enabler
 ↓
Company Existing Capability
 ↓
Competitive / Economic Pressure
 ↓
Likely Evolution
 ↓
Strategic Consequence
```

### Forecast Classification

- **Fact** — confirmed statement
- **Trend** — observable industry direction
- **Inference** — evidence-based deduction
- **Scenario** — conditional possibility
- **Estimate** — quantitative projection

### Horizons

- Near term: 0–2 years
- Mid term: 2–5 years
- Long term: 5+ years

不得把推断路线写成公司已确认 roadmap。

## 17. Overall Assessment

最终用 1–3 个高密度段落回答：

```text
What the company built
 → Why it works
 → What capability it creates
 → Why users care
 → Why competitors care
 → Why it is difficult to copy
 → What constraint comes next
 → Where the product is likely to evolve
```

不要重复参数表和功能列表。

## 18. Evidence & Confidence

| Status | Meaning |
|---|---|
| Fact | 来源明确陈述 |
| Verified | 多个可靠来源确认 |
| Reported | 可靠第三方报告 |
| Inferred | 工程推理 / 结构证据 |
| Estimated | 计算 / benchmark 推算 |
| Assessment | 分析判断 |
| Unknown | 证据不足 |

## Sources

优先官方产品页、手册、技术文档、软件仓库、release notes、专利、认证、公司材料；其次专业评测、长期测试、拆解和工程社区。

```markdown
## Sources
- [Source description](URL)
```
