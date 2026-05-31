---
address: c-000357
type: source
title: "Monitor model invocation using CloudWatch Logs and Amazon S3"
source_url: https://docs.aws.amazon.com/bedrock/latest/userguide/model-invocation-logging.html
source_type: documentation
author: "Amazon Web Services"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - ai
  - aws
  - bedrock
  - logging
  - observability
status: active
related:
  - "[[concepts/MultiProviderGovernance边界]]"
  - "[[concepts/AISafetyOpsGovernance边界]]"
---

# Monitor model invocation using CloudWatch Logs and Amazon S3

**来源**：AWS Documentation
**URL**：https://docs.aws.amazon.com/bedrock/latest/userguide/model-invocation-logging.html

## 摘要

Amazon Bedrock model invocation logging 文档说明客户可以把 Bedrock 调用日志、model input data、model output data 和 metadata 发送到 CloudWatch Logs 或 Amazon S3。日志默认关闭；启用后会按配置保存，直到 logging configuration 被删除。

## 关键贡献

- “默认不存/不训练”不足以描述真实数据路径；客户启用 invocation logging 后会主动创建 prompt/output 副本。
- 日志目的地必须在同一 account 和 Region，适合纳入 provider policy、data residency 和 audit 设计。
- 文档明确 full request data、response data 和 metadata 可被收集，这要求对日志 bucket、KMS、retention、masking 和访问控制做治理。
- 对本 vault 的意义：multi-provider governance 必须把 customer-owned logs 与 provider-owned logs 分开建模。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[concepts/MultiProviderGovernance边界]]
- [[Research: Multi-provider governance 边界]]
