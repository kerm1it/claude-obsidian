---
address: c-000249
type: source
title: "Efficient Memory Management for Large Language Model Serving with PagedAttention"
source_url: https://arxiv.org/abs/2309.06180
source_type: paper
author: "Woosuk Kwon et al."
published: 2023-09-12
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - serving
  - vllm
  - kv-cache
status: active
related:
  - "[[concepts/Serving成本延迟边界]]"
---

# Efficient Memory Management for Large Language Model Serving with PagedAttention

**来源**：arXiv:2309.06180
**URL**：https://arxiv.org/abs/2309.06180

## 摘要

PagedAttention / vLLM 论文指出 LLM serving 的关键瓶颈之一是 KV cache 显存管理。PagedAttention 借鉴操作系统虚拟内存分页思想，把 KV cache 划分成 blocks，以减少碎片和浪费，提高并发与吞吐。

## 关键贡献

- KV cache 会占据大量显存，并直接限制并发。
- 传统连续分配会造成显存浪费和碎片。
- Paging 思路让 LLM serving 可以更高效管理多请求、多序列、多样本。
- vLLM 把系统层 serving 优化变成开源标准组件之一。

## 对 AI 知识体系的归属

- 主归属：3. 推理与能力层
- 交叉链接：7. 产品与组织层
- 作用：提供 KV cache / memory management 是 serving 核心约束的证据。

## 关联

- [[concepts/Serving成本延迟边界]]
- [[Research: Serving 成本 延迟 边界]]
