---
address: c-000405
type: source
title: "Model deprecations"
source_url: https://platform.claude.com/docs/en/resources/model-deprecations
source_type: documentation
author: "Anthropic"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - ai
  - model-lifecycle
  - deprecation
status: active
related:
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/MultiProviderGovernance边界]]"
  - "[[concepts/ProductionContractCompatibilityTest边界]]"
---

# Model deprecations

**来源**：Anthropic Docs
**URL**：https://platform.claude.com/docs/en/resources/model-deprecations

## 摘要

Anthropic model deprecations 文档定义 Active、Legacy、Deprecated、Retired 四种状态，说明 retirement date、recommended replacement、客户通知、usage audit 和迁移测试建议。

## 关键贡献

- 模型生命周期状态可以成为 release gate 的结构化输入。
- Deprecated 仍可用但不推荐，Retired 则请求失败。
- replacement model 需要在 retirement date 前用应用任务充分测试。
- 对本 vault 的意义：provider model deprecation 属于第 7 层迁移治理，必须接入 eval、usage audit、owner 和 deadline。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：3. 推理与能力层、6. 评估与可靠性层

## 关联

- [[concepts/ModelReleaseRollbackGate边界]]
- [[Research: Model release rollback gate 边界]]
