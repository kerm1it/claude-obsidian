---
address: c-000440
type: synthesis
title: "Research: Intolerable risk threshold stop rule 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - governance
  - risk-threshold
status: active
related:
  - "[[concepts/IntolerableRiskThresholdStopRule边界]]"
  - "[[concepts/AISafetyOpsGovernance边界]]"
  - "[[concepts/EvalResultInterpretationDecisionThreshold边界]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
sources:
  - "[[sources/nist-ai-rmf-risk-tolerance-2023]]"
  - "[[sources/nist-ai-rmf-1-0-2023]]"
  - "[[sources/openai-preparedness-framework-2025]]"
  - "[[sources/anthropic-responsible-scaling-policy-v3-2026]]"
  - "[[sources/deepmind-frontier-safety-framework-2025]]"
  - "[[sources/eu-ai-act-prohibited-practices-2024]]"
  - "[[sources/microsoft-responsible-ai-standard-2022]]"
  - "[[sources/iso-iec-42001-ai-management-system-2023]]"
---

# Research: Intolerable risk threshold stop rule 边界

## Overview

本轮研究把 intolerable risk threshold / stop rule 归入第 7 层产品与组织层。第 6 层负责测量风险，第 7 层负责定义哪些风险是 acceptable、tolerable with safeguards、intolerable / prohibited，并把 hard stop 接到 release gate、训练、部署、供应商和事故响应。

稳定结论：**不可容忍风险阈值不是又一个 eval 分数；它是组织和法律层的 no-go 规则，必须绑定证据、owner、required safeguards、残余风险和复审。**

## Key Findings

- NIST AI RMF 明确风险 tolerance 是组织或 AI actor 愿意承受风险以实现目标的程度，并指出 unacceptable negative risk 时 development/deployment 应以安全方式停止，直到风险被充分管理。（Source: [[sources/nist-ai-rmf-risk-tolerance-2023]]）
- OpenAI Preparedness Framework 把 frontier capability 分成 High / Critical 等阈值，并把阈值和 safeguards、Safety Advisory Group review、leadership decision 绑定。（Source: [[sources/openai-preparedness-framework-2025]]）
- Anthropic RSP 用 if-then capability thresholds 和 required safeguards 表达“能力达到阈值就升级 safeguard”，并在 2026 年版本中强调 Risk Reports、Roadmaps、外部审查和现实可执行性。（Source: [[sources/anthropic-responsible-scaling-policy-v3-2026]]）
- Google DeepMind FSF 用 Critical Capability Levels、deployment/security mitigations 和 safety case review 管理 severe harm 风险，并持续新增风险域如 harmful manipulation。（Source: [[sources/deepmind-frontier-safety-framework-2025]]）
- EU AI Act Article 5 直接把某些 AI practices 归为 prohibited/unacceptable risk；这类风险不是内部权衡问题，而是 hard block。（Source: [[sources/eu-ai-act-prohibited-practices-2024]]）
- ISO/IEC 42001 和 Microsoft Responsible AI Standard 提醒：threshold 需要管理系统、impact assessment、责任机制和持续改进承载，否则会退化成政策文本。（Source: [[sources/iso-iec-42001-ai-management-system-2023]]、[[sources/microsoft-responsible-ai-standard-2022]]）

## 主归属

- 主归属：7. 产品与组织层
- 上游：第 6 层 eval、red-team、capability assessment、monitoring、incident、safeguard evidence
- 下游：release/rollback gate、scope restriction、required safeguards、external review、risk report、incident response
- 反哺：发现阈值模糊或误放行后，更新 eval、risk taxonomy、safeguard 和 release rule

## 稳定框架

```text
risk evidence
    -> risk tolerance and capability threshold
    -> required safeguards / prohibited use / no-go condition
    -> residual risk review
    -> stop, pause, restrict, rollback, external review, or accept with owner
    -> production monitoring and periodic threshold refresh
```

## 与相邻概念的边界

- [[concepts/EvalResultInterpretationDecisionThreshold边界]]：普通 threshold 处理“这个分数是否足以决策”；本轮处理“哪些风险不能被分数或收益抵消”。
- [[concepts/AISafetyOpsGovernance边界]]：safety ops 是完整治理操作系统；本轮是其中的 hard-stop 规则组件。
- [[concepts/ModelReleaseRollbackGate边界]]：release gate 是执行点；本轮提供 no-go、pause、external review 和 required safeguard 条件。
- [[concepts/AIIncidentResponsePostmortem边界]]：事故响应处理已经发生的 harm；stop rule 也要从 near miss 和 incident 学习，更新 future gate。

## Open Questions

- 对 frontier capability，怎样在 eval 不确定时定义“已接近阈值”的 precautionary rule？
- 对商业产品，高影响但非灾难性风险如何在法律、用户承诺和业务收益之间确定 residual risk owner？
- 外部审查应该在什么风险类别和阈值上成为强制要求？

## Sources

- [[sources/nist-ai-rmf-risk-tolerance-2023]]
- [[sources/openai-preparedness-framework-2025]]
- [[sources/anthropic-responsible-scaling-policy-v3-2026]]
- [[sources/deepmind-frontier-safety-framework-2025]]
- [[sources/eu-ai-act-prohibited-practices-2024]]
- [[sources/iso-iec-42001-ai-management-system-2023]]
- [[sources/microsoft-responsible-ai-standard-2022]]
