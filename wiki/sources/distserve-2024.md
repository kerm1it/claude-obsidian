---
address: c-000250
type: source
title: "DistServe: Disaggregating Prefill and Decoding for Goodput-optimized Large Language Model Serving"
source_url: https://arxiv.org/abs/2401.09670
source_type: paper
author: "Ying Sheng et al."
published: 2024-01-17
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - serving
  - prefill
  - decode
  - goodput
status: active
related:
  - "[[concepts/Serving成本延迟边界]]"
---

# DistServe

**来源**：arXiv:2401.09670
**URL**：https://arxiv.org/abs/2401.09670

## 摘要

DistServe 研究 LLM serving 中 prefill 和 decode 两个阶段的资源差异。Prefill 处理输入 token，decode 逐步生成输出 token；二者对计算、显存、延迟和吞吐的压力不同。论文提出将 prefill 和 decode 分离部署以优化 goodput。

## 关键贡献

- LLM inference 不是单一阶段，prefill 与 decode 的性能瓶颈不同。
- Goodput 比 raw throughput 更贴近产品：只计算满足 SLO 的有效吞吐。
- 分离 prefill/decode 可以减少干扰，更好满足 TTFT 与 TPOT 约束。
- Agent 长上下文和长输出会放大 prefill/decode tradeoff。

## 对 AI 知识体系的归属

- 主归属：3. 推理与能力层
- 交叉链接：6. 评估与可靠性层、7. 产品与组织层
- 作用：把 serving 指标从“吞吐量”推进到“满足 SLO 的 goodput”。

## 关联

- [[concepts/Serving成本延迟边界]]
- [[Research: Serving 成本 延迟 边界]]
