---
address: c-000251
type: source
title: "Text Generation Inference"
source_url: https://huggingface.co/docs/text-generation-inference/index
source_type: documentation
author: "Hugging Face"
published: 2026-05-30
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - serving
  - tgi
  - huggingface
status: active
related:
  - "[[concepts/Serving成本延迟边界]]"
---

# Text Generation Inference

**来源**：Hugging Face Documentation
**URL**：https://huggingface.co/docs/text-generation-inference/index

## 摘要

Text Generation Inference 是 Hugging Face 的生产 LLM serving stack，支持多模型架构、tensor parallelism、token streaming、continuous batching、Flash Attention、Paged Attention、quantization、LoRA 等功能。

## 关键贡献

- Serving 是一组系统能力，不只是模型加载。
- Streaming、batching、quantization、parallelism 和 attention kernel 都是生产部署旋钮。
- OpenAI-compatible Messages API 说明 serving stack 常需要兼容产品接口。
- TGI 把开源模型部署连接到产品 API 形态。

## 对 AI 知识体系的归属

- 主归属：3. 推理与能力层
- 交叉链接：7. 产品与组织层
- 作用：提供开源 LLM serving stack 的工程参照。

## 关联

- [[concepts/Serving成本延迟边界]]
- [[Research: Serving 成本 延迟 边界]]
