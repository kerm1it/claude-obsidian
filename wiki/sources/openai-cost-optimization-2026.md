---
address: c-000247
type: source
title: "Cost optimization"
source_url: https://platform.openai.com/docs/guides/cost-optimization
source_type: documentation
author: "OpenAI"
published: 2026-05-30
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - cost
  - serving
  - openai
status: active
related:
  - "[[concepts/Serving成本延迟边界]]"
  - "[[concepts/微调RAG上下文工程选择框架]]"
---

# Cost optimization

**来源**：OpenAI Platform Docs
**URL**：https://platform.openai.com/docs/guides/cost-optimization

## 摘要

OpenAI cost optimization guide 将成本优化拆成模型选择、token 数、prompt caching、batch/flex processing、fine-tuning、distillation 等路径。它把 cost、latency、quality 作为需要同时优化的产品约束。

## 关键贡献

- 模型选择是最大成本旋钮之一：不要用最强模型处理所有请求。
- Token 缩减直接降低成本，也常降低延迟。
- Prompt caching 对重复上下文场景有效。
- Fine-tuning / distillation 可以把反复出现的行为压进更小或更便宜的模型。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：2. 模型构建层、3. 推理与能力层、4. 上下文与知识层
- 作用：提供 cost optimization 如何横跨模型、上下文和 serving 的官方框架。

## 关联

- [[concepts/Serving成本延迟边界]]
- [[Research: Serving 成本 延迟 边界]]
