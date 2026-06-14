---
address: c-000403
type: source
title: "Deprecations"
source_url: https://platform.openai.com/docs/deprecations
source_type: documentation
author: "OpenAI"
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

# Deprecations

**来源**：OpenAI Developers Docs
**URL**：https://platform.openai.com/docs/deprecations

## 摘要

OpenAI deprecations 文档列出 API 模型和 endpoint 的弃用、legacy、shutdown、recommended replacement 和通知机制。文档明确软件依赖模型时需要随模型发布和退休做更新。

## 关键贡献

- 模型生命周期不仅是研究发布，也是应用兼容性和迁移问题。
- Deprecation、legacy、sunset / shutdown 要分开治理。
- recommended replacement 和 shutdown date 是 migration gate 的输入。
- 对本 vault 的意义：release / rollback gate 必须包含 provider deprecation monitoring、usage audit、replacement testing 和 migration deadline。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：3. 推理与能力层、6. 评估与可靠性层

## 关联

- [[concepts/ModelReleaseRollbackGate边界]]
- [[Research: Model release rollback gate 边界]]
