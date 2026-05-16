---
id: c-000097
type: source
title: "The Founder's Playbook — Anthropic（2026-05-16）"
source: "https://cdn.prod.website-files.com/6889473510b50328dbb70ae6/69fe2a55b93bb0732b1fe33c_The-Founders-Playbook-05062026_v3%20(1).pdf"
raw: ".raw/articles/founders-playbook-2026-05-16.md"
publisher: Anthropic
date: 2026-05-06
ingested: 2026-05-16
tags:
  - startup
  - ai-native
  - anthropic
  - claude-cowork
  - founder
status: active
---

# The Founder's Playbook — Anthropic（2026-05-16）

Anthropic 发布的 35 页创业者指南，系统描述 AI 原生创业公司从构想到规模化的完整路径。核心产品矩阵：**Claude**（研究与战略）、**Claude Code**（产品构建）、**Claude Cowork**（运营自动化）。

## 核心主张

> "The bottlenecks are no longer what you can build, but what you choose to build."
> "AI compresses quarters into weeks."

AI 时代创业者的工作未变——找真实问题、构建解决方案、规模化；变的是路径，AI 把过去以季度计的工作压缩成以周计。

## 三种 Claude 工具面的使用边界

> "The three share the same Claude underneath; what changes is the workspace around it."

| 任务类型 | 用哪个 | 原因 |
|----------|--------|------|
| 一个问题、改写、快速头脑风暴 | **Claude Chat** | 快、对话、无需配置 |
| 研究/分析/从你的文件构建完成的文档 | **Claude Cowork** | 文件夹访问、连接器、技能、定时运行 |
| 编写/测试/交付软件 | **Claude Code** | 代码库访问、diff、git、开发环境 |

---

## 四阶段创业生命周期

→ 详见：[[concepts/AI原生创业生命周期]]

| 阶段 | 核心任务 | Claude 角色 | 退出条件 |
|------|----------|-------------|----------|
| **Idea** | 验证 PMF 假设 | 研究、竞品分析、反驳 | 用户访谈+数据支撑的假设 |
| **MVP** | 构建可用原型 | 编码、架构决策、安全扫描 | 真实用户的可重复使用模式 |
| **Launch** | 建立可持续系统 | 运营自动化、流程设计 | 系统在创始人缺席时仍运行 |
| **Scale** | 从构建者到对外执行官 | GTM 执行、企业基础设施 | 可持续盈利/IPO就绪/被收购 |

## Chapter 3: Idea Stage 详解

### Idea Stage 退出三问
离开 Idea Stage 需要对三个问题都回答"是"：
1. **问题真实且具体吗？** 能准确说出谁有这个问题、多频繁、多严重、他们现在怎么解决？
2. **你的方案真正解决了问题吗？** 不是你一开始假设的问题，而是验证过程揭示的问题（有时不一样）
3. **有足够信号值得构建 MVP 吗？** 不需要确定性，但需要足够多的定性证据让"提交 MVP"是有理由的决定，而非信仰行为

### Idea Stage 四大挑战

**① 把构建当成验证（最危险）**
> "42% of startups failed because they built something nobody wanted."

AI 消除了构建的技术门槛后，"想法 → 原型"变得极快，但原型不是验证。原型是压力测试工具，用于与潜在用户对话——**对话本身才是真正的证据**。

**② 过早规模化**
AI 工具太强大，很容易在验证问题-方案契合之前就扩大执行。会在不知情的情况下偏离正轨。

**③ 确认偏见被 AI 放大**
> "Confirmation bias now comes with a research engine."

向 AI 提要求支持性证据，它就会找到；要求它给你估算市场规模，它会找到让 TAM 看起来可融资的数字。用 AI 反向操作（devil's advocate）才是解药：**让 Claude 论证为什么竞争对手会成功而你不会**。

**④ 竞争者忽视（Competitor Neglect）**
创始人会因为专注自己的愿景而系统性地低估竞争对手。让 Claude 分析竞品**为什么比你更好**、**为什么客户会选择他们**。

### Idea Stage 关键工作流

**市场研究：**
- 构建 TAM/SAM/SOM 模型，压力测试假设背后的前提
- 识别市场是扩张、整合还是成熟（影响时机和差异化判断）
- 按层级绘制竞争对手图：直接竞争者/间接竞争者/潜在收购方/邻近玩家
- 识别 3 个外部趋势（监管/技术/人口），评估是顺风还是逆风

**客户发现：**
- 用 Claude 设计访谈框架——正确的问题、正确的顺序
- 核心原则：问**相关的过去**（"上次你遇到这个问题时发生了什么？"），不问**假设性未来**（"你会使用这样的产品吗？"）
- **每 5 次访谈后**：让 Claude Cowork 综合笔记，产出两个列表：支持假设的证据 vs 挑战假设的证据。如果第一个列表明显更长，让 Claude 判断这是数据本身的反映还是你想听到的东西

**Claude Cowork 自动化访谈运营：**
- 基于目标画像研究和整理潜在受访者列表（含职位/公司类型/资历）
- 批量起草个性化外发邮件
- 通过 MCP 接入 Gmail + Google Calendar 管理跟进线程、安排访谈
- 自动在定义的节奏发送 follow-up（如第7天未响应者）并更新跟踪表

---

## Chapter 4: MVP Stage 详解

### MVP Stage 退出条件
真实产品-市场契合的证据：特定可识别的用户群觉得产品足够有价值，愿意：
- **回来（留存）**
- **为此付费（营收）**
- **告诉别人（推荐）**

### MVP Stage 挑战详解

**① 智能体技术债** → [[concepts/智能体技术债]]
> "Without specs and architectural constraints written down somewhere the AI can read, each session re-derives foundational decisions from scratch, and those decisions drift."

AI 技术债与普通技术债的区别：普通技术债累积缓慢可以管理，AI 技术债**复利式增长**——没有约束文件的情况下，每次 session 都从零推导基本决定，决定会漂移，最终得到没有一致心智模型的代码库，"不是因为任何单个部分很差，而是因为这些部分从来没有被设计成配合的"。

**② 虚假 PMF（最具心理迷惑性）**
早期势头（创始人朋友、HN 头版、portfolio 公司用户）不是 PMF。这些是昙花一现的力量。**核心指标**：
- **Sean Ellis 测试**：问活跃用户"如果不能再用这个产品你感觉如何？"如果 40%+ 回答"非常失望"——这是有意义的 PMF 信号
- **努力测试**：PMF 前，留存需要创始人不断干预和维护；PMF 后，产品自己开始"拉"用户。**这种努力方向的转变是最清晰的信号之一**

**③ 无摩擦功能蔓延**
当构建近乎免费时，总有一个更酷的 feature 或 edge case 值得处理。传统上工程师时间的成本是对抗蔓延的自然约束，现在这个约束消失了。每个单个的添加都是可辩护的，但产品会超出原始边界并失去方向。

解法：**在构建开始前写下范围文档**——产品做什么/刻意不做什么/什么用户证据才能证明增加新功能是对的。把决策点从"我们应该构建这个吗？"移到"足够多的用户告诉我们没有这个就无法获得价值了吗？"

**④ 安全漏洞（AI 生成代码的固有风险）**
> "The hard truth is that agentic coding tools generate code that works, not code that is inherently secure."

功能代码容易验证（有效或无效），安全漏洞是隐形的直到被利用——没有自然的反馈循环提醒创始人有问题。MVP 上线前必须进行安全审查。
- Claude Code Security（有限 beta）：扫描代码库，找安全漏洞并建议定向补丁
- 重点审查：认证和会话处理、API 响应中的数据暴露、输入验证和注入风险、已知漏洞的依赖

### MVP Stage 关键实践

**CLAUDE.md 工作流：**
- 在打开 Claude Code **之前**，先用 Claude 定义架构原则、应避免的依赖、正在做的权衡
- 每次 session 开始：重新审视范围文档 + 提供 CLAUDE.md 架构上下文
- 每次 session 结束：更新 CLAUDE.md，记录构建了什么、做了什么决定、引入了什么假设（每次 5 分钟文档 = 便宜的保险，对抗架构漂移）

**预设量化目标（在第一个用户之前）：**
- 设置留存基准
- 定义激活标准
- 明确 Day 7 和 Day 30 目标
- 定义你的产品的**假阳性长什么样**：注册但不激活？有收入但无留存？初期热情但无复购？

**3 次迭代诊断（如果还没有 PMF 信号）：**
完成 3 个或更多迭代周期后，给 Claude 你的留存数据、用户反馈、最初问题假设，问三个问题：
1. 数据中有没有某个细分用户群表现与其他人不同？
2. 设计价值和实际体验价值之间的差距是定位问题还是产品问题？
3. 当前产品要达到真正 PMF，什么条件必须成立？这个情景鉴于你的数据是否现实？

---

## Chapter 5: Launch Stage 详解

### Launch Stage 退出三条件
1. **增长可重复且渠道驱动**：不只在留住用户，还在通过特定渠道可预测地获取用户；CAC/LTV/回收期是你知道且能捍卫的数字
2. **产品能处理生产工作负载**：基础设施已加固，安全合规到位，可靠性在真实生产条件下成立
3. **运营无需创始人瓶颈**：流程和自动化就位，你不再是亲自处理支持、分诊、Sprint 规划或报告的人

### Launch Stage 挑战详解

**① 技术债来收账**
MVP 代码库为速度和验证构建，够好但有快捷方式。生产流量、新功能、增长复杂性开始暴露这些快捷方式。

解法：系统性架构审计 → Claude Code 找结构弱点/测试覆盖空洞/重构候选 → 喂给 Claude 排序修复工作（跨多个 Sprint）

**② 创始人成为瓶颈**
从"做工作"过渡到"设计做工作的系统"是创业生命周期中最难的转变之一。迹象：
- 应该一小时处理的决策现在要一周才能轮到你
- 支持请求堆积因为只有你知道答案
- 运营任务只有在你个人记得的时候才发生

**解法**：全面审计你正在亲自处理的一切（最小任务到最高风险决策），识别什么可以系统化、可以委托、什么真正值得创始人时间。

**③ 过早扩张（会杀死 PMF）**
新市场看起来像增长机会，但扩张进入与原始市场有意义不同的市场会引入新的用户行为、合规要求、支付基础设施——你的产品不是为此设计的。你会失去清晰解读自己数据的能力，同时还在忽视原始用户群。

**④ 安全合规不再可推迟**
有了真实用户、真实数据，可能还有企业合同，安全漏洞从理论风险变成真实的暴露风险。合规要求（SOC 2/GDPR/HIPAA）在处理客户数据/支付的那一刻就适用了。

### Launch Stage 三工具协同

> "When Claude Code builds the product, Claude Cowork builds the company around it, and Claude helps operationalize this product and organizational knowledge, a small team can run like a company N× its size."

**运营 OS**（Claude Cowork 实现）：
- Sprint 节奏（scheduling sprint ceremonies）
- 最小规格模板（minimum spec template）
- Bug 分类决策树（bug triage decision tree）
- 周报（weekly metrics brief，从真实数据源自动拉取）

---

## Chapter 6: Scale Stage 详解

### Scale Stage 创始人角色转变
从构建者 → **对外执行官**（analyst briefings、IPO roadshows）。个人日常工作越来越多地围绕公司本身——治理、合规姿态、财务控制、战略叙事。

### Scale Stage 四大挑战

**① 委托运营层**（心理 + 结构双重挑战）
- 委托太多太快 → 关键决策失去只有创始人能提供的上下文
- 委托太慢 → 创始人成为瓶颈

**把机构知识转化为可扩展系统**：识别只存在于创始人头脑中或未文档化的工作流，然后把它们编码进有文档、可审计、可转移的系统。

**② 建立 GTM 功能**
创始人主导销售、Product Hunt 帖子、早期客户关系这种有机增长有天花板。规模化需要真正的 GTM 引擎：
- 用 Claude 构建：市场细分、消息架构、分析师关系策略、销售剧本、面向投资者的指标叙事
- 每个受众（公开投资者、企业买家、分析师）有自己的词汇和评估标准
- 用 Claude Cowork 执行：内容管道、外发序列、分析师简报后勤、PR 节奏、CRM 卫生、管道报告

**③ 扩展技术运营至企业级**
企业买家不只评估产品，他们评估你是否能成为可靠的基础设施合作伙伴：
- 专用支持功能（定义响应时间）
- 技术文档（新客户工程团队可以实际使用的）
- 日志/监控/事件响应工具
- 可观测层（让 SLA 真正可执行）

**④ 建立 GTM 产品营销基础设施**
交互式演示环境、集成文档、沙盒租户、API 参考、技术单页——买家期望在技术上评估你的产品，一个 Loom 视频和销售 Deck 在 Scale 阶段不再足够。

### Scale Stage 护城河构建

**数据飞轮** → [[concepts/数据飞轮复利]]
行为信号（接受/拒绝哪些输出）→ 产品改进 → 更多使用 → 更多数据。一页护城河叙事需要：飞轮如何运转 + 已运转多久 + 资源充足的竞争对手今天开始需要多久追上（通常：≥2年）

**领域专业知识 → AI 上下文的复利**
通过扩展对话、项目、记忆，把行业术语/监管陷阱/edge case 告诉 Claude：
- 通用 AI 医疗账单工具在 340B 药物计划索赔时失败，但你的工具有专用逻辑
- 这种专业知识随时间复利——竞争对手根本找不到

**工作流锁定** → [[concepts/工作流锁定]]
> "Your test suite becomes a map of your moat." 每发现一个通用竞品会出错的 edge case 就加一个测试。

---

## Chapter 7: Same job, new rules

> "The bottlenecks are no longer what you can build, but what you choose to build."

AI 时代创业者的工作未变——找真实问题、构建解决方案、规模化。变的是路径：
- 验证：数月 → 一个下午
- 原型：需要联合创始人 → 清晰的问题 + 几次编码 session
- Launch 就绪：pre-launch 冲刺 → 持续工作流
- 运营：早期雇员救火 → AI 处理，团队专注判断

---

## 关键概念

## 案例公司

| 公司 | 模式 |
|------|------|
| Carta Healthcare | 用 Claude 处理 22,000 例外科手术，数据抽取时间减少 66% |
| Anything | 让 150 万用户无需写代码即可构建软件产品 |
| Cogent | 用 Claude 自动化企业安全漏洞全生命周期管理 |
| Airtree | 用 Claude Cowork 统一原本散落在 12 个工具中的运营数据 |
| Duvo | 完全基于 Claude + Agent SDK 的采购/供应链 AI 代理 |
| Zingage | 家护机构 24/7 自动化运营，结构化工具调用协调 EMR |
| Kindora | 非营利人创建的慈善机构-资助方智能匹配平台，MCP 连接器直接在 Claude 内访问 |
| Wordsmith | 律师转 CTO 创建的法律合同 AI，工程团队用 Claude Code 构建 |
| GC AI | 用领域专业知识构建法务 AI，内置公司专属剧本和风险容忍阈值 |

## 资源

- Claude Code 文档、最佳实践、高级用户技巧
- Claude Cowork 入门
- Anthropic Startups Program（免费 API credits、最高速率限制、创始人活动邀请）

## 关联

- [[entities/Anthropic]]
- [[entities/ClaudeCowork]]
- [[concepts/AI原生创业生命周期]]
- [[concepts/智能体技术债]]
- [[concepts/创始人编排者角色]]
- [[concepts/数据飞轮复利]]
- [[concepts/工作流锁定]]
- [[domains/Claude-Code]]
