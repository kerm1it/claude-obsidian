---
address: c-000335
type: synthesis
title: "Research: AI safety ops governance 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - governance
  - safety-ops
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/AISafetyOpsGovernance边界]]"
  - "[[concepts/ProductOrganizationLayer边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
  - "[[concepts/ToolRiskPermissioning边界]]"
sources:
  - "[[sources/nist-ai-rmf-1-0-2023]]"
  - "[[sources/iso-iec-42001-ai-management-system-2023]]"
  - "[[sources/openai-preparedness-framework-2025]]"
  - "[[sources/anthropic-responsible-scaling-policy-v3-2026]]"
  - "[[sources/deepmind-frontier-safety-framework-2025]]"
  - "[[sources/microsoft-responsible-ai-standard-2022]]"
  - "[[sources/eu-ai-act-risk-management-post-market-2024]]"
  - "[[sources/google-saif-controls-2026]]"
---

# Research: AI safety ops governance 边界

## Overview

AI Safety Ops / Governance 主属第 7 层产品与组织层。它把第 6 层 eval、red-team、monitoring 和 incident evidence 转成组织可执行的 risk register、release gate、owner、safeguards、exception、post-market monitoring 和 audit trail。

## Key Findings

- NIST AI RMF 将 AI 风险管理拆成 Govern、Map、Measure、Manage 四个函数；Govern 是贯穿其他函数的组织治理层（Source: [[sources/nist-ai-rmf-1-0-2023]]）。
- ISO/IEC 42001 将 AI management system 定义为组织为 AI 系统建立政策、目标和实现流程的管理系统，说明 governance 是管理系统而不是单个 checklist（Source: [[sources/iso-iec-42001-ai-management-system-2023]]）。
- OpenAI Preparedness Framework 用 capability reports、safeguards reports、Safety Advisory Group 和领导层决策把模型风险评估接到发布治理（Source: [[sources/openai-preparedness-framework-2025]]）。
- Anthropic RSP v3 用 AI Safety Levels、Required Safeguards、safeguard assessments、risk reports 和 roadmap 管理更高能力模型的风险（Source: [[sources/anthropic-responsible-scaling-policy-v3-2026]]）。
- Google DeepMind Frontier Safety Framework 用 Critical Capability Levels、deployment mitigations、security mitigations 和 safety case review 管理 frontier risk（Source: [[sources/deepmind-frontier-safety-framework-2025]]）。
- Microsoft Responsible AI Standard 把 fairness、reliability/safety、privacy/security、inclusiveness、transparency、accountability 转成 product development requirements 和 impact assessment（Source: [[sources/microsoft-responsible-ai-standard-2022]]）。
- EU AI Act 对高风险系统要求 risk management system、technical documentation、quality management 和 post-market monitoring；它把 AI safety ops 的部分产物外部化为法规义务（Source: [[sources/eu-ai-act-risk-management-post-market-2024]]）。
- Google SAIF 控制框架把 secure-by-design、risk management、AI supply chain、testing/evaluation、logging/monitoring 等控制项组织成 AI 安全运行框架（Source: [[sources/google-saif-controls-2026]]）。

## Stable Definition

```text
eval / red-team / incident / model capability evidence
    -> risk classification and owner assignment
    -> safeguards and release gate
    -> production monitoring
    -> incident response and audit
    -> periodic review and roadmap update
```

## Boundary Rules

| 问题 | 稳定答案 |
|---|---|
| Governance 是不是合规文件？ | 不是。文件只是证据，核心是 owner、gate、monitoring 和 incident loop。 |
| Eval 通过是否等于可发布？ | 不等于。发布还要看 residual risk、用途、用户群、权限和运营准备。 |
| Safety ops 是否属于安全团队？ | 部分属于，但必须跨产品、工程、法务、数据、安全、支持和领导层。 |
| Risk register 是否足够？ | 不够。风险必须连接 mitigation、owner、due date、复测和 release decision。 |
| Frontier safety 和普通产品治理是否同一层？ | 同属第 7 层，但风险 taxonomy、阈值和审批层级不同。 |

## Open Questions

- 如何量化 residual risk，让 release gate 不被 KPI 和商业压力稀释。
- AI incident 的行业通用严重度分级、披露义务和复盘格式仍未统一。
- Agentic systems 的自治工具链让风险跨 prompt、tool、data、identity、provider 扩散，现有 governance artifact 需要继续扩展。

## Sources

- [[sources/nist-ai-rmf-1-0-2023]]
- [[sources/iso-iec-42001-ai-management-system-2023]]
- [[sources/openai-preparedness-framework-2025]]
- [[sources/anthropic-responsible-scaling-policy-v3-2026]]
- [[sources/deepmind-frontier-safety-framework-2025]]
- [[sources/microsoft-responsible-ai-standard-2022]]
- [[sources/eu-ai-act-risk-management-post-market-2024]]
- [[sources/google-saif-controls-2026]]
