---
address: c-000246
type: source
title: "Latency optimization"
source_url: https://platform.openai.com/docs/guides/latency-optimization
source_type: documentation
author: "OpenAI"
published: 2026-05-30
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - latency
  - serving
  - openai
status: active
related:
  - "[[concepts/Serving成本延迟边界]]"
---

# Latency optimization

**来源**：OpenAI Platform Docs
**URL**：https://platform.openai.com/docs/guides/latency-optimization

## 摘要

OpenAI latency optimization guide 将延迟拆成模型选择、输出 token 数、输入 token 数、streaming、parallelization、batching、caching 等策略。文档强调 latency optimization 需要在 quality、cost 和 product UX 之间权衡。

## 关键贡献

- 延迟不只是模型速度，而是请求路径和 token 预算的结果。
- Streaming 降低感知延迟，但不一定降低总完成时间。
- 缩短输出通常是最直接的延迟优化之一。
- Prompt caching、batching、parallelization 属于系统层优化。

## 对 AI 知识体系的归属

- 主归属：3. 推理与能力层
- 交叉链接：7. 产品与组织层、6. 评估与可靠性层
- 作用：提供 serving latency 的产品化优化框架。

## 关联

- [[concepts/Serving成本延迟边界]]
- [[Research: Serving 成本 延迟 边界]]
