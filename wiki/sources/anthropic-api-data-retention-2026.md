---
address: c-000358
type: source
title: "API and data retention"
source_url: https://platform.claude.com/docs/en/manage-claude/api-and-data-retention
source_type: documentation
author: "Anthropic"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - ai
  - anthropic
  - data-retention
  - zdr
status: active
related:
  - "[[concepts/MultiProviderGovernance边界]]"
  - "[[concepts/DataRightsPrivacyConsent边界]]"
---

# API and data retention

**来源**：Anthropic Claude API Docs
**URL**：https://platform.claude.com/docs/en/manage-claude/api-and-data-retention

## 摘要

Anthropic Claude API 数据保留文档说明不同 API 和功能有不同存储需求，保留数据不会在无明确许可下用于模型训练，并定义 Zero Data Retention、HIPAA readiness、Claude Code、managed agents、第三方 integrations 等边界。

## 关键贡献

- ZDR 不是所有产品和功能的全局属性；需要按 API、feature、product interface 和合同边界判断。
- 外部服务、第三方 integrations、partner platforms 和 managed agents 可能有不同保留模型。
- HIPAA-ready API access 体现了 regulated data 需要组织级配置和 feature restrictions。
- 对本 vault 的意义：multi-provider policy 必须区分 API endpoint、产品界面、第三方平台和 tool integration。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：5. Agent 系统层、6. 评估与可靠性层

## 关联

- [[concepts/MultiProviderGovernance边界]]
- [[Research: Multi-provider governance 边界]]
