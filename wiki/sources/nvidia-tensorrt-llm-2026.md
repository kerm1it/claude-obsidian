---
address: c-000254
type: source
title: "TensorRT-LLM"
source_url: https://docs.nvidia.com/tensorrt-llm/
source_type: documentation
author: "NVIDIA"
published: 2026-05-30
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - serving
  - tensorrt-llm
  - nvidia
  - optimization
status: active
related:
  - "[[concepts/Serving成本延迟边界]]"
---

# TensorRT-LLM

**来源**：NVIDIA Documentation
**URL**：https://docs.nvidia.com/tensorrt-llm/

## 摘要

TensorRT-LLM 是 NVIDIA 面向 LLM inference 的优化和部署框架，覆盖 model definition、optimization、runtime execution、distributed serving、quantization、KV cache 和 batching 等能力。

## 关键贡献

- 生产 serving 优化会下沉到 kernel、runtime、cache、batch scheduler 和分布式执行。
- Quantization、speculative decoding、KV cache reuse、in-flight batching 等是常见性能旋钮。
- 自托管 serving 的成本优势必须和系统复杂度、运维能力、硬件利用率一起评估。

## 对 AI 知识体系的归属

- 主归属：3. 推理与能力层
- 交叉链接：2. 模型构建层、7. 产品与组织层
- 作用：提供高性能 LLM serving 的系统层参考。

## 关联

- [[concepts/Serving成本延迟边界]]
- [[Research: Serving 成本 延迟 边界]]
