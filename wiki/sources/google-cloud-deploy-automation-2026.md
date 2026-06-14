---
address: c-000406
type: source
title: "Automate your deployment"
source_url: https://cloud.google.com/deploy/docs/automation
source_type: documentation
author: "Google Cloud"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - deployment
  - canary
  - rollback
status: active
related:
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/AIIncidentResponsePostmortem边界]]"
  - "[[concepts/ProductionContractCompatibilityTest边界]]"
---

# Automate your deployment

**来源**：Google Cloud Documentation
**URL**：https://cloud.google.com/deploy/docs/automation

## 摘要

Google Cloud Deploy automation 文档说明如何自动推进 rollout、canary phase、retry failed rollout，以及在重试失败后创建新 rollout 回滚到目标上的最近成功 release。

## 关键贡献

- Canary phase、wait time、automatic advancement 是 staged rollout 的通用工程模式。
- repair rollout / retry / rollback 是 release gate 的自动执行机制。
- rollback target 应该是最近成功的 release，而不是临时猜测版本。
- 对本 vault 的意义：AI release gate 也应把 canary、retry、rollback 和 automation run 变成可审计 artifact。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层、5. Agent 系统层

## 关联

- [[concepts/ModelReleaseRollbackGate边界]]
- [[Research: Model release rollback gate 边界]]
