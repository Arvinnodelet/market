# Technology Analysis Framework

## Objective

Evaluate the technical architecture, innovation level, manufacturing feasibility, reliability, scalability, and competitive advantages of a hardware product's subsystems. Identify engineering tradeoffs — not just list specifications.

> 💡 本文件定义 **如何评估**（评估维度、输出模板）。**评估什么**（具体子系统）由 `Domains/<domain>/technology.md` 定义。

---

## Evaluation Methodology

### Per-Subsystem Assessment

对于每个子系统，评估以下维度：

| Criterion | Weight | What to Assess |
|---|---|---|
| **Performance** | 30% | Raw metrics vs segment peers at same price |
| **Innovation** | 20% | Truly novel? Self-developed? Industry-first? |
| **Reliability** | 20% | Field failure rate, known issues, design robustness |
| **Cost Efficiency** | 15% | Performance per BOM ¥ vs competitors |
| **Manufacturability** | 15% | Ease of assembly, calibration burden, automation potential |

### Cross-Cutting Assessment

| Criterion | What to Assess |
|---|---|
| **Architecture Coherence** | Do subsystems work well together? Or are they stitched from different suppliers? |
| **Integration Depth** | How many functions shared across fewer chips/sensors? (sensor fusion, combo ICs) |
| **Upgrade Headroom** | Can this architecture support next-generation features without redesign? |
| **Supplier Dependency** | How many single-source components? What happens if key supplier disrupted? |

---

## Technology Evolution Assessment

| Aspect | What to Evaluate |
|---|---|
| **Current Generation** | What's the state of the art? Who leads? |
| **Trajectory** | Where is this technology heading in 2–5 years? |
| **Disruption Risk** | What could make this approach obsolete? |
| **Commoditization Risk** | Is this advantage defensible, or will everyone have it soon? |

---

## Overall Technology Assessment

**Output Template**:

```
### Subsystem Assessments
(substitute actual subsystem names from domain technology.md)
Subsystem A:    [Leading / Competitive / Behind — with specifics]
Subsystem B:    [Leading / Competitive / Behind — with specifics]
Subsystem C:    [Leading / Competitive / Behind — with specifics]

### Innovation Assessment
Truly novel:        [list]
Industry-standard:  [list]
Behind peers:       [list]

### Engineering Tradeoffs Identified
1. [Tradeoff] → [Why they chose A over B]
2.

### Architecture Diagram
[ASCII art of system architecture]

### vs Best Competitor
Better at:   [specific subsystems — with why]
Worse at:    [specific subsystems — with why]
Key difference: [the one architectural decision that most defines this technology]

### Future Evolution Direction
[What will the next generation improve? What's the ceiling of this architecture?]
```
