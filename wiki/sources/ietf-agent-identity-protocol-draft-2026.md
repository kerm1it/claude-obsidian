---
address: c-000362
type: source
title: "Agent Identity Protocol Internet-Draft"
source_url: https://www.ietf.org/archive/id/draft-aip-agent-identity-protocol-00.html
source_type: draft
author: "IETF Internet-Draft / Cao and Arango Gutierrez"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: medium
tags:
  - ai
  - agent-identity
  - authorization
  - draft-standard
status: developing
related:
  - "[[concepts/AgentIdentityDelegation边界]]"
  - "[[concepts/ToolRiskPermissioning边界]]"
---

# Agent Identity Protocol Internet-Draft

**来源**：IETF Internet-Draft
**URL**：https://www.ietf.org/archive/id/draft-aip-agent-identity-protocol-00.html

## 摘要

Agent Identity Protocol draft 定义一个面向 AI agent 的可验证身份和 policy enforcement 协议。它指出 agent 当前常以用户身份或全量 API key 行动，缺少人类与非人类 actor 的可验证身份边界，并提出 identity registry、agent key、signed tool call 和 enforcement proxy 等机制。

## 关键贡献

- 把 agent identity 明确成独立于人类账号的 runtime actor。
- 将 accountable principal、agent public key、signed outbound action 和 policy enforcement 放入同一结构。
- 提醒 multi-agent delegation 会累积权限，需要显式记录授权范围。
- 对本 vault 的意义：它不是稳定标准，但清楚表达了 agent identity 领域正在收敛的工程问题。

## 对 AI 知识体系的归属

- 主归属：5. Agent 系统层
- 交叉链接：7. 产品与组织层、6. 评估与可靠性层

## 关联

- [[concepts/AgentIdentityDelegation边界]]
- [[Research: Agent identity delegation 边界]]
