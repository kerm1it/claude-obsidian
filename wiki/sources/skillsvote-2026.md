---
address: c-000257
type: source
title: "SkillsVote"
source_url: https://arxiv.org/abs/2605.18401
source_type: paper
author: "Hongyi Liu et al."
published: 2026-05-18
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - agent-skills
  - lifecycle
  - routing
status: active
related:
  - "[[concepts/SkillLibraryRouting生命周期]]"
  - "[[concepts/MemorySkillGovernanceDrift边界]]"
---

# SkillsVote

**来源**：arXiv:2605.18401
**URL**：https://arxiv.org/abs/2605.18401

## 摘要

SkillsVote 提出 Agent Skills 的 lifecycle-governance framework，从 collection、recommendation 到 evolution 管理 skill library。它把开放 skill 生态中的重复、质量不均、环境依赖和污染风险作为治理对象。

## 关键贡献

- Skill library 需要 collection、recommendation、evolution 三段治理。
- 执行前进行 agentic library search，暴露结构化 skill context。
- 执行后将 trajectory 分解为 skill-linked subtasks，并进行 outcome attribution。
- 只有 successful reusable discoveries 进入 evidence-gated updates。

## 对 AI 知识体系的归属

- 主归属：4. 上下文与知识层
- 交叉链接：5. Agent 系统层、6. 评估与可靠性层、8. 自我改进与前沿层
- 作用：提供 skill library 从静态集合到可治理生命周期的框架。

## 关联

- [[concepts/SkillLibraryRouting生命周期]]
- [[concepts/MemorySkillGovernanceDrift边界]]
- [[Research: Skill library routing lifecycle]]
