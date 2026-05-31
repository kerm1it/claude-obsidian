---
address: c-000245
type: synthesis
title: "Research: Serving 成本 延迟 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - serving
  - inference
  - latency
  - cost
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/Serving成本延迟边界]]"
  - "[[concepts/TestTimeCompute]]"
  - "[[concepts/微调RAG上下文工程选择框架]]"
  - "[[concepts/AgentHarness与TraceEval]]"
sources:
  - "[[sources/openai-latency-optimization-2026]]"
  - "[[sources/openai-cost-optimization-2026]]"
  - "[[sources/anthropic-prompt-caching-2026]]"
  - "[[sources/pagedattention-vllm-2023]]"
  - "[[sources/distserve-2024]]"
  - "[[sources/huggingface-tgi-2026]]"
  - "[[sources/huggingface-continuous-batching-2026]]"
  - "[[sources/nvidia-genai-perf-2026]]"
  - "[[sources/nvidia-tensorrt-llm-2026]]"
---

# Research: Serving 成本 延迟 边界

## Overview

Serving / 成本 / 延迟稳定归入 [[domains/AI知识体系]] 第 3 层“推理与能力层”，并交叉连接第 7 层产品约束。它回答的问题不是“模型能不能做”，而是“模型能力能否以可接受成本、延迟和吞吐进入真实产品”。

稳定链路：`模型能力 → request/context → prefill → decode → streaming/postprocess → SLO/cost/eval → 产品体验`。

## Key Findings

- OpenAI latency guide 把延迟优化拆成 model、token、streaming、parallelization、batching、caching 等策略，说明 latency 是系统设计问题，不只是模型快慢。（Source: [[sources/openai-latency-optimization-2026]]）
- OpenAI cost guide 把成本优化拆成模型选择、token 缩减、batch/flex、prompt caching、fine-tuning/distillation 等路径；成本和延迟必须和质量 eval 一起看。（Source: [[sources/openai-cost-optimization-2026]]）
- Anthropic prompt caching 将长且重复的 prompt 前缀缓存起来，适合长文档、tool definitions、few-shot examples 和 agent instructions，直接连接上下文工程与 serving。（Source: [[sources/anthropic-prompt-caching-2026]]）
- vLLM / PagedAttention 把 KV cache 管理作为 LLM serving 的核心瓶颈，使用 paging 思路减少显存浪费、提升并发和吞吐。（Source: [[sources/pagedattention-vllm-2023]]）
- DistServe 说明 LLM inference 分成 prefill 和 decode 两个阶段，二者资源特征不同；分离部署可以改善 goodput 和 SLO 达成。（Source: [[sources/distserve-2024]]）
- Hugging Face TGI 把 tensor parallelism、token streaming、continuous batching、Flash Attention、Paged Attention、quantization 组合成生产 serving stack。（Source: [[sources/huggingface-tgi-2026]], [[sources/huggingface-continuous-batching-2026]]）
- NVIDIA GenAI-Perf 明确 TTFT、TPOT、inter-token latency、request latency、throughput 等 LLM serving 指标，为第 6 层 eval/monitor 提供度量语言。（Source: [[sources/nvidia-genai-perf-2026]]）
- TensorRT-LLM 展示生产 serving 优化会下沉到 kernel、KV cache、batch scheduler、quantization 和 distributed serving，而不是只靠 prompt。（Source: [[sources/nvidia-tensorrt-llm-2026]]）

## Stable Boundary

| 概念 | 主职责 | 归属 |
|---|---|---|
| Serving | 把模型推理变成满足 SLO 的可用服务 | 3. 推理与能力层 |
| Cost / latency | 产品级 unit economics 和用户体验约束 | 7. 产品与组织层 |
| Monitoring / eval | 衡量质量、成本、延迟、goodput、错误率 | 6. 评估与可靠性层 |
| Distillation / quantization | 改模型或表示以降低 serving 成本 | 2. 模型构建层 |
| Context reduction / prompt caching | 减 token 和重复前缀成本 | 4. 上下文与知识层 |

## 指标优先级

| 场景 | 先看什么 |
|---|---|
| 聊天产品 | TTFT、streaming、P95 latency、cost/request |
| Agent / coding | cost/success、tool loop latency、trace length、failure rerun cost |
| 批处理 | throughput、batch cost、deadline、error retry |
| 实时语音 | first audio latency、jitter、turn-taking latency |
| 高并发 API | goodput、queue time、P99、GPU utilization |

## Open Questions

- Agent trace 成本应按 request、task、workflow 还是 business outcome 计价。
- Prompt caching 与 memory/RAG 的边界如何在长任务中统一管理。
- Hosted API 的 batch/flex/cache 与自托管 vLLM/TGI/TensorRT-LLM 的成本分界点如何估算。

## Filed Result

本轮归档为 [[concepts/Serving成本延迟边界]]，并回填 [[domains/AI知识体系]] 第 3 层与第 7 层连接。结论：serving 不新增顶层；它是推理能力进入产品时的成本、延迟、吞吐和 SLO 约束接口。
