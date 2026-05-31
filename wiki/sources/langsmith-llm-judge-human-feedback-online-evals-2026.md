---
address: c-000435
type: source
title: "LangSmith LLM-as-Judge evaluators, human feedback, and online evals"
source_url: https://docs.langchain.com/langsmith/improve-judge-evaluator-feedback
source_type: documentation
author: "LangChain"
published: 2026
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - ai
  - evals
  - llm-as-judge
  - observability
status: active
related:
  - "[[concepts/JudgeDriftGraderObservability边界]]"
  - "[[concepts/EvalResultInterpretationDecisionThreshold边界]]"
---

# LangSmith LLM-as-Judge Evaluators, Human Feedback, and Online Evals

**来源**：LangSmith documentation
**URL**：https://docs.langchain.com/langsmith/improve-judge-evaluator-feedback
**抓取时间**：2026-05-30

## 摘要

LangSmith 文档展示了如何用 human feedback 改进 LLM-as-judge evaluator，并把 evaluator 接到在线评估、experiments 和 traces 中。

## 关键贡献

- 把 LLM judge 作为可迭代 evaluator，而不是一次性评分脚本。
- 人类反馈可以用来发现 judge 错误、调试 evaluator prompt，并更新 evaluation workflow。
- Online evals 和 tracing 让 judge 分数、样本、反馈和生产行为能被持续比较。
- 对本 vault 的意义：grader observability 应进入生产 telemetry 和 release workflow。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/JudgeDriftGraderObservability边界]]
- [[Research: Judge drift grader observability 边界]]
