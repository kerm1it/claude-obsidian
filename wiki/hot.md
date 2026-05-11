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

- 地址计数器：58（c-000001 至 c-000057 已分配）
