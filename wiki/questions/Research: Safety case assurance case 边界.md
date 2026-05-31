---
address: c-000460
type: synthesis
title: "Research: Safety case assurance case 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - safety-case
  - assurance-case
  - governance
status: active
related:
  - "[[concepts/SafetyCaseAssuranceCase边界]]"
  - "[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]"
  - "[[concepts/IntolerableRiskThresholdStopRule边界]]"
  - "[[concepts/AISafetyOpsGovernance边界]]"
sources:
  - "[[sources/safety-cases-advanced-ai-systems-2024]]"
  - "[[sources/aisi-frontier-ai-safety-case-cyber-2024]]"
  - "[[sources/big-argument-ai-safety-cases-2025]]"
  - "[[sources/structured-safety-case-ai-systems-2026]]"
  - "[[sources/nist-ai-rmf-1-0-2023]]"
  - "[[sources/openai-preparedness-framework-2025]]"
  - "[[sources/anthropic-responsible-scaling-policy-v3-2026]]"
  - "[[sources/deepmind-frontier-safety-framework-2025]]"
---

# Research: Safety case assurance case 边界

## Overview

本轮研究把 safety case / assurance case 归入第 7 层产品与组织层，作为高风险 AI 系统的发布论证边界。第 6 层提供 eval、red-team、monitoring、lineage、release card 和 production correlation；第 7 层把这些证据组织成 claims-arguments-evidence，并决定残余风险是否可接受。

稳定结论：**safety case 不是“更多 eval”，而是把多源证据和不确定性组织成可审查论证，说明为什么一个特定 AI 系统在特定上下文中可以部署、必须限制，或应该停止。**

## Key Findings

- Clymer 等提出 advanced AI safety case 框架，把论证分为 inability to cause catastrophe、control measures、trustworthiness despite harmful capability、deference to AI advisors 四类。（Source: [[sources/safety-cases-advanced-ai-systems-2024]]）
- UK AISI 的 cyber inability template 用 Claims-Arguments-Evidence 把 risk model、proxy tasks、evaluation settings 和 eval results 连成结构化安全论证。（Source: [[sources/aisi-frontier-ai-safety-case-cyber-2024]]）
- BIG Argument 强调 AI safety case 要 balanced、integrated、grounded：同时处理技术、社会技术、伦理和上下文风险。（Source: [[sources/big-argument-ai-safety-cases-2025]]）
- 2026 structured safety case 论文给出 AI-specific claim、argument 和 evidence taxonomies，并强调 generative/agentic AI 的动态行为需要 adaptive, auditable safety cases。（Source: [[sources/structured-safety-case-ai-systems-2026]]）
- NIST AI RMF、OpenAI Preparedness Framework、Anthropic RSP 和 DeepMind FSF 提供 risk taxonomy、capability threshold、safeguard、review 和 monitoring 结构，可作为 safety case 的治理输入。（Source: [[sources/nist-ai-rmf-1-0-2023]] 等）

## 主归属

- 主归属：7. 产品与组织层
- 证据接口：6. 评估与可靠性层
- 上游：risk model、eval、red-team、release card、stop rule、offline/online correlation、monitoring、incident evidence
- 下游：approval / restrict / pause / rollback / external review / residual risk acceptance

## 稳定框架

```text
top claim and context
    -> risk model and stakeholder harm
    -> subclaims and argument pattern
    -> evidence map with uncertainty and defeaters
    -> independent review and residual risk decision
    -> deployment constraint and maintenance trigger
```

## 与相邻概念的边界

- [[concepts/EvalUncertaintyCommunicationReleaseCard边界]]：release card 是单次变更的轻量证据包；safety case 是高风险系统的完整可审查论证。
- [[concepts/IntolerableRiskThresholdStopRule边界]]：stop rule 定义 no-go 条件；safety case 论证没有触发 no-go 时为什么残余风险可接受。
- [[concepts/AISafetyOpsGovernance边界]]：safety ops 是运行系统；safety case 是重大发布或高风险用例的审查 artifact。
- [[concepts/ModelReleaseRollbackGate边界]]：release gate 执行限制、发布和回滚；safety case 提供高风险 gate 的论证依据。

## Open Questions

- 对快速迭代的 agent / tool system，safety case 的刷新粒度应该是模型、prompt、tool、workflow 还是产品能力？
- 对非灾难性但高影响的产品风险，是否需要完整 safety case，还是 release card + risk register 足够？
- Safety case 的 counterevidence 和 defeater 应如何自动从 incident、online eval、judge drift 和 user reports 中触发？

## Sources

- [[sources/safety-cases-advanced-ai-systems-2024]]
- [[sources/aisi-frontier-ai-safety-case-cyber-2024]]
- [[sources/big-argument-ai-safety-cases-2025]]
- [[sources/structured-safety-case-ai-systems-2026]]
- [[sources/nist-ai-rmf-1-0-2023]]
- [[sources/openai-preparedness-framework-2025]]
- [[sources/anthropic-responsible-scaling-policy-v3-2026]]
- [[sources/deepmind-frontier-safety-framework-2025]]
