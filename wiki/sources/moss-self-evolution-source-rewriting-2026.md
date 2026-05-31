---
address: c-000570
type: source
title: "MOSS: Self-Evolution through Source-Level Rewriting"
source_url: https://arxiv.org/abs/2605.22794
source_type: paper
author: "Qianshu Cai, Yonggang Zhang, Xianzhang Jia, Huajiang Zheng, Wei Xue, Jun Song, Xinmei Tian, Yike Guo"
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - agents
  - self-evolution
  - source-rewriting
status: active
related:
  - "[[concepts/SelfImprovementGateChangeRiskBudget边界]]"
  - "[[concepts/Dream与SelfImprovement工程原语]]"
  - "[[concepts/AgentHarness与TraceEval]]"
---

# MOSS: Self-Evolution through Source-Level Rewriting

**来源**：arXiv:2605.22794
**URL**：https://arxiv.org/abs/2605.22794

## 摘要

MOSS 研究 source-level adaptation：不是只改 prompt、skill file、memory schema 或 workflow graph，而是让 agentic substrate 的源代码也能被候选改动触达。论文强调候选改动由生产失败证据驱动，经过多阶段 pipeline，由外部 coding agent 生成改动，但 MOSS 保留阶段顺序和 verdict。

## 关键机制

- 从 production-failure evidence 自动整理候选批次。
- 在 ephemeral trial workers 中 replay batch 验证候选 image。
- 通过 user-consent-gated promotion 进入 in-place container swap。
- 用 health-probe-gated rollback 做上线后回退。

## 对本体系的贡献

- 证明第 8 层 self-improvement 的改动目标可以从 text artifacts 扩展到 harness/source code。
- 同时证明 source-level self-evolution 必须更强 gate：trial worker、replay、user consent、health probe 和 rollback。
- 支撑本轮将 harness/source rewrite 列为中高风险改动，而不是普通 memory update。

## 对 AI 知识体系的归属

- 主归属：8. 自我改进与前沿层
- 交叉链接：5. Agent 系统层、6. 评估与可靠性层、7. 产品与组织层

## 关联

- [[concepts/SelfImprovementGateChangeRiskBudget边界]]
- [[concepts/Dream与SelfImprovement工程原语]]
- [[Research: Self-improvement gate change-risk budget 边界]]
