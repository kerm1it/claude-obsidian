---
address: c-000486
type: source
title: "Google SRE: Being On-Call"
source_url: https://sre.google/sre-book/being-on-call/
source_type: book-chapter
author: "Google SRE"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - sre
  - on-call
  - escalation
  - monitoring
status: active
related:
  - "[[concepts/MonitorOwnershipEscalationLadder边界]]"
---

# Google SRE: Being On-Call

**来源**：Google SRE Book
**URL**：https://sre.google/sre-book/being-on-call/

## 摘要

Google SRE 的 Being On-Call 章节说明 on-call engineer 如何在约定响应时间内处理生产系统问题，并在需要时升级给其他成员或 incident-management protocol。

## 关键贡献

- On-call engineer 要在分钟级响应时间内确认和 triage 生产告警。
- Primary / secondary rotation 提供 fallback 和工作分配。
- Clear escalation paths、well-defined incident-management procedures 和 blameless postmortem 是 on-call 支撑资源。
- 对本 vault 的意义：AI monitor 要能 page 到人、分出 primary/secondary、并在复杂时进入 incident command，而不是停在 dashboard。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[concepts/MonitorOwnershipEscalationLadder边界]]
- [[Research: Monitor ownership escalation ladder 边界]]
