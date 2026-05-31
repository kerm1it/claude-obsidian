---
address: c-000323
type: source
title: "NIST AI RMF Generative AI Profile"
source_url: https://www.nist.gov/publications/artificial-intelligence-risk-management-framework-generative-artificial-intelligence
source_type: standard
author: "NIST"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - ai
  - nist
  - risk-management
  - privacy
status: active
related:
  - "[[concepts/DataRightsPrivacyConsent边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
  - "[[concepts/AIIncidentResponsePostmortem边界]]"
  - "[[concepts/DatasetLineageProvenanceGraph边界]]"
---

# NIST AI RMF Generative AI Profile

**来源**：NIST
**URL**：https://www.nist.gov/publications/artificial-intelligence-risk-management-framework-generative-artificial-intelligence

## 摘要

NIST AI RMF Generative AI Profile 将生成式 AI 风险放入 govern、map、measure、manage 框架，覆盖数据隐私、数据来源、数据质量、信息安全、有害输出和滥用等风险。

## 关键贡献

- 将 privacy 作为生成式 AI 风险管理的一部分，而不是法律合规的旁支。
- 支持用风险识别、测量和管理流程约束训练数据、RAG、memory、eval 和产品 telemetry。
- 支持把数据来源、第三方组件、系统变更和审计证据放进 lifecycle risk management，而不是只做上线前检查。
- 对本 vault 的意义：第 6 层 eval/reliability 和第 7 层 data rights 要共同形成可审计 gate。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/DataRightsPrivacyConsent边界]]
- [[concepts/AIIncidentResponsePostmortem边界]]
- [[concepts/DatasetLineageProvenanceGraph边界]]
- [[Research: Data rights privacy consent 边界]]
