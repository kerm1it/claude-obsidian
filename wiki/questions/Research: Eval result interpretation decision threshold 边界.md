---
address: c-000418
type: synthesis
title: "Research: Eval result interpretation decision threshold 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - evals
  - decision-threshold
status: active
related:
  - "[[concepts/EvalResultInterpretationDecisionThreshold边界]]"
  - "[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]"
  - "[[concepts/LLMJudgeAIFeedbackCalibration边界]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
sources:
  - "[[sources/openai-evaluation-best-practices-2026]]"
  - "[[sources/anthropic-demystifying-evals-agents-2026-05-26]]"
  - "[[sources/openai-trustworthy-third-party-evaluations-2026]]"
  - "[[sources/google-sre-service-level-objectives-2016]]"
  - "[[sources/google-sre-error-budget-policy-2018]]"
  - "[[sources/kohavi-controlled-experiments-web-2009]]"
  - "[[sources/chatbot-arena-human-preference-2024]]"
  - "[[sources/anytime-valid-confidence-sequences-ab-testing-2023]]"
  - "[[sources/betterbench-benchmark-quality-2024]]"
---

# Research: Eval result interpretation decision threshold 边界

## Overview

本轮研究把 eval result interpretation / decision threshold 归入第 6 层评估与可靠性层。它不生产 eval set，也不执行发布；它负责解释 eval 结果是否足以支持 release、rollback、routing、training 或 self-improvement 决策。

核心结论：**分数只是测量值，阈值和不确定性解释才是工程决策。**

## Key Findings

- OpenAI eval best practices 把 eval 流程拆成 objective、dataset、metrics、run/compare 和 continuous evaluation，说明 eval 必须服务具体生产决策，而不是只产出排行榜分数。（Source: [[sources/openai-evaluation-best-practices-2026]]）
- Anthropic agent eval 经验显示，低分可能来自任务不可解、grader bug、harness 约束或模糊 spec；解释结果前必须验证任务、grader 和 trace。（Source: [[sources/anthropic-demystifying-evals-agents-2026-05-26]]）
- OpenAI third-party eval playbook 强调评估报告需要说明 claim、tested system、harness、budget、elicitation 和 validity checks，否则决策者会高估或低估结论可支持的范围。（Source: [[sources/openai-trustworthy-third-party-evaluations-2026]]）
- Google SRE 的 SLO / error budget 模型提供了稳定类比：阈值不是追求满分，而是把可靠性目标转成发布速度和暂停发布的控制规则。（Source: [[sources/google-sre-service-level-objectives-2016]]、[[sources/google-sre-error-budget-policy-2018]]）
- Kohavi 等 controlled experiments 体系说明，线上 A/B 决策需要因果设计、样本、指标和统计显著性；AI 产品的上线阈值也要预先定义最小有意义效果和停止规则。（Source: [[sources/kohavi-controlled-experiments-web-2009]]）
- Chatbot Arena 使用 pairwise human preference、Bradley-Terry 模型和 confidence intervals，说明 LLM 排名需要表达不确定性；区间重叠时不能把排名差直接当成确定结论。（Source: [[sources/chatbot-arena-human-preference-2024]]）
- Anytime-valid confidence sequences 解决连续观察实验时的 peeking 假阳性风险；这对持续 eval、canary 和线上实验很关键。（Source: [[sources/anytime-valid-confidence-sequences-ab-testing-2023]]）
- BetterBench 把统计显著性、方差报告和可复现性列入 benchmark 质量标准，支持把 variance / uncertainty 当成 eval 解释的必要部分。（Source: [[sources/betterbench-benchmark-quality-2024]]）

## Stable Classification

- 主归属：6. 评估与可靠性层
- 上游：eval dataset lifecycle、grader calibration、human feedback、production logs、risk governance、SLO
- 下游：model release gate、rollback、canary、routing policy、training admission、self-improvement gate
- 交叉链接：7. 产品与组织层，因为阈值最终进入 owner、exception、release 和 rollback；2. 模型构建层，因为阈值决定训练候选是否可用；5. Agent 系统层，因为 agent eval 需要 trace/state/cost 阈值。

## Decision Framework

```text
1. 写清楚这次 eval 控制的决策
2. 绑定 baseline 和最小有意义差异
3. 区分 primary metric、guardrail、diagnostic
4. 设计样本、重复运行、slice 和线上/离线 split
5. 报告 uncertainty：CI、bootstrap、confidence sequence、flakiness、judge disagreement
6. 用 decision band 决定 pass/fail/gray-zone/human-escalation/canary/rollback
7. 记录 owner、例外路径、生产相关性和阈值更新条件
```

## Engineering Practice

- 默认不要用单一平均分发布模型；至少要有 baseline delta、guardrail、关键 slice 和 uncertainty。
- 对 agent eval，解释分数前先检查任务是否可解、grader 是否合理、harness 是否限制了合法策略、trace 是否暴露真实失败。
- 对高风险能力，使用硬 guardrail：安全、隐私、权限和外部副作用指标破线时，总分提升不能抵消风险。
- 对低样本和高成本 eval，设计灰区；灰区进入人工复核、专家评审、canary 或更多样本，而不是自动发布。
- 对线上实验，预先写样本量、最小可检测效果、停止规则和多重比较处理。
- 发布后把阈值和生产指标对齐：如果离线 eval 不能预测投诉、人工接管、事故、成本或满意度，阈值需要重设。

## Open Questions

- 不同 agent trace eval 中，怎样给过程质量、最终状态、成本和安全风险设统一 decision band，仍需要更多行业实践。
- LLM judge 的分数置信区间、judge disagreement 和 human escalation threshold 还没有统一工程标准。
- 高风险模型能力评估中的 intolerable risk threshold 仍依赖组织风险偏好和监管场景，不能用通用分数替代。

## Sources

- [[sources/openai-evaluation-best-practices-2026]]：生产 eval 流程和 continuous evaluation。
- [[sources/anthropic-demystifying-evals-agents-2026-05-26]]：agent eval task / grader / trace 解释风险。
- [[sources/openai-trustworthy-third-party-evaluations-2026]]：第三方 frontier eval 的 claim、harness、budget 和 validity checks。
- [[sources/google-sre-service-level-objectives-2016]]：SLO / SLI / error budget 决策类比。
- [[sources/google-sre-error-budget-policy-2018]]：当 error budget 被耗尽时暂停发布的阈值政策。
- [[sources/kohavi-controlled-experiments-web-2009]]：A/B testing 的因果实验基础。
- [[sources/chatbot-arena-human-preference-2024]]：LLM ranking 的 confidence interval 和 pairwise preference 方法。
- [[sources/anytime-valid-confidence-sequences-ab-testing-2023]]：连续监控实验的 anytime-valid uncertainty。
- [[sources/betterbench-benchmark-quality-2024]]：benchmark 质量中的统计显著性和方差报告要求。
