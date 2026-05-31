---
address: c-000369
type: source
title: "Postmortem Culture: Learning from Failure"
source_url: https://sre.google/sre-book/postmortem-culture/
source_type: book-chapter
author: "Google SRE"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - sre
  - postmortem
  - reliability
status: active
related:
  - "[[concepts/AIIncidentResponsePostmortem边界]]"
  - "[[concepts/AISafetyOpsGovernance边界]]"
---

# Postmortem Culture: Learning from Failure

**来源**：Google SRE Book
**URL**：https://sre.google/sre-book/postmortem-culture/

## 摘要

Google SRE 的 Postmortem Culture 章节说明 postmortem 是事故学习机制：记录影响、处置、root/contributing causes 和 follow-up actions，并以 blameless culture 避免隐瞒和归咎。

## 关键贡献

- Postmortem 触发条件可包括用户可见降级、数据丢失、人工介入、恢复时间超阈值和监控失败。
- Blameless postmortem 关注促成因素和系统改进，不把事故写成惩罚。
- Postmortem 价值来自 action items 和组织学习，而不是文档本身。
- 对本 vault 的意义：AI postmortem 必须把事故变成 eval、monitor、policy、tool gate、data fix 或 provider review。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层、8. 自我改进与前沿层

## 关联

- [[concepts/AIIncidentResponsePostmortem边界]]
- [[Research: AI incident response postmortem 边界]]
