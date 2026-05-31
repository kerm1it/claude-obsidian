---
address: c-000288
type: synthesis
title: "Research: Model routing mixture 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - model-routing
  - inference
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/ModelRoutingMixture边界]]"
  - "[[concepts/Serving成本延迟边界]]"
  - "[[concepts/ReasoningEvalVerifier边界]]"
  - "[[concepts/ProductOrganizationLayer边界]]"
sources:
  - "[[sources/openai-model-selection-2026]]"
  - "[[sources/routellm-2024]]"
  - "[[sources/routerbench-2024]]"
  - "[[sources/frugalgpt-2023]]"
  - "[[sources/optimizing-model-selection-compound-ai-systems-2025]]"
  - "[[sources/mixture-of-agents-2024]]"
  - "[[sources/switch-transformers-2021]]"
---

# Research: Model routing mixture 边界

## Overview

Model routing / mixture 不是新的顶层。外部模型路由主属第 3 层推理与能力层：它在 inference/runtime 阶段选择模型、effort、cascade、ensemble 或 per-module allocation，并由第 6 层 eval 和第 7 层产品 SLO/成本约束。

## Key Findings

- OpenAI 的 model selection 指南给出基本顺序：先用准确率达到生产门槛，再优化成本和延迟；如果成本或延迟是硬约束，则先设阈值再排除不合格模型（Source: [[sources/openai-model-selection-2026]]）。
- RouteLLM 把 routing 定义为强/弱模型之间的动态选择，用偏好数据训练 router 来平衡质量和成本（Source: [[sources/routellm-2024]]）。
- RouterBench 提供 multi-LLM routing 的评估框架和大量 inference outcome 数据，说明 router 必须被系统性评估，而不是只凭单次 benchmark（Source: [[sources/routerbench-2024]]）。
- FrugalGPT 将 prompt adaptation、LLM approximation、LLM cascade 作为降本策略，说明级联是 routing 的早期稳定形态（Source: [[sources/frugalgpt-2023]]）。
- Compound AI 系统中的模型选择不是单请求选择，而是为 self-refine、multi-agent debate 等模块分配模型；局部模块模型选择会显著影响端到端质量（Source: [[sources/optimizing-model-selection-compound-ai-systems-2025]]）。
- Mixture-of-Agents 用多层 agent 聚合多个 LLM 输出，提高开放式生成质量，但这是昂贵的 parallel/ensemble 策略，不等同于低成本 routing（Source: [[sources/mixture-of-agents-2024]]）。
- Switch Transformer 说明 MoE 是另一类 mixture：模型内部按输入选择专家参数，主属第 2 层模型架构，不应和应用层 model routing 混成一类（Source: [[sources/switch-transformers-2021]]）。

## Stable Definition

外部 model routing 的稳定定义：

```text
request + SLO + risk + model pool + eval history
    -> routing decision
    -> model / effort / cascade / ensemble
    -> quality + cost + latency trace
    -> router eval and update
```

## Classification

| 概念 | 主归属 | 说明 |
|---|---|---|
| model selection | 3. 推理与能力层 | 选择满足准确率、成本、延迟目标的模型 |
| model routing | 3. 推理与能力层 | 运行时按请求动态选择模型或策略 |
| cascade / escalation | 3. 推理与能力层 | cheap-first 或 strong-first 的顺序调用 |
| MoE / Switch Transformer | 2. 模型构建层 | 模型内部 sparse expert routing |
| Mixture-of-Agents | 5. Agent 系统层 | 多 agent / 多 LLM 输出聚合 |
| product policy routing | 7. 产品与组织层 | 用户等级、风险、SLO、预算决定可用策略 |

## Engineering Practice

1. 建真实 eval，先确定质量门槛和最强模型上限。
2. 记录每类请求的质量、成本、延迟、上下文长度、失败类型和人工接管。
3. 对低风险高频任务测试小模型、蒸馏或 cheap-first cascade。
4. 对高风险任务使用强模型、verifier gate 或人工审批。
5. 对复杂 agent/compound systems 分模块评估模型选择，避免端到端质量被局部省钱破坏。
6. 持续监控 router drift、模型版本变化、价格变化和输入分布变化。

## Evaluation

- cost/success、accuracy/cost、latency/quality frontier。
- router regret、oracle gap、escalation rate、fallback rate。
- high-risk false downgrade、weak-model miss rate、verifier calibration。
- drift under model/provider/version changes。
- trace-level attribution：失败来自 router 还是下游模型/工具/上下文。

## Open Questions

- Router 如何和第 8 层 self-improvement 自动闭环，需要防止 eval overfitting 和 reward hacking。
- 多 provider 路由涉及数据出境、隐私、合规和 SLA，属于第 7 层 data rights / governance 的后续问题。
- 内置平台路由越来越强时，应用层 router 的收益会下降，需要用真实 workload 重新证明。
