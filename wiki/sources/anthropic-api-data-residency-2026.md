---
address: c-000359
type: source
title: "Data residency"
source_url: https://platform.claude.com/docs/en/build-with-claude/data-residency
source_type: documentation
author: "Anthropic"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - ai
  - anthropic
  - data-residency
  - provider-governance
status: active
related:
  - "[[concepts/MultiProviderGovernance边界]]"
  - "[[concepts/DataRightsPrivacyConsent边界]]"
---

# Data residency

**来源**：Anthropic Claude API Docs
**URL**：https://platform.claude.com/docs/en/build-with-claude/data-residency

## 摘要

Anthropic data residency 文档说明 API 可以通过 `inference_geo` 控制模型推理运行地，并通过 workspace geo 控制 at-rest storage 和部分 endpoint processing 的地理位置。它还说明 workspace 可以限制允许的 inference geos，并在响应 usage 中返回实际 inference geo。

## 关键贡献

- Provider governance 需要把 region/residency 作为可执行 routing constraint，而不是法律文档里的备注。
- Per-request `inference_geo` 与 workspace-level `allowed_inference_geos` 形成两级控制。
- 第三方平台上的 Claude 不使用同一个 `inference_geo` 参数，而由平台 endpoint 或 inference profile 决定地域。
- 对本 vault 的意义：多 provider 系统必须把 direct API、AWS Bedrock、Google Vertex AI 等通道分别建模。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：3. 推理与能力层、6. 评估与可靠性层

## 关联

- [[concepts/MultiProviderGovernance边界]]
- [[Research: Multi-provider governance 边界]]
