---
address: c-000441
type: source
title: "NIST AI RMF: Framing Risk and Risk Tolerance"
source_url: https://airc.nist.gov/airmf-resources/airmf/1-sec-risk/
source_type: framework
author: "NIST AI Resource Center"
published: 2023-01-26
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - ai
  - governance
  - risk-tolerance
  - nist
status: active
related:
  - "[[concepts/MetricConflictResolution边界]]"
  - "[[concepts/IntolerableRiskThresholdStopRule边界]]"
  - "[[concepts/AISafetyOpsGovernance边界]]"
  - "[[concepts/OverrideGovernanceResidualRiskAcceptance边界]]"
---

# NIST AI RMF: Framing Risk and Risk Tolerance

**来源**：NIST AI Resource Center
**URL**：https://airc.nist.gov/airmf-resources/airmf/1-sec-risk/
**发布时间**：2023-01-26

## 摘要

NIST AI RMF 的 Framing Risk 章节定义 AI risk、risk tolerance、risk prioritization，并说明 risk tolerance 应按组织、法规、行业、用途和社会规范确定。

## 关键贡献

- 风险是概率和影响程度的组合，但 AI 风险的负面影响、严重度和可预见性常难以评估。
- AI RMF 不替组织规定 risk tolerance；组织需要按 context 和 use case 定义可接受风险。
- 当 AI system 呈现 unacceptable negative risk levels，例如 imminent severe harm 或 catastrophic risk 时，development / deployment / use 应以安全方式停止，直到风险充分可管理。
- 对本 vault 的意义：intolerable risk threshold 是第 7 层组织 risk tolerance 的硬边界，消费第 6 层证据。
- 对 override governance 的意义：先定义 unacceptable / intolerable 边界，再讨论哪些 residual risk 可由 owner 有期限地接受。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[concepts/IntolerableRiskThresholdStopRule边界]]
- [[concepts/AISafetyOpsGovernance边界]]
- [[concepts/MetricConflictResolution边界]]
- [[concepts/OverrideGovernanceResidualRiskAcceptance边界]]
- [[Research: Intolerable risk threshold stop rule 边界]]
- [[Research: Override governance residual risk acceptance 边界]]
