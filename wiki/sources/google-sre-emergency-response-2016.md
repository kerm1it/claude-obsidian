---
address: c-000368
type: source
title: "Emergency Response"
source_url: https://sre.google/sre-book/emergency-response/
source_type: book-chapter
author: "Google SRE"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - sre
  - incident-response
  - reliability
status: active
related:
  - "[[concepts/AIIncidentResponsePostmortem边界]]"
  - "[[concepts/Serving成本延迟边界]]"
---

# Emergency Response

**来源**：Google SRE Book
**URL**：https://sre.google/sre-book/emergency-response/

## 摘要

Google SRE 的 Emergency Response 章节通过真实事故案例说明 incident response process、rollback testing、out-of-band communications、backup tools、monitoring、training 和演练的重要性。

## 关键贡献

- 事故流程需要被传播、测试和演练，否则真正事故中不会自然生效。
- 回滚程序必须提前在测试环境验证；临场发现回滚不可用会延长事故。
- 监控、通信和备用访问路径同样是事故系统的一部分。
- 对本 vault 的意义：AI incident response 也需要 rollback playbook、备用 provider、禁用工具、降级人工和 out-of-band communication。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：3. 推理与能力层、6. 评估与可靠性层

## 关联

- [[concepts/AIIncidentResponsePostmortem边界]]
- [[Research: AI incident response postmortem 边界]]
