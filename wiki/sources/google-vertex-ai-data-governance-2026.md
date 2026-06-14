---
address: c-000320
type: source
title: "Vertex AI generative AI data governance"
source_url: https://docs.cloud.google.com/vertex-ai/generative-ai/docs/data-governance
source_type: documentation
author: "Google Cloud"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - ai
  - google-cloud
  - vertex-ai
  - data-governance
status: active
related:
  - "[[concepts/DataRightsPrivacyConsent边界]]"
  - "[[concepts/ModelRoutingMixture边界]]"
---

# Vertex AI generative AI data governance

**来源**：Google Cloud Documentation
**URL**：https://docs.cloud.google.com/vertex-ai/generative-ai/docs/data-governance

## 摘要

Google Cloud Vertex AI 的生成式 AI 数据治理文档说明客户数据的处理、隔离、保留、加密和 zero data retention 选项，并说明客户数据不会用于训练基础模型。它把 provider 层数据控制接到产品层权限设计。

## 关键贡献

- 明确生成式 AI 平台需要数据保留、加密、区域和访问控制。
- 把 zero data retention 作为更严格数据边界，而不是默认能力。
- 对本 vault 的意义：多 provider AI 产品必须把 provider 数据治理特性纳入 model routing 和 tool routing。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：3. 推理与能力层、6. 评估与可靠性层

## 关联

- [[concepts/DataRightsPrivacyConsent边界]]
- [[Research: Data rights privacy consent 边界]]
