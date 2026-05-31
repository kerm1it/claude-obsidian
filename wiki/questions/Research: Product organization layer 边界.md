---
address: c-000282
type: synthesis
title: "Research: Product organization layer 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - product
  - org-design
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/ProductOrganizationLayer边界]]"
  - "[[concepts/模型即产品]]"
  - "[[concepts/软件工厂]]"
  - "[[concepts/公司大脑]]"
  - "[[concepts/数据飞轮复利]]"
  - "[[concepts/工作流锁定]]"
sources:
  - "[[sources/anthropic-building-effective-agents-2024]]"
  - "[[sources/openai-practical-guide-building-agents-2025]]"
  - "[[sources/openai-agents-sdk-docs-2026]]"
  - "[[sources/openai-model-optimization-2026]]"
  - "[[sources/founders-playbook-2026-05-16]]"
  - "[[sources/yc-diana-ai-company-ground-up-2026-05-22]]"
  - "[[sources/yc-root-access-self-improving-company-2026-05-22]]"
  - "[[sources/bvp-vertical-ai-playbook-2026]]"
---

# Research: Product organization layer 边界

## Overview

Product / organization layer 是 AI 系统生成链的第 7 层：它接收第 6 层验证过的可靠能力，把能力嵌入产品表面、业务工作流、组织角色、单位经济和反馈数据中。它的稳定边界不是“商业”，而是“能力进入真实组织后的系统接口”。

## Key Findings

- Anthropic 的 agent 工程经验强调 workflows 与 agents 的区别：明确路径的任务适合 workflow，开放式任务才需要更自治的 agent；这说明产品化时应先选择稳定工作流，而不是直接堆多 agent（Source: [[sources/anthropic-building-effective-agents-2024]]）。
- OpenAI 的 agent 指南把 agents 定义为端到端工作流自动化系统，并强调先小范围验证、逐步扩展、用 guardrails 和人工接管处理高风险动作（Source: [[sources/openai-practical-guide-building-agents-2025]]）。
- OpenAI Agents SDK 文档将 code-first agent app 的责任归给应用服务器：orchestration、tool execution、state、approvals 和 observability；这把第 5 层 harness 直接接到第 7 层产品基础设施（Source: [[sources/openai-agents-sdk-docs-2026]]）。
- OpenAI model optimization 文档把 eval、prompt 和 fine-tuning 组织成持续反馈飞轮；第 7 层 telemetry 必须能回填第 6 层 eval 和第 2/4 层改进（Source: [[sources/openai-model-optimization-2026]]）。
- Anthropic Founder Playbook、YC Diana 和 YC Root Access 都指向同一个产品组织模式：AI 原生公司把知识、数据、workflow、skills、质量门和学习机制组织成闭环，而不是只给员工加聊天工具（Source: [[sources/founders-playbook-2026-05-16]]、[[sources/yc-diana-ai-company-ground-up-2026-05-22]]、[[sources/yc-root-access-self-improving-company-2026-05-22]]）。
- BVP 的 Vertical AI 备忘录提供产品筛选标准：从客户想自动化且有明确 ROI 的工作流开始，避免高风险、未编码判断密集、无明显价值的流程（Source: [[sources/bvp-vertical-ai-playbook-2026]]）。

## Stable Definition

第 7 层回答：**如何把可靠 AI 能力变成可重复的用户价值和组织流程？**

它消费：
- 第 3 层的推理、serving、成本、延迟能力。
- 第 4 层的上下文、RAG、memory、skills。
- 第 5 层的 agent loop、tools、harness。
- 第 6 层的 eval、guardrail、monitoring、trace。

它产出：
- 产品表面、工作流集成、人类审批边界。
- telemetry、用户反馈、失败案例、数据飞轮。
- 下一轮 model/context/tool/eval/self-improvement 需求。

## Engineering Pattern

```text
workflow pain
    -> define user outcome and eval baseline
    -> choose model/context/tool/harness
    -> ship narrow product surface
    -> instrument success/failure/cost/latency
    -> gate risky actions with human approval
    -> convert repeated patterns into skill/workflow/eval/data
    -> feed improvements back into layers 2/4/5/6/8
```

## Distinctions

| 相邻概念 | 区别 |
|---|---|
| Agent harness | harness 运行 agent；第 7 层决定这个 agent 是否进入产品和组织流程 |
| Eval | eval 衡量可靠性；第 7 层衡量采用、ROI、workflow fit 和单位经济 |
| Data flywheel | 数据飞轮是第 7 层组件，不是完整层级；它必须被权限、隐私和 eval gate 约束 |
| Self-improvement | 第 7 层产生真实反馈；第 8 层负责把反馈变成可审查改动 |

## Evaluation

- 任务完成率、时间节省、人工接管率、失败恢复率。
- 激活、留存、日常工作流渗透率、重复使用频率。
- cost/success、P95/P99 latency、支持成本、gross margin。
- 高风险动作审批率、错误影响、回滚成功率。
- 反馈是否可追踪到 prompt、RAG、memory、tool、model 或 workflow 改动。

## Open Questions

- Data flywheel 需要单独深挖：哪些信号适合进入训练数据，哪些只适合进入 eval 或 memory。
- Model routing / mixture 需要单独深挖：第 7 层单位经济如何反向约束第 3 层模型选择。
- Reward hacking / eval overfitting 需要单独深挖：当产品团队优化指标时，如何防止质量门被指标污染。

## Sources

- [[sources/anthropic-building-effective-agents-2024]]
- [[sources/openai-practical-guide-building-agents-2025]]
- [[sources/openai-agents-sdk-docs-2026]]
- [[sources/openai-model-optimization-2026]]
- [[sources/founders-playbook-2026-05-16]]
- [[sources/yc-diana-ai-company-ground-up-2026-05-22]]
- [[sources/yc-root-access-self-improving-company-2026-05-22]]
- [[sources/bvp-vertical-ai-playbook-2026]]
