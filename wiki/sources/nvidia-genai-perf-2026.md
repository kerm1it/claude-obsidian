---
address: c-000253
type: source
title: "GenAI-Perf"
source_url: https://docs.nvidia.com/deeplearning/triton-inference-server/user-guide/docs/perf_analyzer/genai-perf/README.html
source_type: documentation
author: "NVIDIA"
published: 2026-05-30
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - serving
  - benchmark
  - latency
  - nvidia
status: active
related:
  - "[[concepts/Serving成本延迟边界]]"
---

# GenAI-Perf

**来源**：NVIDIA Documentation
**URL**：https://docs.nvidia.com/deeplearning/triton-inference-server/user-guide/docs/perf_analyzer/genai-perf/README.html

## 摘要

GenAI-Perf 是 NVIDIA 面向 generative AI 的性能测量工具。它把 LLM serving 指标拆成 time to first token、time per output token、inter token latency、request latency、throughput 等。

## 关键贡献

- LLM serving 指标需要 token-aware，而不是只看普通 HTTP latency。
- TTFT 衡量用户第一次看到输出的等待时间。
- TPOT / inter-token latency 衡量生成过程体验。
- Throughput 必须和 latency percentiles 一起看，避免只优化总吞吐而破坏用户体验。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：3. 推理与能力层、7. 产品与组织层
- 作用：提供 serving eval / monitoring 的指标语言。

## 关联

- [[concepts/Serving成本延迟边界]]
- [[Research: Serving 成本 延迟 边界]]
