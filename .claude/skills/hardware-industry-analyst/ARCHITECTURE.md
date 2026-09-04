# Hardware Industry Analyst Architecture

## 1. System Model

```text
User Question
     ↓
SKILL.md — orchestration
     ↓
Research Type + Domain Detection
     ↓
Frameworks — how to investigate
     ↓
Domains — what matters technically
     ↓
Evidence — how reliable the claims are
     ↓
Playbooks — how to execute recurring deep dives
     ↓
Research + Analysis + Evaluation
     ↓
Templates — how to structure output
     ↓
Report
```

Reference reports are optional side inputs used only for output-style and depth calibration.

## 2. Layer Responsibilities

| Layer | Question | Contents |
|---|---|---|
| SKILL | How should the agent operate? | routing, workflow, quality gates |
| Frameworks | What should be investigated and how should it be evaluated? | company, product, technology, market, competition, ecosystem, financial |
| Domains | What is technically important in this category? | taxonomy, workflow, technology model, subsystems, software, algorithms, sensors, electronics, materials, reliability |
| Evidence | Why should this claim be trusted? | source hierarchy, confidence, fact/inference rules |
| Playbooks | How should a recurring task be executed? | teardown, BOM, competitor comparison, launch, roadmap, supply chain, cost |
| Templates | How should the result be presented? | company, product, technology, market, competition, ecosystem, financial |
| Reference Reports | What output standard is useful as a precedent? | optional structure, density, depth, formatting examples |

## 3. Domain Architecture

A mature Domain uses the following structure:

```text
Domains/<domain>/
├── domain.md
├── technology-model.md
└── knowledge/
    ├── Core Technology
    ├── Hardware / Subsystems
    ├── Software
    ├── Algorithms
    ├── Sensors
    ├── Electronics / Control
    ├── Materials / Consumables
    └── Reliability / Service
```

### Domain Lifecycle

```text
Scaffold
  ↓
Domain Model complete
  ↓
Technology Model established
  ↓
Core Knowledge modules established
  ↓
Active
  ↓
Repeated research / validation
  ↓
Continuous refinement
```

- **Scaffold**: routing entry exists, but technical model and knowledge coverage are incomplete.
- **Active**: sufficient Domain Model + Technology Model + core Knowledge coverage exists for production research.

### Responsibilities inside a Domain

| File | Responsibility |
|---|---|
| `domain.md` | Defines what the domain is, product taxonomy, workflow, research scope, benchmarks, terminology and knowledge map. |
| `technology-model.md` | Defines how domain technologies are organized, connected, measured and causally related; maps technology nodes to Knowledge. |
| `knowledge/*.md` | Stores reusable technical knowledge: principles, components, parameters, mechanisms, failure modes and long-term reference facts. |

Do not force all domains to contain identical knowledge files. A UV printer may need printhead, UV ink, curing, RIP, color management, sensors and control; an FDM printer may need motion, extrusion, hotend, firmware, sensors and materials; a robot vacuum may need SLAM, perception, navigation, drive, battery and docking.

The Domain technology model is not a second evaluation framework. It defines the technical system; `Frameworks/technology.md` defines how that system is evaluated.

## 4. Research Routing

### Product question
`product.md + technology.md + relevant Domain technology-model.md + relevant Domain knowledge + product-report.md`

### Company question
`company.md + technology.md + relevant Domain technology-model.md + relevant Domain knowledge + company-report.md`

### Technology question
`technology.md + relevant Domain technology-model.md + relevant Domain knowledge + technology-report.md`

### Market question
`market.md + competition.md + domain.md + market-report.md`

### Ecosystem question
`ecosystem.md + relevant Domain knowledge + ecosystem-report.md`

### Financial question
`financial.md + company.md + relevant evidence + financial-report.md`

### Competitor question
`competition.md + relevant Domain knowledge + competitor-comparison.md + competition-report.md`

### Teardown question
`product.md + Domain knowledge + teardown-analysis.md`

### BOM / cost question
`product.md + cost-structure-analysis.md + bom-estimation.md`

### Roadmap question
`technology.md + product history + technology-roadmap.md`

## 5. Evidence Flow

```text
Source
  ↓
Evidence
  ↓
Fact / Verified / Reported
  ↓
Inference / Estimate
  ↓
Assessment
```

No silent upgrades are allowed:

```text
Inference  ≠ Fact
Estimate   ≠ Public Data
Reported   ≠ Confirmed
```

## 6. Reference Report Policy

Reference reports are **optional**.

Use one when a suitable existing report can improve consistency of presentation, for example:

- chapter organization
- table density
- technical decomposition depth
- ASCII diagrams / matrices
- parameter presentation
- Sources formatting
- overall report depth

Do not use a reference report as a substitute for research. Its facts, numbers and conclusions must be independently verified before reuse.

If no suitable report exists, proceed directly with Frameworks, Domain Model, Technology Model, Knowledge, Evidence and Templates. Do not force cross-domain report matching merely to obtain a reference.

If the user explicitly specifies a report as a reference, read it and use it only for the requested comparison of structure, depth or presentation unless the user separately asks to investigate its factual claims.

## 7. Knowledge Lifecycle

```text
Research
   ↓
Evidence Collection
   ↓
Verification
   ↓
Analysis
   ↓
Reusable Insight
   ↓
Domain Knowledge Update
   ↓
Future Research
```

Only stable and sufficiently verified information should be promoted into long-term Domain knowledge. Temporary prices, promotions and unverified speculation should remain research evidence rather than permanent knowledge.

## 8. Design Principle

The system standardizes **how research is performed**, not the exact content of every industry.

The core semantic distinction is:

```text
Framework
= How to research / evaluate

Domain
= What matters in this category

Technology Model
= How the category's technologies connect and create capability

Knowledge
= What each technology actually is

Evidence
= Why a claim can be trusted

Playbook
= How to execute a recurring analysis task

Template
= How findings are presented

Reference Report
= Optional precedent for output style / depth
```

That makes the same Skill extensible from:

```text
FDM 3D Printer
UV Printer
Laser Engraver
Robot Vacuum
Pool Robot
Robot Lawn Mower
        ↓
Future Hardware Domains
```

without creating a separate Skill for each product category.
