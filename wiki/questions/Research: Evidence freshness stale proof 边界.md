---
address: c-000477
type: synthesis
title: "Research: Evidence Freshness Stale Proof 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - evals
  - evidence
status: active
related:
  - "[[concepts/EvidenceFreshnessStaleProof边界]]"
  - "[[concepts/PostReleaseEvalDrift边界]]"
  - "[[concepts/EvalPortfolioMetricHierarchy边界]]"
  - "[[concepts/SafetyCaseAssuranceCase边界]]"
sources:
  - "[[sources/safety-case-maintenance-slr-2021]]"
  - "[[sources/dynamic-safety-cases-changing-world-2025]]"
  - "[[sources/runtime-confidence-safety-arguments-2026]]"
  - "[[sources/cmu-sei-drift-monitoring-ml-systems-2026]]"
  - "[[sources/nist-deployed-ai-monitoring-challenges-2026]]"
---

# Research: Evidence Freshness Stale Proof 边界

## Overview

本轮研究把 evidence freshness / stale proof 定义为第 6 层证据有效期边界：每条 eval、release card、safety case、monitor、benchmark、judge 或 red-team 证据，都必须说明有效范围、依赖、失效触发器和刷新动作。它回答“这份证据现在还能支持哪个决策”，而不是只记录“我们曾经测过”。

## Key Findings

- Safety case maintenance 文献指出，系统变更、额外证据和监管要求变化都会挑战原 safety case，维护过程需要识别受影响的 claim / evidence 元素。(Source: [[sources/safety-case-maintenance-slr-2021]])
- Dynamic safety case 研究强调，开放环境和自主系统不能只依赖设计时证据，必须把 runtime data、新知识和上下文变化纳入持续评估。(Source: [[sources/dynamic-safety-cases-changing-world-2025]])
- Runtime confidence update 论文把 design-time evidence 和 windowed runtime safety performance indicators 结合，让安全论证中的 claim confidence 随运行证据更新。(Source: [[sources/runtime-confidence-safety-arguments-2026]])
- CMU SEI 的 drift monitoring 文章区分 data drift、concept drift、label drift，并指出 drift 只有影响性能或 claim 时才应触发行动；这支持 stale proof 需要同时看分布变化和决策影响。(Source: [[sources/cmu-sei-drift-monitoring-ml-systems-2026]])
- NIST deployed AI monitoring 把 post-deployment monitoring 作为真实运行中发现性能退化、不可预期输出和上下文变化的机制；这支持给 release evidence 设 refresh trigger。(Source: [[sources/nist-deployed-ai-monitoring-challenges-2026]])

## Boundary Decision

- 主归属：6. 评估与可靠性层。
- 连接第 7 层：release gate、safety case、risk owner 和 incident response 只能消费 fresh 或被明确降权的证据。
- 连接第 8 层：stale evidence 可以触发 self-improvement 候选，但不能绕过 eval refresh 和 release gate。
- 不新增顶层：这是 eval evidence 的生命周期状态，不是单独“证据层”。

## Stale Proof Fields

- Claim / decision：这份证据支持哪个结论或动作。
- Artifact identity：model、prompt、tool、RAG、provider、judge、dataset、policy 版本。
- Validity scope：任务、人群、语言、风险层、时间窗口、部署范围。
- Freshness window：collected_at、observed_window、valid_until、review cadence。
- Invalidation triggers：artifact change、drift、incident、policy change、judge health drop、eval contamination。
- Proof status：fresh、stale、expired、superseded、invalidated、unknown。
- Action：use、downgrade、refresh、quarantine、restrict、rollback、case update。

## Open Questions

- 不同 risk tier 的证据有效期应该如何默认配置：小时、天、周、release 周期，还是事件触发？
- LLM-as-judge 证据的 stale proof 是否必须独立于被测模型的 stale proof？
- 对 provider silent update，应用侧如何证明“没有变化”而不是只证明“尚未观察到异常”？

## Sources

- [[sources/safety-case-maintenance-slr-2021]]
- [[sources/dynamic-safety-cases-changing-world-2025]]
- [[sources/runtime-confidence-safety-arguments-2026]]
- [[sources/cmu-sei-drift-monitoring-ml-systems-2026]]
- [[sources/nist-deployed-ai-monitoring-challenges-2026]]
