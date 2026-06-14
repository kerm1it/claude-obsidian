---
address: c-000356
type: source
title: "Data protection in Amazon Bedrock"
source_url: https://docs.aws.amazon.com/bedrock/latest/userguide/data-protection.html
source_type: documentation
author: "Amazon Web Services"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - ai
  - aws
  - bedrock
  - data-protection
status: active
related:
  - "[[concepts/MultiProviderGovernance边界]]"
  - "[[concepts/DataRightsPrivacyConsent边界]]"
---

# Data protection in Amazon Bedrock

**来源**：AWS Documentation
**URL**：https://docs.aws.amazon.com/bedrock/latest/userguide/data-protection.html

## 摘要

Amazon Bedrock 数据保护文档把 Bedrock 放在 AWS shared responsibility model 中，强调 IAM、MFA、CloudTrail、encryption、Macie 和敏感信息最小化。文档还说明模型供应商没有 Bedrock model deployment accounts 的访问权，也不能访问 Bedrock logs、customer prompts 或 completions。

## 关键贡献

- Provider governance 需要同时管理 AWS account/IAM、logging、encryption、敏感字段和 provider 隔离。
- AWS 建议不要把敏感信息放入 tags 或 free-form name fields，因为这些字段可能进入 billing 或 diagnostic logs。
- 模型供应商与 Bedrock deployment accounts 隔离，是多 provider 场景中“谁能看到 prompt/completion”的重要差异。
- 对本 vault 的意义：多 provider 比较要覆盖模型供应商、云平台代理、日志路径和客户账号控制，而不只是模型能力。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：5. Agent 系统层、6. 评估与可靠性层

## 关联

- [[concepts/MultiProviderGovernance边界]]
- [[Research: Multi-provider governance 边界]]
