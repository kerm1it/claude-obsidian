---
type: meta
title: "热缓存"
created: 2026-05-05
updated: 2026-05-11
tags:
  - meta
  - hot-cache
status: active
related:
  - "[[index]]"
  - "[[log]]"
  - "[[overview]]"
---

# 最近上下文

## 最近更新

2026-05-14。消化了一条素材：

**agentmemory**（rohitg00/agentmemory，GitHub，⭐ 7,121）：自称 "#1 Persistent memory for AI coding agents"，基于 iii engine，与 LLM Wiki pattern 同源。

- **[[entities/AgentMemory]]**：`npx @agentmemory/agentmemory`；TypeScript；Apache 2.0；0 外部 DB
- **性能**：R@5 95.2%（LongMemEval-S），92% token 节省，51 MCP tools，12 hooks，827 tests
- **[[concepts/四层记忆整合]]**：Working → Episodic → Semantic → Procedural，Ebbinghaus 衰减 + 矛盾检测 + 自动驱逐
- **三流检索**：BM25 + Vector + Graph，RRF 融合——与 [[concepts/混合检索RRF]]（GBrain）独立收敛
- **与 claude-mem 对比**：agentmemory 更工程化（4 层架构、知识图谱、团队记忆），claude-mem 更轻量（75K ⭐，1 条命令）
- **三方独立收敛**：agentmemory 4 层整合 ≈ GBrain Dream Cycle ≈ Anthropic Dreaming——异步离线记忆巩固是 Agent 系统通用原语
- **与 Karpathy 关系**：作者的设计文档（Gist，⭐ 1200）显式扩展了 Karpathy LLM Wiki pattern，agentmemory 是实现
- **更新**：GBrain、ClaudeMem wiki 页面已补充与 agentmemory 的对比

---

2026-05-13。消化了一条素材：

**claude-mem**（thedotmack/claude-mem，GitHub，⭐ 75,423）：目前最流行的 Claude Code 跨会话记忆插件。

- **[[entities/ClaudeMem]]**：一条命令安装（`npx claude-mem install`）；TypeScript；Apache 2.0
- **架构**：5 种生命周期钩子 + SQLite（observations）+ Chroma（向量）+ Worker（port 37777）
- **[[concepts/渐进式上下文注入]]**：3 层 MCP 工作流（search → timeline → get_observations），节省约 10x tokens
- **与 GBrain 对比**：claude-mem 更轻量（实时捕获会话），GBrain 更完整（Compiled Truth + Dream Cycle）
- **与 AgentMemoryAPI 对比**：本地插件 vs 云端 API，互补
- **OpenClaw 集成**：一条 curl 命令接入 OpenClaw Gateway
- **Endless Mode（Beta）**：仿生记忆架构，超长会话专用
- **更新**：GBrain 和 AgentMemoryAPI wiki 页面已补充与 claude-mem 的对比

---

2026-05-12。消化了三条素材：

**Andrew Wilkinson — AI Agents Run My Business and Life**（Greg Isenberg，YouTube，录制于 2026-04-29）：Tiny 创始人分享 AI Agent 完整运营业务实践。

- **[[concepts/自主商业运营]]**：Deep Personality（SaaS）完全由 Agent 运营（Support/Dev/Marketing），营收 $2 万；Harbor 是工具
- **Family Office 替换 Addepar**：CFO 零代码背景，两周替换 $5-10 万/年 SaaS；月 Claude 账单 $4 万
- **个人 AI 栈**：OpenClaw Agent（邮件→Telegram 多选题）+ GBrain（会议/邮件/生活录音）+ Hearsay（全天录音）+ 个性化播客（Gemini Voice）+ 健康 Agent（Apple Watch + 8 专家子 Agent）
- **[[concepts/软件护城河侵蚀]]**："软件现在是个更差的生意"；殡仪馆类比；投 TSMC/数据中心
- **与 Boris Cherny 收敛**：两人独立得出"纯功能性 SaaS 护城河瓦解"
- **提示技巧**：让 Claude 采访你来构建 prompt；总是用 8 个子 Agent 团队
- **新人物**：[[people/AndrewWilkinson]]；新实体：[[entities/Tiny]]
- **GBrain/OpenClaw 更新**：Andrew 是 Garry Tan 朋友，实际生产用户，补充了两个 wiki 页面

---

**Boris Cherny — Why Coding Is Solved, and What Comes Next**（Sequoia Capital，YouTube）：Claude Code 创始人的访谈。

- **[[concepts/ProductOverhang]]**：Claude Code 诞生逻辑——模型能力已存在，产品尚未捕捉；提前建造等待模型赶上；头六个月不好用是预期中的
- **指数增长始于 Opus 4**（2026 年 5 月），此后每个模型版本都有新拐点
- **个人工作流**：从手机工作；5-10 session，几百 Agent 并行，每晚几千 Agent 深度工作
- **[[concepts/Loop机制]]**：`/loop` = cron 调度重复任务（PR 保姆、CI 健康、Twitter 反馈聚类）；Routines 是服务端版本；Boris 称"Loop 是最重要功能"；4.7 会主动提议启动 Loop
- **SaaS 护城河**：削弱——切换成本、流程力量；保留——网络效应、规模经济、稀缺资源；创业最佳时机
- **[[concepts/软件民主化]]**：印刷机类比；领域专家 > 通用工程师；所有人都会编程但专业工程师仍存在
- **Anthropic 内部**：零手写代码，SQL 也由模型生成；Claude 实例通过 Slack 互相通信；领先之处是组织流程，不是模型
- **新人物**：[[people/BorisCherny]]；新实体：[[entities/SequoiaCapital]]

---

**Lucas — The Expanding Toolkit**（Anthropic，YouTube，Code with Claude 2026-05-06）：模型能力扩展工具箱框架。

- **核心论点**：去年要自己搭的脚手架今天已随模型出货 → [[concepts/ExpandingToolkit]]
- **Tool Use**：模型自主选工具 + 自动重试；路由器/预过滤通常反而更差。Tip：在工具 description 里声明**输出 schema** → 省一次 harness 往返
- **Context Management**：1M context + server-side compaction + context editing；Tip：每 N 轮清除 stale tool results
- **Code Execution**：服务端托管沙箱，整个 write-run-fix 在**单个 API turn** 完成 → [[concepts/CodeExecution]]；Claude Code `/schedule` 可定时触发自主循环
- **Computer Use**：Opus 4.7 原生 1440p 坐标，缩放数学消失 → [[concepts/NativeResolutionComputerUse]]；OSWorld 78%；Claude in Chrome（`claude.ai/chrome`）可操控真实浏览器
- **指导原则**：补偿模型不可靠性的代码 → 交给 Anthropic（半衰期几个月）；连接模型与你的世界的代码 → 专注投入（持续增值）
- **新人物**：[[people/Lucas]]

---

2026-05-11。消化了五条素材：

1. **Matt Bleifer — The Thinking Lever**（Anthropic，YouTube）：Test-time compute 设计哲学。三类 token（thinking/tool/text）；Adaptive Thinking 自 Opus 4.6 为默认；Effort 优于思考开关；extra high 是 coding 最佳默认；低 effort ≠ 低智能（Pokémon 速通实验）；Task Budgets 新功能。

2. **Ryan Lopopolo — 工程技术：在智能体优先的世界中利用 Codex**（OpenAI，2026-02-11）：3 名工程师，5 个月，100 万行代码，零人工编码，效率 10×。AGENTS.md 是目录；仓库即记录系统；黄金原则 + 后台 GC 对抗代码熵；智能体 GC ≈ GBrain DreamCycle ≈ Anthropic Dreaming，三者独立收敛。

2. **GBrain**（garrytan/gbrain，14.6K ⭐）：Garry Tan（YC 总裁）开源的 AI Agent 记忆管理系统，核心创新是 Compiled Truth+Timeline 双区结构 + 混合检索 RRF（P@5 +31.4 pts vs baseline）+ Skillify（fat-markdown skill）+ Dream Cycle（夜间自动维护）。与本 vault 的 skills/ 高度同构。

2. **Fiona Fung — Running an AI-native engineering org**（Code with Claude 2026-05-06，YouTube ~30 分钟）：Claude Code 工程负责人 Fiona Fung 分享 AI 原生工程组织的五大主题。

3. **Mahesh — Memory and Dreaming for Self-Learning Agents**（Anthropic 官方，2026-05-11）：Anthropic 平台 PM 发布 Memory API（公测）和 Dreaming（研究预览），Agent 记忆体系进入正式产品化阶段。

---

2026-05-10。消化了三条素材：

1. **@trq212 X Article**：Claude Code 团队 Thariq 主张用 HTML 替代 Markdown 作为 AI 输出格式
2. **AI Agent 实践分享会**（2026-05-05 录像，NotebookLM 转录）：5 位嘉宾分享内部 AI Agent 工作流
3. **Dario & Daniela Amodei 对谈**（Code with Claude 开发者大会，2026-05-06，YouTube 33分10秒）

## 关键事实

### 来自 Mahesh — Anthropic Memory + Dreaming（最新，2026-05-11 摄入）

- **[[concepts/AgentMemoryAPI]]**：文件系统式记忆（Claude 自主用 Bash/Grep 管理），Claude Opus 4.7 SOTA
- **[[concepts/AnthropicDreaming]]**：离线批处理，跨多 Agent transcript，提取共同错误/成功策略，生成 memory diff；Harvey 任务完成率 ↑ 6×；Rockutin 首次犯错率 ↓ 90%
- **关键收敛**：[[concepts/DreamCycle]]（GBrain）与 Dreaming（Anthropic）独立实现同一模式 → 异步记忆维护是 Agent 系统的通用过程层原语
- **[[concepts/乐观并发]]**：content hash 校验，多 Agent 并发写保护
- **[[people/Mahesh]]**：新增人物页

### 来自 Fiona Fung（2026-05-11 摄入）

- **瓶颈已转移**：编码吞吐量不再稀缺 → 验证/安全/跨职能协作成为新瓶颈 → [[concepts/瓶颈转移论]]
- **JIT 规划**：六个月路线图三个月就过时；改为即时规划，idea → prototype → PR → [[concepts/JIT规划]]
- **技术争论新范式**：生成三个 PR 对比，代码赢，不去白板
- **Claude Code 审查策略**：Claude 负责 style/lint/bug；人类保留法务/安全/产品品位
- **管理者先做 IC**：重狗粮，建立团队信任；org 尽量扁平
- **三大核心原则**：全员用 Claude Code；Claudify 一切；明确许可干掉旧流程
- **效果信号**：onboarding 上手时间 ↓；PR 周期 ↓；Claude 辅助提交率趋近 100%
- **[[people/FionaFung]]**：新增人物页

### 来自 Dario & Daniela 对谈

- **Q1 2026 年化增长 80x**（预期 10x）→ SpaceX 算力合作公告
- **Dario**：预测 **2026 年出现单人十亿美金公司**，目前已有 2 人团队 10 亿、单人数亿
- **多 Agent 愿景**："数据中心里的天才国家"——从个人工具 → 团队 → 组织级 AI
- **Amdahl 定律**：代码写快了，但安全/验证/架构成为新瓶颈
- **Daniela**：开发者是最重要用户；**Hold Light and Shade** 是 Anthropic 核心价值观
- Claude Code 2022 年试验失败（模型太弱），2024 年成功 → 能力台阶突然点亮
- Claude 被用于加速 Claude 自身训练，内部 PR 数量明显提升

### 来自 AI Agent 实践分享会

- **[[people/Zara]]**：Claude Code 接入飞书 → 替代 terminal
- **[[people/Sparks]]**（[[entities/Midas]]）：双层 Agent 量化交易
- **[[people/Brandon]]**（[[entities/Instant]]）：70% 决策与 AI 一致；"宁可浪费 Token，不浪费时间"
- **[[people/Siqi]]**（[[entities/Pika]]）：AI 数字分身"47"，有手机号、加入会议
- **[[people/Haoran]]**（[[entities/MX]]）：AI 原生团队工作空间，50 个 agent

### 来自 @trq212

- HTML > Markdown：信息密度、交互性、分享便利；代价是生成慢 2-4 倍

## 当前线索

- [[concepts/智能体优先工程]] — OpenAI 实战验证框架，与 Fiona Fung 框架高度同构，可合并为统一视角
- [[concepts/代码仓库即记录系统]] — 直接适用于本 vault 和自己的项目：仓库/vault 即记忆
- [[concepts/智能体GC]] — 三方独立收敛（OpenAI / GBrain / Anthropic），异步离线维护是 Agent 系统通用原语
- [[concepts/AnthropicDreaming]] — Anthropic 官方 Dreaming，研究预览，值得深入跟踪应用效果
- [[concepts/AgentMemoryAPI]] — 尝试在自己的 Agent 项目中接入 Memory API
- [[concepts/AI原生工程组织]] — Fiona 的整体框架，自己团队可对照检视哪些规范值得借鉴
- [[concepts/瓶颈转移论]] — 与 [[concepts/AmdahlsLawInAI]] 互相印证，值得深入思考
- [[concepts/JIT规划]] — 在自己的项目中实践即时规划
- [[entities/GBrain]] — 开源 Agent 记忆系统，架构可深入研究（Compiled Truth、Minions、Dream Cycle）
- [[concepts/Skillify]] — fat-markdown skill 模式与本 vault skills/ 同构，可互相借鉴
- [[concepts/混合检索RRF]] — RRF 融合检索，可应用于本 vault 的 wiki-query 改进
- [[concepts/单人十亿美金公司]] — 2026 年底截止，值得持续关注
- [[concepts/国家级天才数据中心]] — 多 Agent 架构演进方向
- [[concepts/Claude-Code接入飞书]] — 可以深入研究实现方案
- [[entities/MX]] — 产品值得关注

## DragonScale

- 地址计数器：80（c-000001 至 c-000080 已分配）
