---
address: c-000569
type: source
title: "Automated Self-Testing as a Quality Gate"
source_url: https://arxiv.org/abs/2603.15676
source_type: paper
author: "Alexandre Cristovao Maiorano"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - evals
  - release-gate
  - llm-applications
status: active
related:
  - "[[concepts/SelfImprovementGateChangeRiskBudget边界]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/EvalResultInterpretationDecisionThreshold边界]]"
---

# Automated Self-Testing as a Quality Gate

**来源**：arXiv:2603.15676
**URL**：https://arxiv.org/abs/2603.15676
**标题**：Automated Self-Testing as a Quality Gate: Evidence-Driven Release Management for LLM Applications

## 摘要

这篇论文提出 LLM 应用的 automated self-testing framework，把非确定性 LLM 应用发布变成 evidence-based release management。它的核心决策是 PROMOTE / HOLD / ROLLBACK，并围绕 task success rate、research context preservation、P95 latency、safety pass rate 和 evidence coverage 五类维度做质量门。

## 对本体系的贡献

- 给 self-improvement gate 一个直接工程先例：候选改动不是“感觉变好”，而是进入明确的 promote/hold/rollback gate。
- 说明 LLM 应用 gate 不能只看准确率，还要看上下文保持、延迟、安全和证据覆盖。
- 适合支撑第 6 层 eval result interpretation 与第 7 层 release/rollback gate。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层、8. 自我改进与前沿层

## 关联

- [[concepts/SelfImprovementGateChangeRiskBudget边界]]
- [[concepts/ModelReleaseRollbackGate边界]]
- [[Research: Self-improvement gate change-risk budget 边界]]
