---
address: c-000294
type: source
title: "Mixture-of-Agents Enhances Large Language Model Capabilities"
source_url: https://arxiv.org/abs/2406.04692
source_type: paper
author: "Junlin Wang et al."
published: 2024-06-07
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - multi-agent
  - ensemble
  - mixture-of-agents
status: active
related:
  - "[[concepts/ModelRoutingMixture边界]]"
  - "[[concepts/AgentHarness与TraceEval]]"
---

# Mixture-of-Agents Enhances Large Language Model Capabilities

**来源**：arXiv
**URL**：https://arxiv.org/abs/2406.04692

## 摘要

Mixture-of-Agents 使用多层 LLM agents，让每层 agents 读取上一层输出作为辅助信息，再由后续层继续生成或聚合。它是一种 multi-agent / ensemble 策略，用多个模型的输出提升开放式任务质量。

## 关键贡献

- 将多个 LLM 的能力组合成 layered MoA architecture。
- 每个 agent 使用上一层多个 agents 的输出作为辅助信息。
- 在开放式生成 benchmark 上报告较强表现。
- 对本 vault 的意义：MoA 属于昂贵的 parallel/ensemble 策略，目标偏质量提升，不等同于低成本 model routing。

## 对 AI 知识体系的归属

- 主归属：5. Agent 系统层
- 交叉链接：3. 推理与能力层、6. 评估与可靠性层、7. 产品与组织层
- 作用：提供“mixture”在 agent 层的代表性形态。

## 关联

- [[concepts/ModelRoutingMixture边界]]
- [[concepts/AgentHarness与TraceEval]]
- [[Research: Model routing mixture 边界]]
