---
address: c-000183
type: synthesis
title: "Research: 微调 vs RAG vs 上下文工程"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - fine-tuning
  - rag
  - context-engineering
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/微调RAG上下文工程选择框架]]"
  - "[[concepts/上下文工程]]"
  - "[[concepts/渐进式上下文注入]]"
sources:
  - "[[sources/microsoft-customizing-llms-2026]]"
  - "[[sources/microsoft-fine-tuning-considerations-2026]]"
  - "[[sources/openai-model-optimization-2026]]"
  - "[[sources/openai-optimizing-llm-accuracy-2026]]"
  - "[[sources/openai-fine-tuning-techniques-2025]]"
  - "[[sources/google-cloud-rag-overview]]"
  - "[[sources/rag-2020]]"
  - "[[sources/huggingface-peft-docs]]"
---

# Research: 微调 vs RAG vs 上下文工程

## Overview

微调、RAG、上下文工程不是三选一，而是一组递进工具。上下文工程解决“当下给模型什么信息和约束”；RAG 解决“外部知识如何进入上下文”；微调解决“模型行为、格式、工具使用、成本和延迟如何稳定化”。

这轮研究把它们放回 [[domains/AI知识体系]]：RAG 和上下文工程主归属第 4 层，微调主归属第 2 层；三者都必须被第 6 层 eval 约束，并服务第 7 层产品部署。

## Key Findings

- Microsoft 明确把 prompt engineering、RAG、fine-tuning 定义为互补方法，而不是互斥选项。（Source: [[sources/microsoft-customizing-llms-2026]]）
- RAG 适合私有、庞大、频繁变化或需要出处的知识；它把外部数据注入 prompt，让回答更贴近组织知识库和最新信息。（Source: [[sources/microsoft-customizing-llms-2026]], [[sources/google-cloud-rag-overview]]）
- Fine-tuning 适合已有高质量示例、需要稳定格式/语气/工具使用/任务表现，或想降低 prompt token、成本和延迟的场景。（Source: [[sources/microsoft-fine-tuning-considerations-2026]]）
- OpenAI 的优化工作流从 eval 开始，再迭代 prompt、fine-tuning data 和模型输出；没有 eval，优化会退化成感觉驱动。（Source: [[sources/openai-model-optimization-2026]]）
- OpenAI 建议 fine-tuning 前先有 prompt-engineering 基线；训练数据质量比数量重要，错误来自 context 缺失时不应优先微调。（Source: [[sources/openai-optimizing-llm-accuracy-2026]]）
- OpenAI fine-tuning cookbook 将 SFT 标为适合结构、语气、复杂指令和成本/延迟优化；不适合“加入全新知识”，此时应考虑 RAG。（Source: [[sources/openai-fine-tuning-techniques-2025]]）
- RAG 的瓶颈不是“有没有向量库”，而是检索质量；Google Cloud 强调错误检索会导致 grounded 但错误的生成。（Source: [[sources/google-cloud-rag-overview]]）
- RAG 和微调可以组合：RAG 提供外部知识，微调训练模型更好地使用检索内容、拒答无答案场景或保持输出格式。（Source: [[sources/openai-fine-tuned-rag-qdrant-2023]], [[sources/microsoft-fine-tuning-considerations-2026]]）

## 选择框架

| 问题                | 优先方案            | 判断依据                |
| ----------------- | --------------- | ------------------- |
| 指令、格式、约束没说清       | 上下文工程           | 先降低不确定性             |
| 缺最新/私有/大量知识       | RAG             | 知识应留在外部，可更新、可追溯     |
| 输出行为长期不稳定         | 微调              | 行为模式需要写入权重或 adapter |
| 工具调用不稳            | 微调 + trace eval | 工具选择是可学习行为，但必须验证    |
| 检索内容质量差           | 改 RAG pipeline  | 微调不能补救错误输入          |
| 检索对了但模型不会用        | RAG + 微调        | 训练模型使用上下文           |
| prompt 过长导致成本/延迟高 | 微调或蒸馏           | 把重复模式压进模型           |

## Open Questions

- 长上下文窗口继续变大后，哪些 RAG 需求会转为 context engineering，哪些仍需要 retrieval/reranking。
- RAG+fine-tuning 在 agent tool-use 场景下的最佳 eval 组合：最终答案、trace、retrieval hit、tool-call precision 是否需要统一评分。
- 开源模型 PEFT/LoRA 与托管模型 fine-tuning 的成本边界，需要按具体硬件和部署约束另开研究。

## Filed Result

本轮归档为 [[concepts/微调RAG上下文工程选择框架]]，并回填 [[domains/AI知识体系]] 第 2、4、6、7 层之间的连接。
