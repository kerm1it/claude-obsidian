---
address: c-000280
type: source
title: "EmbodiedBench: Comprehensive Benchmarking Multi-modal Large Language Models for Vision-Driven Embodied Agents"
source_url: https://arxiv.org/abs/2502.09560
source_type: paper
author: "Rui Yang et al."
published: 2025-02-13
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - embodied-agents
  - multimodal
  - benchmark
status: active
related:
  - "[[concepts/MultimodalEvalSimulationEval边界]]"
---

# EmbodiedBench

**来源**：arXiv / ICML 2025
**URL**：https://arxiv.org/abs/2502.09560

## 摘要

EmbodiedBench 是面向 vision-driven embodied agents 的多模态大模型 benchmark。它包含 1,128 个测试任务，覆盖四个环境，从高层语义任务到导航和操作等低层动作任务。

## 关键贡献

- 评估 MLLM 作为 embodied agent 的能力，而不只是静态图像/视频理解。
- 六个能力子集包括 commonsense reasoning、complex instruction understanding、spatial awareness、visual perception 和 long-term planning。
- 评估 24 个 proprietary 和 open-source MLLM，显示模型在高层任务更强，但低层 manipulation 仍弱。
- 提供从多模态理解到闭环行动评估的桥梁。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：5. Agent 系统层、3. 推理与能力层
- 作用：为 embodied agent 提供任务级和能力级 eval 结构。

## 关联

- [[concepts/MultimodalEvalSimulationEval边界]]
- [[Research: Multimodal eval simulation eval 边界]]
