# Product Analysis Framework

## Objective

Analyze a specific hardware product from engineering, user experience, manufacturing, and competitive perspectives. Produce a recommendation: Buy / Consider / Skip.

---

# 1. Product Positioning

| Attribute | Data | Source |
|---|---|---|
| **Manufacturer** | | |
| **Series / Tier** | | |
| **MSRP** | | Official store |
| **Street Price** | | Retail channels |
| **Release Date** | | Press release |
| **Status** | Active / EOL / Announced | |
| **Target User** | Beginner / Enthusiast / Prosumer / Professional / Industrial | |
| **Predecessor** | (if upgrade) | |

**Positioning Check**: Does the price match the specs vs competitors at the same price point?

---

# 2. Technical Architecture

> ⚠️ **子系统清单来自领域的 `technology.md`**。每项子系统展开以下评估：
> - 关键指标采集 + 段位均值对比
> - 自研 vs 外购（对护城河的影响）
> - 定性评估 vs 同价位段竞品

## Subsystem Assessments

| Subsystem | Spec Highlights | vs Segment Average | Self-Dev? | Assessment |
|---|---|---|---|---|
| | | | | |
| | | | | |
| | | | | |

> 填写规则：从领域的 `technology.md` 的子系统清单中选取与本品相关的子系统，对每个子系统进行指标采集和定性评估。

**Technical Assessment**: ___ (summary across subsystems)

---

# 3. User Experience

| Dimension | Assessment |
|---|---|
| **Out-of-Box Experience** | Setup time, onboarding steps |
| **First Use Quality** | Default settings results |
| **Software Experience** | App/slicer/controller quality, cloud features |
| **Noise Level** | dB at 1m, quiet mode? |
| **Maintenance Burden** | Frequency, difficulty, part availability |
| **Reliability** | Known issues, failure modes, community complaints |
| **Support Quality** | Response time, documentation quality, community help |

---

# 4. Manufacturing Perspective

| Dimension | Estimate / Assessment |
|---|---|
| **Est. BOM Cost** | |
| **Assembly Complexity** | Part count, harness complexity, calibration steps |
| **DFM Quality** | Snap-fit vs screws, modular vs monolithic |
| **Serviceability** | How easy to replace common failure parts? |
| **Est. Gross Margin** | (MSRP − BOM) ÷ MSRP |

---

# 5. Competitive Benchmark

Compare against 2–3 direct competitors in the same price tier (±20%):

| Dimension | This Product | Competitor A | Competitor B |
|---|---|---|---|
| **Price** | | | |
| **Key Spec 1** | | | |
| **Key Spec 2** | | | |
| **Key Spec 3** | | | |
| **Key Feature** | | | |
| **Calibration / Setup** | | | |
| **Software** | | | |
| **Ecosystem** | | | |

**Competitive Position**: Better than peers on ___. Worse than peers on ___.

---

# 6. Strategic Assessment

**Output Template**:

```
### Assessments
Technical:        [Leading / Competitive / Behind]
User Experience:  [Leading / Competitive / Behind]
Value (specs/$):  [Leading / Competitive / Behind]
Manufacturing:    [Leading / Competitive / Behind]

### Verdict: 🟢 Buy / 🟡 Consider / 🔴 Skip

### Strengths
1.
2.
3.

### Weaknesses
1.
2.
3.

### Best For
- User type A
- Use case B

### Not For
- User type C

### vs Top Competitor
Better at:
Worse at:
Choose this if: [decision rule]
Choose competitor if: [decision rule]
```
