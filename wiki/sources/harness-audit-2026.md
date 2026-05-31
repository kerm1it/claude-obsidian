---
address: c-000208
type: source
title: "Auditing Agent Harness Safety"
source_url: https://arxiv.org/abs/2605.14271
source_type: paper
author: "Chengzhi Liu et al."
published: 2026-05-14
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - agents
  - audit
  - harness
status: active
related:
  - "[[concepts/AgentHarness与TraceEval]]"
  - "[[concepts/Agent评估体系]]"
---

# Auditing Agent Harness Safety

**来源**：arXiv
**URL**：https://arxiv.org/abs/2605.14271

## 摘要

HarnessAudit 研究 agent harness 的安全审计问题，关注完整执行轨迹中的权限边界、执行忠实度和系统稳定性，而不是只看最终输出。

## 关键贡献

- 正确答案不代表安全执行；很多违规发生在中间轨迹而不是最终状态。
- 多 agent harness 扩大资源访问和信息流风险面。
- Harness design 会设定可安全部署的上限，因此必须审计完整 trajectory。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：5. Agent 系统层
- 作用：为 harness 引入审计和复现维度。

## 关联

- [[concepts/AgentHarness与TraceEval]]
- [[concepts/Agent评估体系]]
- [[Research: Agent harness 与 trace eval]]
