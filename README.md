# Supervisor-Skills（HuangShiLab 维护版）

本仓库为 [黄适（Shi Huang）](https://github.com/shihuang)（香港大学牙科学院，[HuangShiLab](https://github.com/HuangShiLab)）维护的 fork，面向本实验室的科研写作、数据分析与项目管理场景。

**上游来源**：本项目 fork 自 [HKUSTDial/Supervisor-Skills](https://github.com/HKUSTDial/Supervisor-Skills)（骆昱宇，香港科技大学（广州）），上游内容以 [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) 协议开源，版权归 Yuyu Luo 及 HKUSTDial 团队所有，感谢吴垠、李伯岩、谢宇鹏对上游仓库的贡献。上游的 `handbook/` 与 `skills/` 下标注为原有的技能全部保留可用，其详细介绍见上游 README，此处不再复制。

## 为什么做这个 fork

先向上游致敬。骆昱宇教授发起这个项目时写下的动机，我几乎每一句都有共鸣：带学生、做评审这些年，我见过的是同一组困境——学生读遍"科研指南"面对自己的课题仍不知如何下笔；导师时间有限，没法对每个想法及时给出细致评估；论文写完，不确定逻辑是否严密、图表是否合格、行文有没有低级错误；以及 AI 时代的"能力鸿沟"——没有判断力和学术品味，再强的模型也只是高级玩具。骆教授的贡献在于把这个共识变成了可执行的技能框架，并把方法论系统地蒸馏出来。

但我自己的工作经验和他的不完全重叠，这正是我做 fork 而不是只用上游的原因。我在微生物组/宏基因组领域做干湿结合的研究：真实样品处理、宿主污染控制、株水平检测、benchmark 设计（2bRAD-M、Strain2bScan 这条线），同时承担期刊评审和企业合作的技术分析项目。这类项目里的坑有自己的形状：项目初期定下的总体框架执行中被反复遗忘；中间过程记录混进论文正文；关键结果在逻辑上撑不起关键结论，却被静默略过；AI 干一步停一步，跨会话就丢工作思路。这些教训不在任何通用科研指南里，只存在于自己的项目复盘中。

因此本 fork 的规则是：**上游的方法论框架原样保留；本实验室每次项目复盘得到的教训，持续蒸馏成新技能**——每个新技能都附真实反例档案，写明它从哪次失效中来、拦截机制加在哪一环。新增技能见下节。

---

## 核心：本 fork 新增技能

### supervisor —— 持续工作协议 + 交付前审查

**解决什么问题**：多步骤项目（如软件论文的 benchmark 设计与写作）中，AI 经常交付即停、遗忘项目初期定下的总体框架、把中间过程当正文、对不支持结论的关键结果静默略过。

**怎么来的**：本实验室真实项目（Strain2bScan benchmark 等）复盘的 5 个反例，每个规则都能回溯到具体失效场景（见 `references/project-cases.md`）。

**机制**：
- **持续工作**：工作台账外置到文件，每完成一项自动推进下一项；停止仅限四种白名单情形（全部完成 / 方向分叉需决策 / 技术阻塞 / 上下文水位），停止时必须输出恢复指引；
- **交付前审查**：框架对照、叙事结构（每图必指认论点，禁止按分析顺序罗列）、过程记录隔离（commit 号、运行日志、GitHub 链接一律不进正文，判据：删掉不影响读者理解科学结论的就是过程记录）、结论-证据匹配（矛盾必须主动报告，禁止静默略过）、统计措辞（禁用 "trend" 描述非显著结果）；
- **框架守卫**：项目总体设计（步骤、数据类型、评价指标、预期信号）持久化为文件，每次交付前对照，防止"提醒过一次又被遗忘"；
- **Token 预算**：台账与中间产物落盘、先定位后读文件、80% 水位写交接快照、保留失败记录等 7 条上下文纪律。

### skill-hygiene —— skill 编写与质检规范

**解决什么问题**：skill 写得很长却触发不准、加载浪费 token、规则空洞不可执行——包括"提示词给了仓库 URL 但 skill 根本没被加载"这类部署层失效。

**怎么来的**：整合公开实证研究（SkillReducer 对 55,315 个公开 skill 的分析：26.4% 缺路由描述、正文平均 60%+ 不可执行；规范压缩后 token 降 39–48% 而质量反升）与 context engineering 实践，证据与出处见 `references/evidence.md`。

**机制**：渐进式披露三级加载（description 只写"做什么+何时触发"、正文只放可执行规则、案例证据拆 references 并标注"何时读+关键词"）；三道质量门（忠实度 / 任务走查 / 瘦身门）；七项审查清单（含对上游贡献的协议与署名检查）。

### stats-evidence-audit —— 统计证据审查

**解决什么问题**：统计报告审查缺乏系统判据——伪重复、多重比较未校正、"trend" 包装非显著结果、只报 p 值不报效应量、图注缺统计要素，在微生物组数据（高维稀疏、组成性）中尤其高发。

**怎么来的**：与 [nature-skills](https://github.com/Yuan1z0825/nature-skills)（Apache-2.0）对比发现的缺口，维度划分参考其 nature-statistics；具体规则自撰，依据 ASA p 值声明、SAMPL 报告规范、组成性数据与伪重复经典文献（见 `references/stats-sources.md`）。

**机制**：8 项可判定审查维度（实验单位独立性、重复数定义、精确 p 值、多重比较校正、效应量与 CI、图注统计要素、跨章节数值一致性、阴性结果措辞）+ 统计小节起草规则；由 supervisor 审查清单第 5 条调用执行深度检查。

---

## 更新日志

| 日期 | 更新 |
|---|---|
| 2026-11-14 | 新增 `supervisor`（持续工作 + 交付审查 + Token 预算，含 5 个反例档案）；触发描述扩展至审稿场景；修复"停止白名单与 80% 水位规则冲突"（自审发现） |
| 2026-11-14 | 新增 `skill-hygiene`（skill 编写与质检规范，基于 55k+ skill 实证研究与 context engineering 证据） |
| 2026-11-14 | 新增 `stats-evidence-audit`（统计证据审查，补齐与 nature-skills 对比的缺口）；README 重写并增加"相关技能生态" |

## 目录结构

```
Supervisor-Skills/
├── skills/
│   ├── supervisor/                 # ⭐ 本 fork：持续工作 + 交付审查 + Token 预算
│   │   ├── SKILL.md
│   │   └── references/project-cases.md   # 5 个真实项目反例档案
│   ├── skill-hygiene/              # ⭐ 本 fork：skill 编写与质检
│   │   ├── SKILL.md
│   │   └── references/evidence.md        # 方法实证依据
│   ├── stats-evidence-audit/       # ⭐ 本 fork：统计证据审查
│   │   ├── SKILL.md
│   │   └── references/stats-sources.md
│   └── <上游原有技能 11 个>          # idea-evaluator, paper-writer, paper-polish 等，见上游 README
├── handbook/                       # 📖 上游科研与写作系统指南（保留）
└── assets/                         # 上游图片资源
```

## 相关技能生态

执行层任务优先调用 **[Yuan1z0825/nature-skills](https://github.com/Yuan1z0825/nature-skills)**（Apache-2.0）：Nature 风格写作/润色、投稿级科研图（含渲染 QA）、文献逐字段核验（nature-ref-verifier）、返修回复。本 fork 负责判断层（选题、叙事、统计审查、工作流），两仓库互补。

<<<<<<< HEAD
这里保留了系统性的理论框架，供你深入阅读和系统学习。只有理解了"道"，才能更好地使用"器"。

| 章节 | 内容 | 链接 |
|---|---|---|
| **第一章：宏观认识** | 从审稿人视角看论文质量（Novel Problem, Novel Method, Nice Story, Nice Presentation） | [1.1 如何评价一篇论文的质量](handbook/01_Preliminary/1.1_如何评价一篇论文的质量.md) / [博士生科研入门辅导](handbook/01_Preliminary/博士生科研入门辅导.pdf)|
| **第二章：Idea构思** | Idea的生命周期、5维思考框架（更高更快更强更省更广）、颠覆式创新 | [2.1 Idea生命周期](handbook/02_Idea_Generation/2.1_Idea的生命周期与能力匹配.md) / [2.2 更高更快更强](handbook/02_Idea_Generation/2.2_想Idea的思路_更高更快更强.md) / [2.3 颠覆式创新](handbook/02_Idea_Generation/2.3_进阶_如何做颠覆式创新.md) |
| **第三章：论文写作** | 科研论文全流程、Introduction思考模型、技术类/Benchmark类论文模板、写作Checklist | [3.1 全流程](handbook/03_Paper_Writing/3.1_完成一篇科研论文你需要做几件事情.md) / [3.2 Intro模型](handbook/03_Paper_Writing/3.2_Introduction写作的思考模型.md) / [3.3 技术类模板](handbook/03_Paper_Writing/3.3_技术类Full_Paper思考模板.md) / [3.4 Benchmark模板](handbook/03_Paper_Writing/3.4_Benchmark与Evaluation类论文思考模板.md) / [3.5 Checklist](handbook/03_Paper_Writing/3.5_写作细节与Checklist.md) |
| **第四章：科研作图** | 动机图、总览图、实验图的设计范式与绘图Checklist | [4.1 动机图](handbook/04_Scientific_Plotting/4.1_Motivated_Example_Figure.md) / [4.2 总览图](handbook/04_Scientific_Plotting/4.2_Solution_Overview_Figure.md) / [4.3 实验图](handbook/04_Scientific_Plotting/4.3_Experimental_Results_Figure.md) / [4.4 Checklist](handbook/04_Scientific_Plotting/4.4_绘图Checklist与工具速查表.md) |
| **第五章：前沿实战** | Vibe Research/Coding/Figure/Writing 入门与实战经验 | [5.1 入门指南](handbook/05_Vibe_Research/5.1_Vibe_Research与Vibe_Coding入门.md) / [5.2 实战经验](handbook/05_Vibe_Research/5.2_李伯岩实战经验分享与会议纪要.md) |
| **第六章：顶会案例** | Alpha-SQL (ICML'25)、AFlow (ICLR'25)、LEAD (VLDB'26) 写作思路剖析 | [6.1 Alpha-SQL](handbook/06_Case_Studies/6.1_ICML_2025_Alpha-SQL写作剖析.md) / [6.2 AFlow](handbook/06_Case_Studies/6.2_ICLR_2025_AFlow写作剖析.md) / [6.3 LEAD](handbook/06_Case_Studies/6.3_VLDB_2026_LEAD写作剖析.md) |

### 🛠️ Skills：提炼出的可执行 AI Skills

这里是本仓库的核心卖点！我们将上述理论经验蒸馏成了结构化的 Prompt/Skill 文件。你可以直接复制这些内容，导入到你的 AI 助手中（Claude、DeepSeek、Kimi 等均可）。

| 技能名称 | 功能描述 | 链接 |
|---|---|---|
| **Idea Evaluator** | 输入你的 Idea，AI 将根据"更高更快更强"5维框架和能力匹配表进行客观评估与打分 | [使用技能](skills/idea-evaluator/SKILL.md) |
| **Vibe Research Guide** | AI 辅助科研全流程指导：Vibe Coding / Vibe Figure / Vibe Writing | [使用技能](skills/vibe-research-workflow/SKILL.md) |
| **Supervisor** | 把长周期科研任务拆成外置台账、连续工作循环和交付前二值检查，防止中途丢状态或提前宣布完成 | [使用技能](skills/supervisor/SKILL.md) |
| **Delivery Evidence Audit** | 审查结论、源表、图表面板、补充材料编号和原始数据/转换链路的一致性，并逐条处置批注与修订 | [使用技能](skills/delivery-evidence-audit/SKILL.md) |
| **Supervisor Review** | 在最终交付前执行 frozen package、feedback disposition、证据一致性和 clean-checkout 的二值发布门禁 | [使用技能](skills/supervisor-review/SKILL.md) |
| **Project Experience Codifier** | 把重复事故、审稿发现和 benchmark 陷阱转化为 incident record、binary gate 和可复用 skill | [使用技能](skills/project-experience-codifier/SKILL.md) |
| **Computational Method Release Audit** | 一体化审计方法主张、truth set、benchmark comparator、event-level validation、taxonomy mapping、catalogue/metric-complete denominator、bootstrap target 和代码/数据归档 | [使用技能](skills/computational-method-release-audit/SKILL.md) |
| **Introduction Drafter** | 基于 Introduction 的 Flowchart 思考模型，输入研究动机，直接产出六段式 Intro 正文（引用经真实检索核验；也可只要大纲） | [使用技能](skills/intro-drafter/SKILL.md) |
| **Paper Writer** | 证据门控的论文正文写作：从单段到整篇，每个事实性声明可溯源到你的材料或核验过的文献，引用经独立核查，绝不编造 | [使用技能](skills/paper-writer/SKILL.md) |
| **Paper Polish** | 忠于原意的语言润色：改语法、去 AI 腔、把握措辞分寸、中文稿改写为投稿级英文，可能动到含义的改动逐条标出请你确认 | [使用技能](skills/paper-polish/SKILL.md) |
| **Deep Research** | 综述级文献深度调研：多视角检索、逐条引用核验、MECE 分类综合与交叉对比，产出逐条回答研究问题的 survey 报告 | [使用技能](skills/deep-research/SKILL.md) |
| **Tech Paper Template** | 基于"技术类Full Paper思考模板"，辅助你一步步梳理论文的完整逻辑链 | [使用技能](skills/tech-paper-template/SKILL.md) |
| **Benchmark Paper Template** | 专为 Benchmark/Evaluation 类论文设计，辅助梳理评估逻辑和实验设计 | [使用技能](skills/benchmark-paper-template/SKILL.md) |
| **Pre-Submission Reviewer** | 顶会审稿人视角！基于写作 Checklist 和英语语法易错点，对草稿进行全面审查 | [使用技能](skills/pre-submission-reviewer/SKILL.md) |
| **Figure Design Advisor** | 告诉 AI 你想表达什么，它会根据动机图/总览图/实验图的设计范式给出专业作图建议 | [使用技能](skills/figure-designer/SKILL.md) |
| **Draw.io Reconstruction** | 将参考图、论文图、架构图、幻灯片图或 UI 截图重建为可编辑 `.drawio` 文件，并导出 PNG 预览与视觉审计 | [使用技能](skills/drawio-reconstruction/SKILL.md) |
| **Rebuttal Guidance** | 基于条件说服模型，识别审稿人心态（X）、匹配 rebuttal 策略（Y），为每条 Weakness/Question 生成可执行的回应指导，含 concern 分类、语气建议、证据指针与完整性检查 | [使用技能](skills/rebuttal-guidance/SKILL.md) |

## 快速开始 (Quick Start)

把下方这段 Prompt 发给你的 AI 助手（Claude Code、Cursor、Codex 等）即可完成安装：
=======
## 快速开始
>>>>>>> fb7f34a (README: rewrite as HuangShiLab fork (remove upstream promo, own narrative, feature new skills))

```
Help me install Supervisor-Skills from https://github.com/HuangShiLab/Supervisor-Skills with Skills.
```

## License

上游内容（`handbook/`、`skills/` 下原有技能及 `assets/`）以 [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) 发布，版权归原作者及 HKUSTDial 团队；本 fork 新增内容（`skills/supervisor/`、`skills/skill-hygiene/`、`skills/stats-evidence-audit/` 及本 README）同样以 CC BY-NC-SA 4.0 发布，署名：Shi Huang / HuangShiLab。
