---
address: c-000487
type: source
title: "Google SRE: Managing Incidents"
source_url: https://sre.google/sre-book/managing-incidents/
source_type: book-chapter
author: "Google SRE"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - sre
  - incident-management
  - escalation
  - operations
status: active
related:
  - "[[concepts/MonitorOwnershipEscalationLadder边界]]"
  - "[[concepts/MonitorTabletopRunbookDrill边界]]"
---

# Google SRE: Managing Incidents

**来源**：Google SRE Book
**URL**：https://sre.google/sre-book/managing-incidents/

## 摘要

Google SRE 的 Managing Incidents 章节把事故响应拆成 Incident Command、Operational Work、Communication 和 Planning 等角色，并强调 live incident state document、recognized command post 和 clear handoff。

## 关键贡献

- Incident commander 持有全局状态，按需要组织任务和分配职责。
- Ops lead 负责具体系统操作，Communication 负责状态更新和 stakeholder 接口。
- Live incident state document 和清晰交接减少混乱和重复行动。
- 对本 vault 的意义：AI monitor 升级成 incident 后，需要角色分离和状态文档，不能让修复者同时承担全局协调和外部沟通。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[concepts/MonitorOwnershipEscalationLadder边界]]
- [[concepts/MonitorTabletopRunbookDrill边界]]
- [[Research: Monitor ownership escalation ladder 边界]]
- [[Research: Monitor tabletop runbook drill 边界]]
