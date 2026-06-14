---
address: c-000355
type: source
title: "Data, privacy, and security for Foundry Models sold by Azure"
source_url: https://learn.microsoft.com/en-us/azure/foundry/responsible-ai/openai/data-privacy
source_type: documentation
author: "Microsoft Learn"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - ai
  - azure
  - data-privacy
  - provider-governance
status: active
related:
  - "[[concepts/MultiProviderGovernance边界]]"
  - "[[concepts/DataRightsPrivacyConsent边界]]"
---

# Data, privacy, and security for Foundry Models sold by Azure

**来源**：Microsoft Learn
**URL**：https://learn.microsoft.com/en-us/azure/foundry/responsible-ai/openai/data-privacy

## 摘要

Microsoft Learn 的 Azure Foundry Models 数据、隐私和安全文档说明客户上传或功能自动存储的数据如何保存、加密、删除，以及 fine-tuning、batch、guardrails 和 abuse monitoring 等功能的数据边界。它是 multi-provider governance 中 Azure 侧 provider policy 的官方锚点。

## 关键贡献

- 存储数据通常在客户 Azure tenant 的 Foundry resource 中、同一 geography 内静态保存，并使用 AES-256 加密。
- fine-tuning 上传的训练数据不会在未获许可或指令下用于训练生成式 AI foundation models。
- batch、preview feature、stored completions、guardrails 和 content logging 可能带来不同的数据处理路径。
- 对本 vault 的意义：provider policy 不能只按 vendor 粗分，必须按 feature、deployment type、region 和 retention 条件细分。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：3. 推理与能力层、6. 评估与可靠性层

## 关联

- [[concepts/MultiProviderGovernance边界]]
- [[Research: Multi-provider governance 边界]]
