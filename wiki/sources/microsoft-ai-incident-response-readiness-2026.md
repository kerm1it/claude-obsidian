---
address: c-000488
type: source
title: "Incident response readiness for AI systems"
source_url: https://learn.microsoft.com/en-us/security/zero-trust/sfi/incident-response-ai-systems
source_type: documentation
author: "Microsoft Learn"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - ai
  - incident-response
  - observability
  - monitoring
status: active
related:
  - "[[concepts/MonitorOwnershipEscalationLadder边界]]"
  - "[[concepts/MonitorTabletopRunbookDrill边界]]"
---

# Incident response readiness for AI systems

**来源**：Microsoft Learn
**URL**：https://learn.microsoft.com/en-us/security/zero-trust/sfi/incident-response-ai-systems

## 摘要

Microsoft 的 AI incident response readiness 文档指出，AI 系统的非确定性、上下文相关严重度、根因模糊和遥测缺口，会让传统 incident response 不够用，需要 AI-specific taxonomy、observability、staged remediation、ownership 和 escalation triggers。

## 关键贡献

- 传统安全监控不一定捕获 anomalous output、classifier confidence shifts 或 post-update behavior。
- AI incident playbook 需要明确 entry/exit criteria、ownership assignments 和 escalation triggers。
- Staged remediation 包括 first-hour containment、24-hour expansion 和 longer-term source fix。
- 要求测试 cross-functional coordination，并保护处理有害内容的响应人员。
- 对本 vault 的意义：AI monitor ownership 必须覆盖输出异常、用户报告、模型更新后行为和人类响应者负担。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[concepts/MonitorOwnershipEscalationLadder边界]]
- [[concepts/MonitorTabletopRunbookDrill边界]]
- [[Research: Monitor ownership escalation ladder 边界]]
- [[Research: Monitor tabletop runbook drill 边界]]
