---
address: c-000466
type: synthesis
title: "Research: Post-release Eval Drift 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - evals
  - production-monitoring
status: active
related:
  - "[[concepts/PostReleaseEvalDrift边界]]"
  - "[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]"
  - "[[concepts/OfflineOnlineEvalCorrelation边界]]"
  - "[[concepts/SafetyCaseAssuranceCase边界]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
sources:
  - "[[sources/nist-deployed-ai-monitoring-challenges-2026]]"
  - "[[sources/aws-prescriptive-genai-production-monitoring-2026]]"
  - "[[sources/aws-prescriptive-genai-drift-detection-2026]]"
  - "[[sources/google-cloud-genai-monitoring-2024]]"
  - "[[sources/openai-evaluation-best-practices-2026]]"
  - "[[sources/langchain-production-monitoring-regression-tests-2026]]"
---

# Research: Post-release Eval Drift 边界

## Overview

本轮研究把 post-release eval drift 定义为“发布后 eval 证据失效监控”，主归属第 6 层评估与可靠性层。它不是普通 monitoring，也不是 release gate 本身，而是持续判断 release card、offline eval、online outcome 和 safety case 的证据是否因真实生产变化而变 stale。

## Key Findings

- NIST 2026 明确把 deployed AI monitoring 视为 post-deployment 必需实践，用来验证系统在真实场景中是否可靠、追踪不可预期输出，并提供部署后后果可见性。(Source: [[sources/nist-deployed-ai-monitoring-challenges-2026]])
- NIST 把监控拆成 functionality、operational、human factors、security、compliance、large-scale impacts 六类，并指出 performance degradation / drift、fragmented logging、人机反馈环研究不足是关键挑战。(Source: [[sources/nist-deployed-ai-monitoring-challenges-2026]])
- AWS 的 GenAI operational guidance 把生产监控拆成 application health、business metrics、model quality，并把 drift detection、feedback loop 和 structured improvement 放进生产维护流程。(Source: [[sources/aws-prescriptive-genai-production-monitoring-2026]])
- AWS 的 drift guidance 说明 LLM drift 通常来自数据分布或用户行为变化，工程上需要 reference/current distribution、embedding distance、threshold alert 和 LLM-as-judge semantic diagnosis。(Source: [[sources/aws-prescriptive-genai-drift-detection-2026]])
- Google Cloud 的 GenAI 部署指南强调要对应用端到端日志、组件 lineage、drift/skew、performance decay 和 continuous evaluation 建 alert，这支持把 post-release drift 连接到 release evidence refresh。(Source: [[sources/google-cloud-genai-monitoring-2024]])
- 既有 [[concepts/OfflineOnlineEvalCorrelation边界]] 已证明离线 eval 必须被线上 outcome 反校准；post-release eval drift 是更长期的“相关性和证据是否过期”监控层。

## Key Concepts

- [[concepts/PostReleaseEvalDrift边界]]：发布后证据保鲜边界，检查 release card / safety case / eval threshold 是否仍有效。
- Stale evidence：曾经足以支持发布的证据，在生产分布、artifact、judge、policy 或风险条件变化后不再足以支持当前决策。
- Drift action ladder：continue、investigate、refresh eval、quarantine metric、canary、rollback、incident、safety case refresh。

## Boundary Decision

- 主归属：6. 评估与可靠性层。
- 连接第 7 层：release / rollback gate、safety case、incident response 需要消费 drift 信号。
- 连接第 8 层：drifted traces 可以进入 data flywheel 和 self-improvement，但必须先经过质量、权利和 eval gate。
- 不新增顶层：它是 eval evidence 的生命周期状态，不是新的“运维层”或“监控层”。

## Engineering Checklist

1. Release card 写清楚上线后看什么信号、多久看、谁看、何时回滚。
2. 冻结 artifact identity 和 production baseline：model、prompt、RAG、tool、judge、provider、cohort、time window。
3. 监控 prompt/input、response/output、embedding、score、judge health、guardrail、business/user outcome、cost/latency。
4. 把 drift alert 连接到行动：owner、investigation、eval refresh、threshold update、rollback、incident 或 safety case refresh。
5. 把 drifted trace 回填到 annotation、regression eval、release card 和 offline/online correlation。

## Open Questions

- 高风险场景下，哪些 drift signal 应直接触发 pause / rollback，哪些只触发 evidence refresh？
- LLM agent 的 long-horizon workflow drift 是否需要独立于 prompt/response embedding 的状态轨迹 drift 指标？
- 对 provider silent update，应用侧需要多高频率的 canary rerun 才足以发现证据失效？

## Sources

- [[sources/nist-deployed-ai-monitoring-challenges-2026]]
- [[sources/aws-prescriptive-genai-production-monitoring-2026]]
- [[sources/aws-prescriptive-genai-drift-detection-2026]]
- [[sources/google-cloud-genai-monitoring-2024]]
- [[sources/openai-evaluation-best-practices-2026]]
- [[sources/langchain-production-monitoring-regression-tests-2026]]
