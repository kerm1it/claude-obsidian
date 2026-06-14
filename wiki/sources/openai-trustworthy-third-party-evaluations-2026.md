---
address: c-000419
type: source
title: "A shared playbook for trustworthy third party evaluations"
source_url: https://openai.com/index/trustworthy-third-party-evaluations-foundations/
source_type: engineering-blog
author: "OpenAI"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - ai
  - evals
  - frontier-evaluation
status: active
related:
  - "[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]"
  - "[[concepts/EvalResultInterpretationDecisionThreshold边界]]"
  - "[[concepts/EvalPortfolioMetricHierarchy边界]]"
  - "[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]"
  - "[[concepts/AgentHarness与TraceEval]]"
---

# A shared playbook for trustworthy third party evaluations

**来源**：OpenAI
**URL**：https://openai.com/index/trustworthy-third-party-evaluations-foundations/
**发布**：2026-05-29

## 摘要

OpenAI 总结 frontier model 第三方评估中的关键有效性风险：harness 选择、任务是否破损、elicitation budget、safeguard testing、sandbagging、contamination 和 reward hacking 都会改变 eval 结论能支持的 claim。

## 关键贡献

- 强调 eval 报告要说明 claim、tested system、harness、budget、elicitation method 和 validity checks。
- 将 broken problems、ambiguous prompts、missing files、flaky services、unfair scoring criteria 视为标准有效性风险。
- 对本 vault 的意义：decision threshold 不能只看分数，还要解释这次 eval 到底支持什么结论、不支持什么结论。
- 对 release card 的意义：每张卡都要固定 claim、tested system、harness、budget 和 validity checks，防止决策者把 eval 外推到未测试范围。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：5. Agent 系统层、7. 产品与组织层

## 关联

- [[concepts/EvalResultInterpretationDecisionThreshold边界]]
- [[concepts/EvalUncertaintyCommunicationReleaseCard边界]]
- [[concepts/EvalPortfolioMetricHierarchy边界]]
- [[Research: Eval result interpretation decision threshold 边界]]
