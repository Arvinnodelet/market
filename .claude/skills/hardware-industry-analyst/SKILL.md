---
name: hardware-industry-analyst
version: 2.1.0
description: Analyze consumer hardware products, companies, technologies, ecosystems, competition, markets, manufacturing, and economics across multiple hardware domains.
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

# Hardware Industry Analyst

## 1. Purpose

This skill is a generic hardware research and analysis system for 3D printers, UV printers, laser engravers, robot vacuums, pool robots, lawn mowers, sensors, and other consumer/prosumer hardware.

The system separates four layers:

```text
Research Process
      ↓
Frameworks  ← what must be investigated
      ↓
Domain      ← what matters in this hardware category
      ↓
Evidence    ← how reliable each claim is
      ↓
Analysis / Evaluation
      ↓
Report
```

### Core principles

- Research before evaluation.
- Frameworks define the investigation skeleton.
- Domains define the technical model, terminology, taxonomy, workflow, subsystems, and benchmarks.
- Evidence controls confidence; distinguish fact, verified finding, report, inference, estimate, and unknown.
- Existing reports define output density; reuse structure and depth standards, never conclusions or data.
- Engineering reasoning is preferred over marketing language.
- Unknown is an acceptable result; never manufacture specifications.

## 2. Supported Domains

| Domain ID | 中文名 | English | Status |
|---|---|---|---|
| `fdm-3d-printer` | 桌面 FDM 3D 打印机 | Desktop FDM 3D Printer | Active |
| `robot-vacuum` | 扫地机器人 | Robot Vacuum | Active |
| `laser-engraver` | 激光雕刻机 | Laser Engraver | Active |
| `pool-robot` | 泳池清洁机器人 | Pool Robot | Active |
| `lawn-mower` | 割草机器人 | Robot Lawn Mower | Active |
| `uv-printer` | UV 打印机 | UV Printer | Ready to add |

新增硬件品类优先创建 `Domains/<domain>/`，而不是创建新的专项 Skill。最小启动内容是 `domain.md`；`technology.md` 和 `knowledge/` 随研究积累。

## 3. Research Categories

- Company — 公司能力、产品版图、技术、生态、制造、财务、竞争战略
- Product — 单品定位、规格、架构、子系统、软件、耗材、体验、制造、成本、竞品、演进
- Technology — 技术原理、实现、算法、性能、路线、竞品方案、权衡
- Ecosystem — 软件、耗材、配件、云平台、开放接口、用户社区、锁定效应
- Competition — 玩家、产品、技术、价格、生态、商业模式、竞争位置
- Market — 市场定义、规模、需求、区域、竞争、技术、渠道、预测
- Financial — 收入、利润、成本结构、现金流、估值、经营效率

## 4. Workflow

### Step 1 — Detect Domain + Research Type

优先读取项目级 Domain Configuration；没有明确配置时，根据用户关键词和产品特征判断领域与研究类型。

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

`technology` 对 Company/Product 仍为强制项，但技术深度根据任务和产品定位动态调整。

### Step 3 — Load Domain Model

必须读取 `domain.md`；存在时按需读取 `technology.md` 和 `knowledge/*.md`。缺少知识模块不是错误，可以先通过 WebSearch 建立事实，再把验证过且长期复用的信息沉淀到 Domain knowledge。

### Step 4 — Read Reference Report (MANDATORY)

正式生成报告前必须发现并完整读取至少 1 份同领域或同报告类型的已有 Markdown 报告，并提取：章节结构、表格密度、技术拆解粒度、ASCII 图密度、产品参数粒度和 Sources 格式。

只能继承表达方式和深度标准，不得复制参考报告的结论、数字或未经验证的判断。没有同领域报告时，使用其他领域最接近的报告，并说明可能存在领域适配限制。

### Step 5 — Build Evidence Base

关键事实按以下证据层级处理：

```text
Official explicit
      ↓
Multiple reliable sources
      ↓
Credible third-party report
      ↓
Engineering inference
      ↓
Estimate / calculation
      ↓
Unknown
```

核心架构、传感器配置、材料、价格、发布日期、性能指标、成本等不得仅凭搜索摘要或营销文案直接升级为高置信结论。

### Step 6 — Analyze

明确区分：

- Fact：来源明确陈述
- Verified：多来源交叉验证
- Inference：根据结构、照片、拆机、接口、规格等推断
- Estimate：计算或行业基准估算
- Assessment：基于证据形成的工程判断

涉及 BOM、毛利、可靠性、供应链等无法直接验证的数据时，必须写明假设和置信度。

### Step 7 — Generate Report

报告回答三个层次：

```text
What is it?
    ↓
How does it work / how good is it?
    ↓
Why does it matter commercially and competitively?
```

## 5. Report Structures

### Company
公司概况 → 发展历程 → 业务/产品版图 → 产品线 → 技术体系 → 生态系统 → 制造与供应链 → 商业模式/财务 → 竞争格局 → 战略判断 → Sources

### Product
产品定义 → 市场定位 → 产品线角色 → 用户与使用场景 → 核心规格 → 系统架构 → 核心子系统 → 软件/算法 → 材料/耗材 → 体验 → 可靠性与维护 → 制造与服务 → 成本/经济性 → 竞品 → 产品演进 → 综合判断 → Sources

### Technology
技术定义 → 工作原理 → 系统架构 → 硬件实现 → 软件/算法 → 关键性能 → 工程难点 → 可靠性 → 制造与成本 → 竞品方案 → Trade-offs → 演进路线 → 趋势

### Ecosystem
生态边界 → 硬件 → 软件 → 耗材/配件 → 云服务 → 开放接口 → 社区 → 用户锁定 → 商业价值 → 竞品生态比较

### Competition
市场边界 → 玩家地图 → 产品矩阵 → 技术路线 → 价格带 → 生态 → 制造/供应链 → 商业模式 → 竞争位置 → 潜在变化

### Market
市场定义 → 产品分类 → TAM/SAM/SOM（仅在数据足够时）→ 历史规模 → 增长驱动 → 用户结构 → 渠道 → 区域 → 竞争格局 → 技术趋势 → 供应链 → 未来情景

### Financial
收入 → 增长 → 毛利 → 费用 → 现金流 → 成本结构 → 单位经济模型 → 估值/融资 → 资本效率 → 风险 → 与业务战略的关系

## 6. Technical Depth Rules

技术深度动态调整，不再强制所有 Company/Product 报告的技术章节固定占 40–60%。

| Task | Recommended technical share |
|---|---:|
| Company overview | 30–50% |
| Flagship product | 30–50% |
| Standard product | 20–35% |
| Entry/basic product | 10–25% |
| Pure technology study | 50–70% |

旗舰产品或核心技术通常选择 2–3 个最具差异化的技术进行深拆。每项技术应覆盖原理、系统架构、硬件实现、材料/器件、安装位置、关键参数、控制/算法、可靠性/失效模式、代际演进、跨型号差异、竞品本质差异、优势与局限。

200–400 行仅作为高深度参考区间，不再作为机械硬性要求。真正标准是技术拆解足以解释设计原因及其对性能、成本、可靠性和竞争结果的影响。

## 7. Cross-Product Analysis

覆盖 ≥3 个型号时，优先建立横向矩阵：核心规格、传感器、运动/执行机构、核心模块、软件能力、材料/耗材兼容、生态兼容、价格与定位等。

传感器矩阵使用 `Confirmed`、`Reported`、`Inferred`、`Unknown` 等证据状态；不要用 emoji 作为正文信息载体。

## 8. Evaluation Model

研究阶段与最终评价阶段分开。

### Technical
创新性、性能、可靠性、复杂度、可扩展性、可制造性

### User
易用性、首次使用、维护、软件、校准、售后

### Value
规格/价格、功能密度、耗材/服务成本、升级成本

### Manufacturing
BOM、装配复杂度、DFM、良率、校准、可维修性

### Business
收入模式、毛利逻辑、渠道、生态、竞争壁垒

### Strategic
产品在公司产品线中的角色、平台价值、技术路线意义、竞争防御性

默认综合判断输出：
- Product Strengths
- Product Weaknesses
- Technical Position
- User Value
- Manufacturing Position
- Competitive Position
- Strategic Role
- Overall Assessment

只有用户明确要求购买建议时，才使用 Buy / Consider / Skip。

## 9. Source Rules

优先级：官方产品页/技术文档/用户手册/服务手册/Wiki/认证资料 → 厂商采访/发布会/技术演讲/专利 → 高质量行业媒体和专业评测 → 深度拆机/工程社区 → 经交叉验证的供应链信息。

禁止把搜索引擎结果页当作来源；禁止用单一营销文案证明复杂技术结论；禁止将推断写成官方事实；禁止将估算值写成公开财务数据。

Sources 使用独立条目：

```markdown
## Sources
- [Source description](URL)
- [Source description](URL)
```

## 10. Output Rules

- 使用 Markdown。
- 参数优先使用表格。
- 技术架构优先使用 ASCII 图、流程图、矩阵。
- 关键判断必须可追溯到证据或明确工程推理。
- 对未知信息明确写 `Unknown / 未公开`，不要填猜测数字。
- 报告正文不暴露内部 Framework / Domain 文件路径和文件名。
- 正文不使用 SWOT 矩阵、星级评分、emoji 作为评价体系。
- 不使用管理咨询式空泛叙述替代工程分析。
- 不为了追求篇幅而重复同一结论。

## 11. Continuous Knowledge Build-Up

```text
首次研究 → domain.md + WebSearch
       ↓
建立事实与产品模型
       ↓
验证关键结论
       ↓
沉淀 technology.md / knowledge/*.md
       ↓
下一次研究直接复用
       ↓
WebSearch 主要用于更新、验证和发现变化
```

每次研究结束后，优先沉淀新术语、子系统定义、技术路线、benchmark、核心器件/供应商、常见失效模式、竞品差异和高质量长期来源。一次性价格、短期促销、未经验证的论坛猜测不要直接写入长期知识库。

## Change Log

| Version | Date | Change |
|---|---|---|
| V2.1.0 | 2026-09-02 | 升级为研究 + 证据 + 评价体系；Company/Product 结构分离；技术深度动态化；新增 Market/Research/Evidence 体系；取消默认 Buy/Consider/Skip |
| V2.0.1 | 2026-07-01 | 强制读取已有报告作为格式标尺；增加技术深度约束；禁止 SWOT/emoji/星级评分 |
| V2.0.0 | 2026-06-30 | 从 3DP 专项 Skill 重构为通用 Skill + Domain 插件 |
| V1.1.1 | 2026-06-17 | 禁止在报告中泄露内部框架文件名 |
| V1.1.0 | 2026-06-16 | 强化框架组合和技术深度 |
| V1.0.0 | 2026-06-16 | 初始版本 |
