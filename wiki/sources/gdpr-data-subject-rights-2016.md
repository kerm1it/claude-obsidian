---
address: c-000322
type: source
title: "GDPR data subject rights"
source_url: https://eur-lex.europa.eu/eli/reg/2016/679/oj
source_type: regulation
author: "European Union"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - privacy
  - gdpr
  - data-rights
  - regulation
status: active
related:
  - "[[concepts/DataRightsPrivacyConsent边界]]"
  - "[[concepts/DataDeletionUnlearningImpact边界]]"
  - "[[concepts/EvidenceMinimizationPrivacyPreservingAuditPacket边界]]"
---

# GDPR data subject rights

**来源**：EUR-Lex
**URL**：https://eur-lex.europa.eu/eli/reg/2016/679/oj

## 摘要

GDPR 是个人数据处理的基础法规之一，要求个人数据处理具备透明性、合法基础、目的限制、数据最小化、准确性、存储期限限制、安全性和数据主体权利。

## 关键贡献

- 固定了访问、更正、删除、限制处理、可携带、反对等权利。
- 强调 purpose limitation 和 data minimization，这直接约束 AI 产品的数据飞轮。
- 对本 vault 的意义：data rights 不能只写在隐私政策里，必须变成系统可执行的 deletion/export/retention/audit 流程。
- 对 deletion/unlearning 的意义：Article 17 类删除权是工程触发器之一，但请求并非无条件；系统要记录范围、法律/合同依据、例外、下游影响、执行证据和用户/组织响应。
- 对 privacy-preserving audit packet 的意义：审计证据也要遵守目的限制、最小化、保存期限和可证明责任，不能因为“以后可能审计”而长期保存完整用户现场。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[concepts/DataRightsPrivacyConsent边界]]
- [[concepts/DataDeletionUnlearningImpact边界]]
- [[concepts/EvidenceMinimizationPrivacyPreservingAuditPacket边界]]
- [[Research: Data rights privacy consent 边界]]
- [[Research: Data deletion unlearning impact 边界]]
