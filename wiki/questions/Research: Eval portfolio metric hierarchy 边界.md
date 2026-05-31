---
address: c-000472
type: synthesis
title: "Research: Eval Portfolio Metric Hierarchy 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - evals
  - metrics
status: active
related:
  - "[[concepts/EvalPortfolioMetricHierarchy边界]]"
  - "[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]"
  - "[[concepts/EvalResultInterpretationDecisionThreshold边界]]"
  - "[[concepts/PostReleaseEvalDrift边界]]"
sources:
  - "[[sources/openai-evaluation-best-practices-2026]]"
  - "[[sources/openai-evals-framework-2026]]"
  - "[[sources/openai-simple-evals-2026]]"
  - "[[sources/openai-evals-business-framework-2025]]"
  - "[[sources/helm-holistic-evaluation-2022]]"
  - "[[sources/google-ml-test-score-2016]]"
---

# Research: Eval Portfolio Metric Hierarchy 边界

## Overview

本轮研究把 eval portfolio / metric hierarchy 定义为第 6 层的“证据组合架构”：不是新增一个 benchmark，而是把不同 eval 资产和指标按决策用途组织起来，明确 hard stop、guardrail、primary、slice、regression、online、diagnostic 和 exploratory 指标的优先级。

## Key Findings

- OpenAI evaluation best practices 将 eval 设计拆成 objective、dataset、metrics、run/compare、continuous evaluation，并强调要用 production data、historical data 和 human feedback 扩充 eval set。(Source: [[sources/openai-evaluation-best-practices-2026]])
- OpenAI simple-evals 把 MMLU、MATH、GPQA、DROP、MGSM、HumanEval、SimpleQA、BrowseComp、HealthBench 等放在一个轻量评估集合中，说明通用 benchmark 可以成为 portfolio 的能力探针，但不是产品 release gate 的全部。(Source: [[sources/openai-simple-evals-2026]])
- HELM 的核心贡献是多场景、多指标评估，覆盖 accuracy、calibration、robustness、fairness、bias、toxicity、efficiency，直接支持“不要用单一总分评价模型”。(Source: [[sources/helm-holistic-evaluation-2022]])
- Google ML Test Score 从生产系统角度强调 data tests、model tests、infrastructure tests 和 monitoring tests，说明 eval portfolio 必须包含工程和监控证据，而不只是模型 accuracy。(Source: [[sources/google-ml-test-score-2016]])
- OpenAI 的业务 eval 框架把 eval 类比为把模糊目标变成明确规格和测量路径，这支持将 eval portfolio 绑定具体产品决策而不是抽象能力排名。(Source: [[sources/openai-evals-business-framework-2025]])

## Boundary Decision

- 主归属：6. 评估与可靠性层。
- 连接第 7 层：release gate、rollback、safety case、risk owner 和产品 ROI 都消费组合后的证据。
- 连接第 8 层：portfolio 的失败和漂移决定哪些 trace 进入 self-improvement，但不能绕过 guardrail 和 hold-out。
- 不新增顶层：portfolio 是第 6 层 eval evidence 的组织方式，不是“指标层”。

## Recommended Hierarchy

1. Hard stop：法律禁止、不可容忍风险、critical safeguard failure。
2. Guardrail：安全、隐私、公平、拒答、tool permission、成本、延迟底线。
3. Product contract / regression：产品承诺和已知失败不得回归。
4. Primary task metric：核心任务质量是否超过 baseline。
5. Slice metric：关键用户、语言、任务、工具路径、风险类是否稳定。
6. Online / business metric：线上 outcome 是否和离线预测同向。
7. Diagnostic / exploratory：定位原因或发现新风险，不直接放行。

## Open Questions

- 对不同 risk tier，hard stop / guardrail / primary metric 的最小组合应如何裁剪？
- 当 public benchmark、private hold-out 和 online metric 结论冲突时，是否需要标准化 escalation rule？
- Portfolio 中哪些指标应该按 release 运行，哪些可以按周或按 post-release drift trigger 运行？

## Sources

- [[sources/openai-evaluation-best-practices-2026]]
- [[sources/openai-evals-framework-2026]]
- [[sources/openai-simple-evals-2026]]
- [[sources/openai-evals-business-framework-2025]]
- [[sources/helm-holistic-evaluation-2022]]
- [[sources/google-ml-test-score-2016]]
