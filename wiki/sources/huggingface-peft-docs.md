---
address: c-000179
type: source
title: "PEFT — Hugging Face Documentation"
source_url: https://huggingface.co/docs/peft/v0.6.0/index
source_type: documentation
author: "Hugging Face"
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - fine-tuning
  - peft
  - lora
status: active
related:
  - "[[domains/AI知识体系]]"
---

# PEFT — Hugging Face Documentation

**来源**：Hugging Face PEFT 文档
**URL**：https://huggingface.co/docs/peft/v0.6.0/index

## 摘要

PEFT（Parameter-Efficient Fine-Tuning）是一组参数高效微调方法。它只训练少量额外参数或适配器，从而降低大模型微调的计算和存储成本。

## 关键贡献

- PEFT 说明“微调”不必总是全量更新模型参数。
- LoRA、Prefix Tuning、Prompt Tuning、AdaLoRA 等方法都属于“在模型构建层做低成本适配”的路线。
- 它是“什么时候改权重、什么时候只改上下文”的关键对照点。

## 对 AI 知识体系的归属

- 主归属：2. 模型构建层
- 交叉链接：4. 上下文与知识层、7. 产品与组织层
- 后续研究：微调 vs RAG vs prompt/context engineering。

## 关联

- [[domains/AI知识体系]]
- [[learning/AI体系学习路线]]
