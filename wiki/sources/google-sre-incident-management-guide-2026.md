---
address: c-000506
type: source
title: "Google SRE: Incident Management Guide"
source_url: https://sre.google/resources/practices-and-processes/incident-management-guide/
source_type: documentation
author: "Google SRE"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - sre
  - incident-management
  - training
status: active
related:
  - "[[concepts/MonitorTabletopRunbookDrill边界]]"
  - "[[concepts/MonitorOwnershipEscalationLadder边界]]"
  - "[[concepts/AIIncidentResponsePostmortem边界]]"
---

# Google SRE: Incident Management Guide

**来源**：Google SRE
**URL**：https://sre.google/resources/practices-and-processes/incident-management-guide/

## 摘要

Google SRE 的 incident management guide 强调事故管理需要清晰角色、训练、状态文档、指挥和执行分离。它把 incident command、operations、communications 和 planning 作为可重复执行的协作结构。

## 关键贡献

- 事故管理能力需要提前训练，不应在事故中临时形成。
- Incident commander 负责全局协调，operations 负责具体修复，communications 负责状态同步。
- 状态文档、handoff 和明确的 command post 能降低混乱和重复行动。
- 对本 vault 的意义：AI monitor drill 要验证角色是否能实际接管，而不是只验证监控指标存在。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[concepts/MonitorTabletopRunbookDrill边界]]
- [[Research: Monitor tabletop runbook drill 边界]]
