---
address: c-000252
type: source
title: "Continuous batching"
source_url: https://huggingface.co/docs/text-generation-inference/conceptual/continuous_batching
source_type: documentation
author: "Hugging Face"
published: 2026-05-30
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - serving
  - batching
  - throughput
status: active
related:
  - "[[concepts/Serving成本延迟边界]]"
---

# Continuous batching

**来源**：Hugging Face TGI Documentation
**URL**：https://huggingface.co/docs/text-generation-inference/conceptual/continuous_batching

## 摘要

Continuous batching 让 serving 系统在生成过程中动态加入和移除请求，避免传统静态 batch 被最长请求拖慢。它是 LLM serving 提升吞吐和 GPU 利用率的关键机制之一。

## 关键贡献

- LLM 生成长度差异大，静态 batching 容易浪费计算。
- Continuous batching 可以在 decode 过程中持续填充 batch。
- 吞吐提升通常伴随调度复杂度，需要和 latency SLO 一起调参。
- 它解释了为什么 serving 优化要按 token 流而不是按 request 黑箱看。

## 对 AI 知识体系的归属

- 主归属：3. 推理与能力层
- 交叉链接：7. 产品与组织层
- 作用：提供 batching / throughput 的稳定工程原语。

## 关联

- [[concepts/Serving成本延迟边界]]
- [[Research: Serving 成本 延迟 边界]]
