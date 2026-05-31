---
address: c-000436
type: source
title: "Phoenix LLM Evaluators and Observability"
source_url: https://arize.com/docs/phoenix/evaluation/how-to-evals/llm-as-a-judge
source_type: documentation
author: "Arize Phoenix"
published: 2026
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - ai
  - evals
  - observability
  - llm-as-judge
status: active
related:
  - "[[concepts/JudgeDriftGraderObservability边界]]"
  - "[[concepts/AgentHarness与TraceEval]]"
---

# Phoenix LLM Evaluators and Observability

**来源**：Arize Phoenix documentation
**URL**：https://arize.com/docs/phoenix/evaluation/how-to-evals/llm-as-a-judge
**抓取时间**：2026-05-30

## 摘要

Phoenix 文档把 LLM-as-a-judge 放在 observability 和 evaluation 工作流中，支持对 traces、experiments、evaluators 和生产指标进行统一分析。

## 关键贡献

- LLM evaluator 可以用于 hallucination、QA correctness、relevance 等开放任务评分。
- Evaluation 与 tracing 结合，能把评分结果回连到输入、输出、上下文、retrieval 和系统运行轨迹。
- Observability 视角让 grader 的输出不只是离线分数，而是可监控的生产信号。
- 对本 vault 的意义：judge drift 可以通过 trace-level score trend、slice、latency、cost 和 feedback 对齐来监控。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：5. Agent 系统层、7. 产品与组织层

## 关联

- [[concepts/JudgeDriftGraderObservability边界]]
- [[Research: Judge drift grader observability 边界]]
