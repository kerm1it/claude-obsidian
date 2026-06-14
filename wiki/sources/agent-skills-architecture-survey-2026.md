---
address: c-000222
type: source
title: "Agent Skills for Large Language Models"
source_url: https://arxiv.org/abs/2602.12430
source_type: paper
author: "Renjun Xu, Yang Yan"
published: 2026-02-17
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - agent-skills
  - survey
  - security
status: active
related:
  - "[[concepts/Skill与ToolMemory边界]]"
  - "[[concepts/AgentSkillsStandard]]"
---

# Agent Skills for Large Language Models

**来源**：arXiv:2602.12430
**URL**：https://arxiv.org/abs/2602.12430

## 摘要

这篇 survey 把 agent skills 定义为 agent 按需加载的 instructions、code 和 resources 组合，用于在不重新训练模型的情况下扩展能力。论文把领域组织为 architecture、acquisition、deployment、security 四个方向。

## 关键贡献

- Skill 是单体模型走向模块化 agent 的抽象层。
- Progressive disclosure、portable skill definitions 和 MCP 互补是架构基础。
- Skill acquisition 包括人工策划、强化学习 skill library、自主发现和组合式合成。
- Security 是一等问题，论文强调 skill provenance、permission model 和 lifecycle governance。

## 对 AI 知识体系的归属

- 主归属：4. 上下文与知识层
- 交叉链接：5. Agent 系统层、6. 评估与可靠性层、8. 自我改进与前沿层
- 作用：提供 skill 作为 AI agent 抽象层的全景框架。

## 关联

- [[concepts/Skill与ToolMemory边界]]
- [[Research: Skill 与 tool memory workflow 边界]]
