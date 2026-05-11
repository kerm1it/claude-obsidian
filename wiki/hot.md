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

2026-05-11。消化了一条素材：

1. **GBrain**（garrytan/gbrain，14.6K ⭐）：Garry Tan（YC 总裁）开源的 AI Agent 记忆管理系统，核心创新是 Compiled Truth+Timeline 双区结构 + 混合检索 RRF（P@5 +31.4 pts vs baseline）+ Skillify（fat-markdown skill）+ Dream Cycle（夜间自动维护）。与本 vault 的 skills/ 高度同构。

---

2026-05-10。消化了三条素材：

1. **@trq212 X Article**：Claude Code 团队 Thariq 主张用 HTML 替代 Markdown 作为 AI 输出格式
2. **AI Agent 实践分享会**（2026-05-05 录像，NotebookLM 转录）：5 位嘉宾分享内部 AI Agent 工作流
3. **Dario & Daniela Amodei 对谈**（Code with Claude 开发者大会，2026-05-06，YouTube 33分10秒）

## 关键事实

### 来自 Dario & Daniela 对谈（最新）

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

- [[entities/GBrain]] — 开源 Agent 记忆系统，架构可深入研究（Compiled Truth、Minions、Dream Cycle）
- [[concepts/Skillify]] — fat-markdown skill 模式与本 vault skills/ 同构，可互相借鉴
- [[concepts/混合检索RRF]] — RRF 融合检索，可应用于本 vault 的 wiki-query 改进
- [[concepts/单人十亿美金公司]] — 2026 年底截止，值得持续关注
- [[concepts/国家级天才数据中心]] — 多 Agent 架构演进方向
- [[concepts/AmdahlsLawInAI]] — 在自己的 AI 工作流中找新瓶颈
- [[concepts/Claude-Code接入飞书]] — 可以深入研究实现方案
- [[entities/MX]] — 产品值得关注

## DragonScale

- 地址计数器：38（c-000001 至 c-000037 已分配）
