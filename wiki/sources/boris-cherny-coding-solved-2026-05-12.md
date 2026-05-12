---
address: c-000064
type: source
title: "Why Coding Is Solved, and What Comes Next — Boris Cherny（Sequoia Capital，2026-05-12）"
created: 2026-05-12
updated: 2026-05-12
tags:
  - anthropic
  - claude-code
  - software-development
  - sequoia
  - interview
status: active
source_url: "https://www.youtube.com/watch?v=SlGRN8jh2RI"
source_kind: youtube
people:
  - "[[people/BorisCherny]]"
entities:
  - "[[entities/Anthropic]]"
  - "[[entities/SequoiaCapital]]"
concepts:
  - "[[concepts/ProductOverhang]]"
  - "[[concepts/软件民主化]]"
  - "[[concepts/Loop机制]]"
related:
  - "[[sources/the-expanding-toolkit-2026-05-12]]"
  - "[[sources/fiona-fung-ai-native-engineering-2026-05-11]]"
  - "[[domains/Claude-Code]]"
---

# Why Coding Is Solved, and What Comes Next — Boris Cherny（Sequoia Capital，2026-05-12）

**演讲人：** [[people/BorisCherny]]（Claude Code 创始人，[[entities/Anthropic]]）  
**主持：** Lauren Reeder（[[entities/SequoiaCapital]]）  
**来源：** [YouTube](https://www.youtube.com/watch?v=SlGRN8jh2RI)  
**时长：** 约 45 分钟（含 Q&A）

---

## Claude Code 的起源

Boris 于 2024 年底加入 Anthropic 内部孵化器 **Anthropic Labs**（与 MCP、Desktop App 同期诞生，团队只有几个人）。起初他做 Claude Code 完全是"意外"——感受到了**产品过剩**（[[concepts/ProductOverhang]]）：模型能做的远超任何已有产品所能捕捉的。

- 2024 年底的 SoTA 仅是"按 Tab 补全一行代码"（Sonnet 3.5 时代）
- 感觉下一步是让 Agent 写全部代码 → 开始构建
- 头六个月完全不好用，个人使用率仅约 10%
- 最初发布也不是爆款；**指数增长始于 2026 年 5 月的 Opus 4**
- 此后每个模型版本（4.5 → 4.6 → 4.7）都有一次新的拐点

> "我们是在为下一个模型构建，这几乎是贯穿整个过程的想法。"

---

## "编程已被解决"

Boris 本人自 2025 年 10/11 月起，**100% 的代码由模型编写**。Claude Code 代码库（TypeScript + React，选择原因：当时对模型分布最友好）也是如此。

- **个人每日产出**：通常几十个 PR，某天创纪录 150 个 PR
- 大型复杂代码库、冷门语言仍有差距，但"答案通常是等下一个模型"
- 对整个行业而言：仍是 ~50% 解决，但轨迹明确

---

## 个人工作流：从手机管理数百个 Agent

Boris 现在主要用**手机**工作：Claude App → Code 标签页，同时有 5–10 个 session，每个 session 有若干 Agent，通常**几百个 Agent 并行**，每晚**几千个 Agent 做深度工作**。

### `/loop`（[[concepts/Loop机制]]）

> "Loop 是我目前认为最重要的功能。最简单但最有效的东西。"

原理：让 Claude 用 cron 调度一个**重复任务**，可以每分钟/每五分钟/每天触发。

Boris 正在运行的 loop 举例：
- **PR 保姆**：自动修复 CI、自动 rebase
- **CI 健康维护**：检测并修复 flaky test
- **Twitter 反馈聚类**：每 30 分钟抓取一次并聚类
- **Routines**（新功能）：同一机制的服务端版本，关闭笔记本电脑后继续运行

---

## 未来团队形态

- **更多跨学科 Generalist**：工程师同时精通设计、产品、数据科学
- **Anthropic 内部现状**：Claude Code 团队所有人（EM、PM、设计师、数据科学家、财务、用户研究）都写代码
- 专家身份不消失，但**每个人都会编程**
- 公司 Claude 实例之间通过 **Slack** 互相通信，协同解决 unknowns

---

## "SaaS 末日"论：七种商业护城河

引用 Hamilton Helmer《七种力量》（Seven Powers）框架分析 AI 对商业护城河的影响：

**会被削弱的护城河：**
- **切换成本**（Switching Costs）：模型可以帮你从一个工具迁移到另一个
- **流程力量**（Process Power）：4.7 可以"爬山"任何流程，给定目标就会迭代到完成

**仍然重要的护城河：**
- **网络效应**（Network Effects）
- **规模经济**（Scale Economies）
- **稀缺资源**（Cornered Resources）

**对创业公司的影响：**
- 未来 10 年的创业公司数量将是过去 10 年的 10 倍
- 小团队可以构建媲美大公司的产品，并正面竞争
- 大公司面临流程改造、内部阻力；**AI 原生创业公司没有这个包袱**

> "这是创业的最好时代，是成为一家初创公司的最好时代。"

---

## 编程民主化：印刷机类比

[[concepts/软件民主化]]

> "1400 年代，欧洲只有 10% 的人口识字……印刷机发明后 50 年，出版量超过此前一千年。书本价格下降 100 倍。数百年后，全球识字率达到 70%。"

Boris 的预测：
- 编程将像读写一样成为每个人都能做的技能（不需要"编程学位"）
- 速度比识字率普及**快得多**（不需要几百年）
- **最懂会计的人才是写会计软件的最佳人选**——编程是容易的部分，领域知识才是难的

---

## 产品 vs 模型：各占多少功劳？

一年前大约 50/50。随着模型越来越好，**harness（产品侧）的重要性相对下降**。

- 两年后：模型将更好地"自然做正确的事"
- 今天的 prompt injection 防护、权限模式、Human-in-the-loop 等安全机制**都会变得不那么重要**——模型会自己做对
- 产品重要性来自**细节打磨**，让用户全天使用时体验流畅

---

## Anthropic 内部领先在哪里？

**模型侧**：使用的是和外界一样的模型（Mythos 内测 → Opus 4.7 主力）

**领先的地方是组织结构和流程**：
- 公司内部零手写代码，连 SQL 都由模型生成
- Claude 实例全天候通过 Slack 通信协作
- 核心是"我们用了我们发布的所有东西"

---

## 多 Agent 并行化

**当前**：主要靠 prompting；4.7 会更自然地启动 loop（主动提议"我来每 30 分钟给你发报告"）

**未来**：不应该由工程师决定何时并行化——**模型应该自己判断**。如果用户还需要手动决定，那是产品设计问题。

---

## 云端 vs 本地模型

> "不重要——因为模型最终会自己决定。"

几年后模型会自行决定用云端还是本地资源来跑 Agent；这不再是工程师要操心的决策。

---

## 前瞻：正在构建的产品

- **Claude Design**（已提及，会越来越好）
- Claude Code 的近期更新（"coming weeks"）
- **/loop、/batch**：大规模并行 Agent 管理将持续改进
- **Computer Use**：另一个"现在建、等模型变好"的方向

---

## 关联

- [[people/BorisCherny]] — 演讲人，Claude Code 创始人
- [[entities/SequoiaCapital]] — 主办方
- [[concepts/ProductOverhang]] — 构建时模型尚未就绪的策略
- [[concepts/软件民主化]] — 印刷机类比，编程将像读写一样普及
- [[concepts/Loop机制]] — cron 式重复 Agent 任务
- [[domains/Claude-Code]] — 主题域
- [[sources/the-expanding-toolkit-2026-05-12]] — 同期 Lucas 演讲，工具箱扩展
- [[sources/fiona-fung-ai-native-engineering-2026-05-11]] — Fiona Fung，AI 原生工程组织
