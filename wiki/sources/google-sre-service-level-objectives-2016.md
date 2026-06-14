---
address: c-000420
type: source
title: "Service Level Objectives"
source_url: https://sre.google/sre-book/service-level-objectives/
source_type: book-chapter
author: "Google SRE"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - sre
  - slo
  - reliability
status: active
related:
  - "[[concepts/EvalResultInterpretationDecisionThreshold边界]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
---

# Service Level Objectives

**来源**：Google SRE Book
**URL**：https://sre.google/sre-book/service-level-objectives/

## 摘要

Google SRE 的 SLO 章节区分 SLI、SLO 和 SLA，并说明 SLO violation rate 与 error budget 可以进入发布决策。它把可靠性从主观期望转成可测量、可协商的工程目标。

## 关键贡献

- SLI 是实际测量，SLO 是目标阈值，SLA 是带后果的协议。
- 明确 SLO 有助于管理用户和团队对服务可靠性的预期。
- 对本 vault 的意义：AI eval threshold 可以借鉴 SLO 思路，把质量、安全、延迟、成本和任务成功率转成可执行控制面。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[concepts/EvalResultInterpretationDecisionThreshold边界]]
- [[concepts/ModelReleaseRollbackGate边界]]
