---
address: c-000210
type: synthesis
title: "Research: Dream 与 self-improvement 工程原语"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - self-improvement
  - dreaming
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/Dream与SelfImprovement工程原语]]"
  - "[[concepts/DreamCycle]]"
  - "[[concepts/AnthropicDreaming]]"
  - "[[concepts/自我改进AI循环]]"
  - "[[concepts/自主ML研究循环]]"
sources:
  - "[[sources/anthropic-dreams-docs-2026]]"
  - "[[sources/claude-managed-agents-memory-2026]]"
  - "[[sources/claude-managed-agents-dreaming-outcomes-2026]]"
  - "[[sources/reflexion-2023]]"
  - "[[sources/seal-self-adapting-language-models-2025]]"
  - "[[sources/sia-self-improving-ai-2026]]"
  - "[[sources/memory-dreaming-self-learning-agents-2026-05-11]]"
  - "[[sources/autoresearch-2026-05-20]]"
  - "[[sources/yc-root-access-self-improving-company-2026-05-22]]"
---

# Research: Dream 与 self-improvement 工程原语

## Overview

Dream / self-improvement 可以稳定归入 [[domains/AI知识体系]] 第 8 层，但它真正发挥作用时会反哺第 4 层 memory/context、第 5 层 harness/tool、第 6 层 eval，少数前沿系统才反哺第 2 层 weights。

本轮结论：自我改进不是单点技术，而是 `trace → eval → consolidation/reflection → diff → gate → apply` 的闭环。

## Key Findings

- Anthropic Dreams 是异步 job：读取已有 memory store 和 1-100 个历史 session，产出一个新的 output memory store；输入 store 不被修改，便于审查和丢弃。（Source: [[sources/anthropic-dreams-docs-2026]]）
- Claude Managed Agents memory 把记忆挂载为文件系统，agent 可跨 session 学习；官方案例强调 memory 要可观察、可控制。（Source: [[sources/claude-managed-agents-memory-2026]]）
- Managed Agents 的 dreaming、outcomes 和 multiagent orchestration 说明生产级 self-improvement 需要 memory、eval outcome 和 orchestration 同时存在。（Source: [[sources/claude-managed-agents-dreaming-outcomes-2026]]）
- Reflexion 是早期稳定原语：不改权重，而是把反馈写成语言反思，存入 episodic memory，用于下一次尝试。（Source: [[sources/reflexion-2023]]）
- SEAL 和 SIA 把自我改进推进到权重更新层，但仍需要外部训练、评价和奖励信号；这属于前沿研究，不等同于今天的生产 dream。（Source: [[sources/seal-self-adapting-language-models-2025]], [[sources/sia-self-improving-ai-2026]]）
- Karpathy autoresearch 是可审查的自主实验闭环：program.md 设目标，agent 改代码，固定时间窗训练，用 val_bpb 评估再迭代。（Source: [[sources/autoresearch-2026-05-20]]）

## Stable Model

| 阶段 | 输入 | 输出 | 回填位置 |
|---|---|---|---|
| Capture | trace、session、工具调用、失败案例 | 可审计日志 | 第 5 层 |
| Evaluate | outcome、tests、grader、人工审查 | 分数和失败归因 | 第 6 层 |
| Consolidate | memory store、transcripts | 去重/纠错/新洞察 | 第 4 层 |
| Propose diff | 失败归因、模式 | memory/tool/prompt/harness/eval/weight 改动 | 第 4/5/6/2 层 |
| Gate | tests、eval、hold-out、review | 是否应用 | 第 6 层 |
| Apply | 被批准的 diff | 新系统状态 | 反哺前层 |

## Boundary

- Dream 的主线是 **异步记忆巩固**，不是实时推理。
- Self-improvement 的最小可用形式是 **外部系统改进**，不是模型权重自改。
- 自我进化只有在 `可观测运行 → 可验证改动 → 可回滚应用` 同时存在时才有工程意义。

## Open Questions

- Dream 输出应多大比例自动应用，哪些必须人工审核。
- Weight-level self-improvement 如何避免训练数据污染和 eval overfitting。
- 多 agent 系统中，memory consolidation 的权限边界应按用户、团队、组织还是任务划分。

## Filed Result

本轮归档为 [[concepts/Dream与SelfImprovement工程原语]]，并回填 [[domains/AI知识体系]] 第 8 层；四个初始验收主题已经串成稳定链路：选择框架 → RAG/Memory → Harness/Trace → Dream/Self-improvement。
