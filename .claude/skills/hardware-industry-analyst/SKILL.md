---
name: hardware-industry-analyst
version: 2.0.0
description: Analyze companies, products, technologies, ecosystems, business models, manufacturing strategies, and market trends for consumer hardware robotics industries.
triggers:
  # === 3D Printer ===
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
  # === Robot Vacuum ===
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
  # === Laser Engraver ===
  - 激光雕刻
  - laser engraver
  - laser cutter
  - xTool
  - LaserPecker
  - 镭雕
  # === Pool Robot ===
  - 泳池机器人
  - pool robot
  - pool cleaner
  - Aiper
  - Beatbot
  # === Lawn Mower ===
  - 割草机器人
  - robot lawn mower
  - robotic mower
  - Husqvarna
  - Segway Navimow
---

> **Change List**：
> | Version | Date | Change Description |
> |---------|------|-------------------|
> | V2.0.1 | 2026-07-01 | Step 4 从可选升级为强制步骤（MANDATORY）：必须读取至少 1 份已有报告作为格式标尺；Step 5 新增技术特色篇幅要求（40-60%）、单技术深度要求（200-400 行）、禁止 SWOT/emoji/星级评分；Design Philosophy 新增"已有报告定义血肉密度"原则 |
> | V2.0.0 | 2026-06-30 | 架构重构 — 从 3DP 专项技能拆分为通用技能 + Domain 插件体系；新增扫地机/激光雕刻/泳池机器人/割草机器人领域 |
> | V1.1.1 | 2026-06-17 | Step 5 新增"禁止泄露框架文件名"规则 |
> | V1.1.0 | 2026-06-16 | Step 2 框架选择改为必选组合；Step 5 技术特色章节增加最小深度约束 |
> | V1.0.0 | 2026-06-16 | 初始版本 — 5 步分析工作流、4 维评估框架 |

# Hardware Industry Analyst

## Purpose

This skill provides a structured framework for researching and analyzing companies, products, technologies, ecosystems, and market trends in **consumer hardware robotics**. It supports multiple hardware domains through a plugin architecture — the same analytical rigor applies whether the product is a 3D printer, robot vacuum, laser engraver, pool robot, or lawn mower.

## Design Philosophy

```
CLAUDE.md          → 项目级治理（版本/命名/符号/数据来源）+ domain 声明
SKILL.md (本文件)   → 通用分析工作流 + 4 维评估维度 + 报告结构
Frameworks/        → 通用评估框架（与领域无关）
Domains/<domain>/  → 领域知识插件（domain.md + technology.md + knowledge/）
```

**核心原则**：
- **Frameworks** 定义"评估什么维度"（骨架）—— 告诉你需要覆盖哪些方面
- **Domains** 定义"评估什么内容"（领域知识）—— 告诉你该领域的术语、基准、子系统
- **已有报告** 定义"写成什么样"（血肉密度）—— 告诉你工程深度、表格风格、章节组织方式
- 新增一个硬件品类只需创建 Domain 插件，Frameworks 不变

---

## Supported Domains

| Domain ID | 中文名 | English | Status |
|---|---|---|---|
| `fdm-3d-printer` | 桌面 FDM 3D 打印机 | Desktop FDM 3D Printer | ✅ Active |
| `robot-vacuum` | 扫地机器人 | Robot Vacuum | ✅ Active |
| `laser-engraver` | 激光雕刻机 | Laser Engraver | ✅ Active |
| `pool-robot` | 泳池清洁机器人 | Pool Robot | ✅ Active |
| `lawn-mower` | 割草机器人 | Robot Lawn Mower | ✅ Active |

> 💡 **添加新领域**：复制 `Domains/_template/` → 填写 `domain.md`（最小启动）→ 将触发词添加到本文件的 `triggers` 清单。`technology.md` 和 `knowledge/*.md` 可选，首次调研后渐进补全。

---

## Analysis Workflow

### Step 1: Detect Domain & Research Category

**Domain Detection**：读取项目 `CLAUDE.md` 的 `Domain Configuration` 确定活跃领域。若无显式声明，通过用户在对话中使用的关键词自动匹配。

**Category**：识别研究类型 — Company / Product / Technology / Ecosystem / Competition / Market。

### Step 2: Load Frameworks

加载通用评估框架（`Frameworks/`）— 这些框架与领域无关，适用于所有硬件品类：

| Category | Required Frameworks | Rule |
|---|---|---|
| **Company** | `company.md` **+ `technology.md`** | 全景评估 + 至少 1 项独有技术深度拆解 |
| **Product** | `product.md` **+ `technology.md`** | 单品分析 + 关键子系统技术评估 |
| **Technology** | `technology.md` | 单项技术全维度拆解 |
| **Ecosystem** | `ecosystem.md` | 生态锁入与平台护城河 |
| **Competition** | `competition.md` + `financial.md` | 多玩家对比 + 财务健康度 |
| **Market** | `competition.md` | 市场规模、趋势与预测 |

`technology.md` 是 Company 和 Product 报告的强制加载项 — 确保每份报告都有工程深度。

### Step 3: Load Domain Knowledge

加载活跃领域的知识（`Domains/<domain>/`）：

1. **必须加载**：`domain.md` — 获取术语表、行业媒体列表、子系统清单、单位符号规范
2. **按需加载**：若 `technology.md` 存在 → 获取领域特定的子系统基准和架构权衡
3. **按需加载**：若 `knowledge/*.md` 存在 → 预加载 curated 技术知识（原理/路线/厂商/矩阵/趋势）
4. **缺失处理**：不存在的 knowledge 模块不作为错误——缺失的基准数据和知识通过 WebSearch 即时搜索补充。调研完成后，建议将验证过的关键发现沉淀到对应的 knowledge 文件中

### Step 4: Read Reference Report (MANDATORY)

> ⚠️ **此步骤不可跳过。** 跳过是导致输出质量偏差的首要原因。

**操作**：

1. 使用 `Glob` (`*.md`) 发现所有已有报告
2. **必须**使用 `Read` 完整读取至少 **1 份**与当前任务**同领域或同报告类型**的已有报告
3. 从参考报告中提取格式模式，作为输出标尺：

| 提取维度 | 具体关注 |
|---|---|
| **章节结构** | 章节编号方式（中文数字/阿拉伯数字）、层级深度、目录格式 |
| **表格风格** | 参数表格式（`\| 参数 \| 详情 \|`）、对比矩阵样式、表格密度 |
| **技术深度** | 每项核心技术占多少行、拆解到哪个粒度（材料/安装/演进/对比） |
| **ASCII 图密度** | 架构图、布置图、流程图的详细程度 |
| **产品详解方式** | 每个机型单独展开还是系列统述、参数表粒度 |
| **Sources 格式** | 末尾 Sources 是否带 URL、每条是否独立一行 |

**规则**：
- 禁止直接复制已有报告的结论或数据
- 若目标领域**完全无已有报告**（新领域首份报告），使用其他领域的已有报告作为格式参考，并在 Step 5 输出时注明"无同领域参考，深度可能不足"
- 若目标领域有报告但类型不同（如只有 Company 报告但要写 Product 报告），仍必须读取该报告作为风格参考

### Step 5: Generate Output

按以下结构产出报告（参考 `CLAUDE.md` 版本规范）。**结构顺序和占比以 Step 4 读取的参考报告为准**：

| 报告类型 | 结构 |
|---|---|
| **Company/Product** | 公司概况 → 发展历程与里程碑 → 产品线全景 → 各系列产品详解 → 配件与生态系统 → 产品对比矩阵 → 技术特色与核心优势（**占报告 40-60% 篇幅**）→ 市场定位与竞争格局 → 客户群体与选购建议 → [附录] → Sources |
| **Technology** | 概述 → 工作原理 → 硬件实现 → 软件/算法 → 性能分析 → 竞品对比 → 权衡 → 行业趋势 |
| **Competitor** | 市场格局 → 玩家概况 → 技术对比 → 产品对比 → 生态对比 → 商业模式 → SWOT → 展望 |
| **Market** | 摘要 → 市场定义 → 规模 → 需求驱动 → 竞争动态 → 技术趋势 → 区域 → 预测 |

**技术特色章节要求**（Company/Product 报告）：
- **篇幅**：技术特色章节应占报告总篇幅的 **40-60%**，是全篇最重的章节
- **数量**：至少选取 **2-3 个**该公司/产品**独有或行业领先**的技术做深度拆解
- **每个技术的拆解粒度**（以参考报告为标尺，单技术 200-400 行）：
  - 工作原理（含 ASCII 架构图/原理图）
  - 硬件实现（含材料选型、安装位置、关键参数）
  - 演进历史（该技术的代际变化，如有）
  - 各系列/各型号对比（表格跨系列汇总）
  - 与竞品方案的本质区别（是原理差异还是参数差异）
  - 优势与局限（客观陈述，不回避缺陷）
- **展示方式**：多用表格、ASCII 图、对比矩阵；少用 SWOT/星级评分/emoji

**全系传感器信息汇总**（Product 报告，覆盖 ≥3 款机型时推荐添加）：
- **位置**：技术特色章节末尾，深度技术拆解之后，作为所有传感器分析的横切总结
- **格式**：机型（行）× 传感器类型（列）二维矩阵表
- **图例**：`✅ 公开确认 | 🟡 行业推断/未公开确认 | — 未搭载 | 数字 已确认数量`
- **传感器列选取**：从该领域 subsystem 清单中提取所有感知/检测类传感器 + 通用传感器（IMU、霍尔、热敏电阻等）+ 机型独有的特殊传感器
- **表后附说明**：逐条解释每类传感器的数据来源、推断依据、边界条件，标注 EOL（†）和新品（🆕）
- **参考实现**：`元鼎智能_Aiper_产品报告_2026` §2.2d（泳池机器人）、`拓竹科技_BambuLab_产品报告_2026` §3.4（3D 打印机）

**Sources 格式**：
- 每条独立一行，格式为 `- [来源描述](URL)`
- 优先引用官方文档/Wiki、社区深度讨论、行业媒体评测
- 不引用搜索引擎结果页

**禁止事项**：
- 禁止泄露 `Frameworks/` 和 `Domains/` 下的文件名（用自然语言替代）
- 禁止在正文中使用 SWOT 矩阵、星级评分、emoji 表情符号
- 禁止使用"管理咨询"风格的叙述性段落替代技术参数表格

---

## Core Evaluation Dimensions

### Technology
- Innovation, reliability, complexity, scalability, manufacturability

### Cost
- BOM impact, manufacturing cost, service cost, upgrade cost

### User Experience
- Ease of use, calibration, maintenance, ecosystem integration

### Business
- Revenue model, competitive advantage, market position, growth potential

---

## Engineering Priorities

Prefer engineering reasoning over marketing claims. Always discuss:

- Architecture decisions
- Tradeoffs
- Reliability risks
- Supply chain implications
- Manufacturing implications

When information is incomplete:
- State assumptions clearly
- Provide confidence levels
- Distinguish facts from speculation

---

## Preferred Output Style

**Prefer:** tables, matrices, BOM breakdowns, architecture diagrams, engineering comparisons

**Avoid:** marketing language, vendor marketing claims, unsupported assumptions

---

## Repository Structure

```
Frameworks/                          ← 通用框架（领域无关）
├── company.md                       ← 公司全景评估
├── product.md                       ← 单品分析（引用领域 technology.md 的子系统清单）
├── technology.md                    ← 技术评估模板（定义评估维度，不定义具体子系统）
├── ecosystem.md                     ← 生态 & 平台护城河
├── competition.md                   ← 竞争格局
└── financial.md                     ← 财务分析

Domains/
├── _template/                       ← 🆕 新领域模板
│   ├── domain.md                    ← 领域元数据 + 触发词 + 术语表
│   ├── technology.md                ← 该领域的子系统清单 & 基准值
│   └── knowledge/                   ← 领域知识模块
├── fdm-3d-printer/                  ← 桌面 FDM 3D 打印机
├── robot-vacuum/                    ← 扫地机器人
├── laser-engraver/                  ← 激光雕刻机
├── pool-robot/                      ← 泳池清洁机器人
└── lawn-mower/                      ← 割草机器人
```
