---
address: c-000206
type: source
title: "Harness-Bench"
source_url: https://arxiv.org/abs/2605.27922
source_type: paper
author: "arXiv"
published: 2026-05-30
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - agents
  - benchmark
  - harness
status: active
related:
  - "[[concepts/AgentHarness与TraceEval]]"
  - "[[concepts/Agent评估体系]]"
---

# Harness-Bench

**来源**：arXiv
**URL**：https://arxiv.org/abs/2605.27922

## 摘要

Harness-Bench 研究 agent harness 对性能评估的影响。它关注同一模型在不同 harness 设置下的差异，提醒 benchmark 需要记录运行环境、工具和控制策略。

## 关键贡献

- Agent 性能不是模型能力的纯函数；harness 会改变可完成任务空间。
- Benchmark 若不控制 harness 条件，会混淆模型能力与运行时工程能力。
- 这支持本 vault 将 harness 放入第 5 层，而不是把它当作第 1-3 层模型能力。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：5. Agent 系统层
- 作用：提醒 eval 报告必须包含 harness 条件。

## 关联

- [[concepts/AgentHarness与TraceEval]]
- [[concepts/Agent评估体系]]
- [[Research: Agent harness 与 trace eval]]
