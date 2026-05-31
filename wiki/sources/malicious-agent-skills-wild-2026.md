---
address: c-000226
type: source
title: "Malicious Agent Skills in the Wild"
source_url: https://arxiv.org/abs/2602.06547
source_type: paper
author: "Yi Liu et al."
published: 2026-03-14
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - agent-skills
  - security
  - malicious-skills
status: active
related:
  - "[[concepts/Skill与ToolMemory边界]]"
---

# Malicious Agent Skills in the Wild

**来源**：arXiv:2602.06547
**URL**：https://arxiv.org/abs/2602.06547

## 摘要

这篇研究针对恶意 agent skills 建立标注数据集，行为验证 98,380 个 skills，确认 157 个恶意 skills 和 632 个漏洞。论文把恶意 skill 分为 Data Thieves 和 Agent Hijackers 两类。

## 关键贡献

- 第三方 skill 在用户机器上以用户权限运行，供应链风险不能按普通 Markdown 处理。
- Data Thieves 通过供应链技术外传凭据或数据。
- Agent Hijackers 通过 instruction manipulation 劫持 agent 决策。
- 高级恶意 skill 会利用平台 hook、permission flags 或未公开能力。
- 负责任披露后，大量确认恶意 skill 在 30 天内被移除。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：4. 上下文与知识层、5. Agent 系统层
- 作用：把 skill 安全从“最佳实践”升级为供应链治理问题。

## 关联

- [[concepts/Skill与ToolMemory边界]]
- [[Research: Skill 与 tool memory workflow 边界]]
