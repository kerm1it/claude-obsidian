---
address: c-000224
type: source
title: "From Skill Text to Skill Structure"
source_url: https://arxiv.org/abs/2604.24026
source_type: paper
author: "Qiliang Liang, Hansi Wang, Zhong Liang, Yang Liu"
published: 2026-05-04
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - agent-skills
  - representation
  - security
status: active
related:
  - "[[concepts/Skill与ToolMemory边界]]"
---

# From Skill Text to Skill Structure

**来源**：arXiv:2604.24026
**URL**：https://arxiv.org/abs/2604.24026

## 摘要

论文指出当前 agent skills 多是 `SKILL.md` 风格文本，触发接口、执行结构、资源使用和副作用常被混在自然语言里。作者提出 Scheduling-Structural-Logical 表示，把 skill-level scheduling、scene-level execution structure 和 logic-level action/resource-use evidence 拆开。

## 关键贡献

- Skill-centered systems 需要同时管理调用接口、执行结构和副作用。
- 纯文本 skill 难以支持大规模发现、路由和风险评估。
- SSL 表示在 Skill Discovery 和 Risk Assessment 任务上优于 text-only baseline。
- 论文把 skill 从“文档”推进到“可审查的结构化程序性知识”。

## 对 AI 知识体系的归属

- 主归属：4. 上下文与知识层
- 交叉链接：6. 评估与可靠性层
- 作用：说明 skill 的长期演化方向是可检索、可审计、可结构化，而不只是 Markdown。

## 关联

- [[concepts/Skill与ToolMemory边界]]
- [[Research: Skill 与 tool memory workflow 边界]]
