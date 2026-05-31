---
address: c-000429
type: source
title: "Deprecations"
source_url: https://docs.together.ai/docs/deprecations
source_type: documentation
author: "Together AI"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - ai
  - provider-lifecycle
  - deprecation
status: active
related:
  - "[[concepts/ProductionContractCompatibilityTest边界]]"
  - "[[concepts/MultiProviderGovernance边界]]"
---

# Deprecations

**来源**：Together AI Docs
**URL**：https://docs.together.ai/docs/deprecations

## 摘要

Together AI deprecations 文档说明其模型生命周期政策，包括 upgrades、redirects 和 scheduled deprecations。它展示了多 provider 系统中模型生命周期信号需要被持续监控。

## 关键贡献

- Provider 会持续引入新模型、升级现有模型并 deprecate 旧模型。
- Lifecycle policy、redirects 和 scheduled deprecations 是应用侧兼容性测试和迁移计划的输入。
- 对本 vault 的意义：multi-provider governance 不能只管数据和合约，还要把模型生命周期变更接入 production contract 和 release gate。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[concepts/ProductionContractCompatibilityTest边界]]
- [[concepts/MultiProviderGovernance边界]]
