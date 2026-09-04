---
name: hardware-industry-analyst
version: 3.0.0
description: Evidence-driven hardware industry research and analysis system that converts product, technology, competition, manufacturing, ecosystem, and market evidence into causal, strategic, and future-roadmap conclusions.
triggers:
  - 3D打印
  - 3D printer
  - FDM
  - FFF
  - CoreXY
  - Bambu Lab
  - 拓竹
  - Creality
  - 创想三维
  - Prusa
  - Voron
  - Anycubic
  - Elegoo
  - Qidi
  - AMS
  - CFS
  - 涡流传感器
  - eddy current
  - hotend
  - 热端
  - slicer
  - 切片
  - multi-color
  - 多色打印
  - UV打印机
  - UV printer
  - UV ink
  - UV墨水
  - 喷墨打印
  - 扫地机
  - 扫地机器人
  - robot vacuum
  - Roborock
  - 石头
  - Ecovacs
  - 科沃斯
  - Dreame
  - 追觅
  - iRobot
  - Roomba
  - Narwal
  - 云鲸
  - LDS
  - 基站
  - 避障
  - 激光雕刻
  - laser engraver
  - laser cutter
  - xTool
  - LaserPecker
  - 镭雕
  - 泳池机器人
  - pool robot
  - pool cleaner
  - Aiper
  - Beatbot
  - 割草机器人
  - robot lawn mower
  - robotic mower
  - Husqvarna
  - Segway Navimow
---

# Hardware Industry Analyst v3

## 1. Mission

This skill is a reusable research and analysis system for consumer/prosumer hardware. Its purpose is not merely to collect specifications, but to explain:

```text
What was built
      ↓
Why it works
      ↓
What capability it creates
      ↓
Why users care
      ↓
Why competitors care
      ↓
Why it is difficult to copy
      ↓
What constraint comes next
      ↓
Where technology / product / strategy is likely to evolve
```

### Core principle

**Research completeness is necessary; analytical causality is mandatory.**

A report is incomplete if it lists technologies without explaining their system effect, competitive meaning, or strategic consequence.

---

## 2. Analytical Engine

All major conclusions should follow this causal chain where applicable:

```text
Evidence
  ↓
Fact / Observation
  ↓
Mechanism / Cause
  ↓
Capability
  ↓
Product / User Effect
  ↓
Economic Effect
  ↓
Competitive Effect
  ↓
Strategic Significance
  ↓
Future Implication
```

The analyst must distinguish the following layers:

1. **Fact** — directly stated or directly observed.
2. **Mechanism** — engineering explanation of how/why the fact produces an effect.
3. **Capability** — reusable system capability created by the mechanism.
4. **Product Effect** — measurable or observable product consequence.
5. **User / Economic Value** — why the effect matters in workflow, cost, quality, time, or adoption.
6. **Competitive Effect** — how it changes relative position.
7. **Strategic Significance** — why it matters to the company's long-term position.
8. **Future Implication** — what constraint or opportunity logically follows.

Never jump directly from a feature to a strategic conclusion without the intermediate reasoning.

---

## 3. Mandatory Analysis Models

Before writing a high-depth report, load the relevant files under `Analysis/`:

- `analysis-model.md` — universal causal reasoning and evidence-to-conclusion model.
- `technology-analysis.md` — technology cluster, closed-loop, trade-off, and evolution analysis.
- `future-analysis.md` — bottleneck-driven future analysis.

Additional analysis models may be added for competition, manufacturing, economics, ecosystem, or other recurring reasoning tasks.

### Capability model

Use:

```text
Component
  ↓
Subsystem
  ↓
System Capability
  ↓
Workflow Capability
  ↓
Product Positioning
```

A component is not automatically a capability. A capability must explain what the integrated system can now do better.

### Defensibility model

When assessing a potential moat:

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

Ask why a competitor cannot simply reproduce the visible feature.

---

## 4. Supported Domains

| Domain ID | 中文名 | English | Status |
|---|---|---|---|
| `fdm-3d-printer` | 桌面 FDM 3D 打印机 | Desktop FDM 3D Printer | Active |
| `robot-vacuum` | 扫地机器人 | Robot Vacuum | Active |
| `uv-printer` | UV 打印机 | UV Printer | Active |
| `laser-engraver` | 激光雕刻机 | Laser Engraver | Scaffold |
| `pool-robot` | 泳池清洁机器人 | Pool Robot | Scaffold |
| `lawn-mower` | 割草机器人 | Robot Lawn Mower | Scaffold |

**Active** means the domain has a usable domain model and knowledge layer. **Scaffold** means routing exists but the technical model should be expanded before assuming parity with Active domains.

For a new hardware category, create `Domains/<domain>/` rather than creating another specialized Skill. Minimum content is `domain.md`; add `technology-model.md` and `knowledge/` as reusable knowledge accumulates.

---

## 5. Research Types

- Company — company capability, portfolio, technology, ecosystem, manufacturing, financials, strategy
- Product — positioning, architecture, subsystems, software, materials, UX, manufacturing, economics, competition, evolution
- Technology — principle, architecture, implementation, algorithms, performance, trade-offs, competition, evolution
- Ecosystem — software, consumables, accessories, cloud, APIs, community, lock-in, monetization
- Competition — players, products, technology routes, price, ecosystem, manufacturing, business model, competitive position
- Market — definition, segmentation, demand, scale, regions, channels, competition, technology, forecast
- Financial — revenue, growth, margin, costs, cash flow, unit economics, valuation, capital efficiency

---

## 6. Research Workflow

### Step 1 — Detect scope

Identify domain, research type, time boundary, target company/product, comparison set, and user objective.

### Step 2 — Load Framework

| Research type | Required framework |
|---|---|
| Company | company + technology |
| Product | product + technology |
| Technology | technology |
| Ecosystem | ecosystem |
| Competition | competition + financial |
| Market | market + competition |
| Financial | financial + company |

`technology` remains mandatory for Company/Product research, but depth depends on product importance.

### Step 3 — Load Domain Model

Read `domain.md`. When available, use `technology-model.md` and relevant `knowledge/*.md`.

Do not assume Scaffold domains have complete technical knowledge.

### Step 4 — Load Analysis Models

For high-depth work, load the relevant analysis models before drafting conclusions.

At minimum for Product/Technology research:
- causal analysis
- technology cluster analysis
- trade-off analysis
- evolution analysis

For strategic/future sections:
- future analysis
- competitive defensibility
- chapter handoff model

### Step 5 — Reference Report

A high-quality historical report may be used as a **benchmark for depth and expression**, especially when the user explicitly identifies it as the reference.

Use it for:
- chapter organization
- analytical depth
- table density
- technical decomposition
- architecture diagrams
- parameter presentation
- Sources style

Do not inherit its facts, conclusions, market data, cost data, or technical judgments without re-verification.

### Step 6 — Build Evidence Base

Evidence priority:

```text
Official explicit evidence
      ↓
Multiple reliable sources
      ↓
Credible third-party evidence
      ↓
Engineering inference
      ↓
Estimate / calculation
      ↓
Unknown
```

Important architecture, sensors, materials, performance, price, launch date, cost, and financial claims require appropriate evidence quality.

### Step 7 — Build System Model

Before writing long prose, map:

```text
Market / User Problem
      ↓
Product Architecture
      ↓
Subsystems
      ↓
Technology Clusters
      ↓
System Capabilities
      ↓
User Workflow
      ↓
Economic / Manufacturing Effects
      ↓
Competitive Position
```

### Step 8 — Analyze

Convert evidence into causal conclusions. Separate facts from inferences and assessments.

### Step 9 — Analyze Evolution

For major technologies and products use:

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

### Step 10 — Analyze Future

Use the future model:

```text
Current State
      ↓
Unresolved Problems / Bottlenecks
      ↓
Evolution Drivers
      ↓
Technology Enablers
      ↓
Existing Company Capabilities
      ↓
Competitive / Economic Pressure
      ↓
Likely Evolution
      ↓
Strategic Consequence
```

Do not turn an inferred roadmap into a confirmed company plan.

### Step 11 — Quality Audit

Before finalizing, verify:

- every major conclusion has evidence or explicit reasoning;
- technology sections explain capability, not only features;
- major technologies are grouped into coherent clusters;
- each major technology includes trade-offs;
- competitive comparisons explain architectural/capability differences;
- future outlook is derived from identified bottlenecks and capabilities;
- facts, reports, inferences, estimates, and assessments are clearly separated;
- no unsupported precision is introduced;
- conclusions do not repeat without adding a new analytical layer.

---

## 7. Technology Analysis Rules

### 7.1 Technology Cluster is the default unit

Do not treat every feature as a standalone core technology.

A Technology Cluster integrates related hardware, sensing, actuation, software, algorithms, and control into one system capability.

Recommended structure:

```text
Problem
  ↓
Technology Cluster
  ├─ Architecture
  ├─ Hardware
  ├─ Sensors
  ├─ Actuators
  ├─ Software / Algorithms
  └─ Control
  ↓
System Capability
  ↓
Product / User Value
  ↓
Competitive Advantage
  ↓
Strategic Value
```

### 7.2 Core technology selection

Prioritize technologies that satisfy several of these conditions:

- materially change product capability;
- solve a major legacy limitation;
- integrate multiple subsystems;
- materially affect cost, reliability, throughput, quality, or UX;
- differentiate the product from competitors;
- create reusable platform capability;
- are difficult to reproduce without complementary assets;
- influence future product evolution.

Do not select a technology only because marketing calls it “new”.

### 7.3 Closed-loop analysis

When feedback is present, explain:

```text
Sensing
  ↓
State Estimation
  ↓
Decision / Control
  ↓
Actuation
  ↓
Physical Result
  ↓
Feedback
```

Identify what is sensed, what is estimated, what is controlled, the actuator, latency, calibration dependency, failure mode, and resulting capability.

### 7.4 Trade-off is mandatory

For each major technology, answer:

- What problem does it solve?
- What does it make better?
- What does it make worse?
- What cost/complexity does it introduce?
- What new failure modes appear?
- Why did the company accept the trade-off?
- Under what market position is the trade-off rational?

### 7.5 Recommended depth

For flagship products or strategically important technologies, normally deep-dive **2–4 Technology Clusters** rather than many shallow features.

Each deep dive should cover, where evidence permits:

1. Problem
2. Legacy limitation
3. Architecture
4. Mechanism
5. Hardware / sensors / actuators
6. Software / algorithms
7. Closed loop
8. Key parameters
9. Capability created
10. Product/user effect
11. Reliability / failure modes
12. Trade-offs
13. Competitor difference
14. Copyability / defensibility
15. Next constraint
16. Strategic significance

---

## 8. Product Capability Analysis

The report must distinguish:

```text
Specification ≠ Capability ≠ User Value
```

Example reasoning pattern:

```text
Higher acceleration
      ↓
Motion system + frame + control + vibration compensation
      ↓
Higher stable printing throughput
      ↓
Shorter job time at acceptable quality
      ↓
Higher workflow productivity
```

Do not claim user value from a specification alone when system integration determines the actual outcome.

---

## 9. Competitive Analysis

Compare architectures and capabilities, not only headline specifications.

For every major difference, ask:

1. What is different?
2. Why is it different?
3. What capability does the difference create?
4. Does the competitor solve the same problem another way?
5. What are the trade-offs?
6. Why can one competitor not simply copy the other's visible feature?
7. Does the difference matter to the target user or only on paper?

Preferred comparison:

| Dimension | Product A | Product B | Underlying difference | Capability effect | Strategic meaning |
|---|---|---|---|---|---|

---

## 10. Strategic Analysis

Use:

```text
Technology Capability
      ↓
Product Capability
      ↓
Portfolio Role
      ↓
Market Position
      ↓
Economic Effect
      ↓
Competitive Advantage
      ↓
Defensibility
      ↓
Strategic Option
```

Strategic analysis must answer:

- What platform capability has been built?
- Is it reusable across products?
- Does it improve cost, speed, quality, UX, or reliability?
- Does it strengthen ecosystem lock-in or channel position?
- Does it change the company's feasible product roadmap?
- Is the advantage structural, execution-based, temporary, or easily copied?

Avoid generic statements such as “technology strengthens competitiveness” unless the causal mechanism is demonstrated.

---

## 11. Future Outlook

Future analysis is not a generic trend section.

It must start from current constraints:

```text
Current Capability
      ↓
Remaining Bottleneck
      ↓
Why the Bottleneck Matters
      ↓
Enablers Becoming Available
      ↓
Company's Existing Assets
      ↓
Competitive / Economic Pressure
      ↓
Likely Evolution
      ↓
Strategic Consequence
```

Classify forward-looking statements as:

- **Fact** — confirmed current/future statement from the company or authoritative source.
- **Trend** — externally observable industry direction.
- **Inference** — reasoned conclusion from evidence.
- **Scenario** — conditional future possibility.
- **Estimate** — numerical or quantitative projection.

Never present inferred roadmap items as confirmed launches.

Preferred horizons:

- Near term: approximately 0–2 years
- Mid term: approximately 2–5 years
- Long term: 5+ years

Use flexible horizons when the technology cycle does not fit these ranges.

---

## 12. Evidence Labels

Use consistently:

- **Fact** — source explicitly states it.
- **Verified** — independently confirmed by multiple reliable sources.
- **Reported** — credible third party reports it, but independent confirmation is limited.
- **Inference** — derived from evidence and engineering reasoning.
- **Estimate** — calculated or benchmarked approximation.
- **Assessment** — analyst judgment based on evidence.
- **Unknown** — insufficient evidence.

When confidence matters, explicitly state confidence and assumptions.

---

## 13. Cross-Product Analysis

When covering ≥3 models, use a horizontal matrix.

Recommended dimensions:
- positioning
- price
- build volume / core specifications
- motion architecture
- sensing
- actuation
- thermal system
- software / algorithms
- materials
- automation
- ecosystem
- manufacturing complexity
- upgrade path
- strategic role

Sensor and architecture states should use `Confirmed`, `Reported`, `Inferred`, or `Unknown` rather than emoji.

---

## 14. Research-Type Report Structures

### Company
Company definition → history → portfolio → market positioning → technology system → product capability → ecosystem → manufacturing/supply chain → business/financials → competition → strategic analysis → future outlook → overall assessment → Sources

### Product
Use `Templates/product-report-v3.md` as the preferred structure:

Product definition → portfolio role → user/market problem → specifications → architecture → capability map → core technology system → software/algorithms → materials/ecosystem → UX → reliability/manufacturing → competitive benchmark → evolution → strategic analysis → future outlook → overall assessment → evidence → Sources

### Technology
Technology definition → problem → technology cluster → architecture → mechanism → hardware → sensing → actuation → software/control → closed loop → performance → reliability → manufacturing/economics → trade-offs → competitive difference → evolution → strategic significance → future outlook → Sources

### Ecosystem
Ecosystem boundary → hardware → software → consumables/accessories → cloud → APIs → community → workflow integration → switching cost → monetization → competitive ecosystem comparison → strategic implications

### Competition
Market boundary → player map → product matrix → architecture/technology routes → price → ecosystem → manufacturing → business model → capability comparison → competitive position → future shifts

### Market
Market definition → segmentation → scale → demand → users → channels → regions → competition → technology → supply chain → economics → scenarios → strategic implications

### Financial
Revenue → growth → margin → operating expenses → cash flow → cost structure → unit economics → valuation/funding → capital efficiency → operational drivers → strategic relationship → risks

---

## 15. Technical Depth Rules

Technical depth is determined by analytical importance, not fixed word count.

| Task | Typical technical share |
|---|---:|
| Company overview | 30–50% |
| Flagship product | 30–50% |
| Standard product | 20–35% |
| Entry/basic product | 10–25% |
| Pure technology study | 50–70% |

A high-depth technology section is successful only when it explains design reasons and their impact on performance, cost, reliability, UX, manufacturing, and competition.

200–400 lines may be appropriate for a deep technology chapter, but line count is never the objective.

---

## 16. Output Rules

- Markdown only.
- Use tables for specifications and cross-product comparison.
- Use ASCII diagrams for architecture, control loops, technology chains, and evolution.
- Trace important conclusions to evidence or explicit reasoning.
- Mark unknowns as `Unknown / 未公开`.
- Never manufacture specifications, costs, financial figures, or roadmaps.
- Keep engineering terminology precise.
- Prefer mechanism and causal explanation over marketing language.
- Avoid generic consulting language.
- Do not repeat the same conclusion merely to increase length.
- Do not expose internal Framework / Domain file paths in the final report unless the user asks for methodology.
- Do not use SWOT, star ratings, or emoji as the core evaluation system.
- Sources must be independently listed at the end.

### Source format

```markdown
## Sources
- [Source description](URL)
- [Source description](URL)
```

---

## 17. Evaluation Model

Separate research from final assessment.

### Technical
Innovation, performance, reliability, complexity, scalability, manufacturability

### User
Setup, calibration, workflow, maintenance, software, service

### Value
Specification/price, functional density, consumable/service cost, upgrade cost

### Manufacturing
BOM, assembly complexity, DFM, calibration, yield, repairability

### Business
Revenue model, margin logic, channels, ecosystem, competitive moat

### Strategic
Portfolio role, platform value, technology-route significance, defensibility

Default final assessment:
- Product Strengths
- Product Weaknesses
- Technical Position
- User Value
- Manufacturing Position
- Competitive Position
- Strategic Role
- Key Uncertainties

Only use Buy / Consider / Skip when the user explicitly requests a purchasing recommendation.

---

## 18. Chapter Handoff

The report is a connected analytical system, not independent chapters.

```text
Product Architecture
      ↓
Technology Capability
      ↓
Product / Workflow Capability
      ↓
Competitive Position
      ↓
Economic / Manufacturing Effect
      ↓
Strategic Analysis
      ↓
Future Outlook
```

Later chapters must reuse and extend earlier conclusions.

Examples:
- A technology trade-off identified in the technology chapter should appear in manufacturing, UX, or competitive analysis where relevant.
- A capability identified in the product chapter should inform strategic positioning.
- A bottleneck identified in technology should become an input to future outlook.
- A competitive gap should be tested against the company's existing technology and manufacturing assets before predicting future moves.

---

## 19. Continuous Knowledge Build-Up

```text
Research
  ↓
Verified Evidence
  ↓
Reusable Domain Knowledge
  ↓
Technology Model
  ↓
Analysis Model
  ↓
Higher-quality Reports
  ↓
New Evidence / Corrections
  ↺
```

Knowledge files should capture reusable engineering knowledge. Analysis files should capture reusable reasoning models. Reports remain evidence-bound outputs, not permanent sources of truth.

### Final standard

The quality of this Skill is measured by whether it can move from:

**“The company has feature X.”**

to:

**“The company built X to solve problem Y; X works through mechanism Z; the integrated system creates capability A; that changes user/economic outcome B; it creates competitive effect C; the advantage is or is not defensible because of D; the next constraint is E; therefore the most plausible future evolution is F.”**
