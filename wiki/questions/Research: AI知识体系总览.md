---
address: c-000170
type: synthesis
title: "Research: AI 知识体系总览"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - knowledge-system
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/AI系统生成链]]"
  - "[[learning/AI体系学习路线]]"
sources:
  - "[[sources/stanford-ai-index-2026]]"
  - "[[sources/attention-is-all-you-need-2017]]"
  - "[[sources/scaling-laws-neural-language-models-2020]]"
  - "[[sources/instructgpt-rlhf-2022]]"
  - "[[sources/rag-2020]]"
  - "[[sources/react-2022]]"
  - "[[sources/distilling-knowledge-neural-network-2015]]"
  - "[[sources/huggingface-peft-docs]]"
  - "[[sources/openai-model-distillation-2024]]"
  - "[[sources/openai-agents-sdk-evolution-2026]]"
  - "[[sources/anthropic-context-engineering-agents-2026-05-26]]"
  - "[[sources/anthropic-demystifying-evals-agents-2026-05-26]]"
  - "[[sources/yc-root-access-self-improving-company-2026-05-22]]"
  - "[[sources/gemini-coleads-origins-2026-05-30]]"
---

# Research: AI 知识体系总览

## Overview

AI 工程知识可以稳定组织为一条系统生成链：基础理论解释能力来源，模型构建把数据和反馈压缩进权重，推理层释放能力，上下文层把任务现场接入模型，Agent 层让模型行动，评估层让行动可靠，产品组织层把可靠能力变成价值，自我改进层把真实运行反馈重新喂回前面各层。

这条链比按“模型微调 / prompt / agent / dream”等词分组更稳定，因为它按系统中信息和控制流的方向组织。

## Key Findings

- Transformer 是当前 LLM 的基础架构支点：它用注意力替代循环和卷积，使序列建模更并行、更可扩展。（Source: [[sources/attention-is-all-you-need-2017]]）
- Scaling Laws 解释了为什么模型大小、数据量和训练计算会形成可预测的性能趋势，是“基础理论层 → 模型构建层”的桥。（Source: [[sources/scaling-laws-neural-language-models-2020]]）
- 指令微调与 RLHF 解决的是“更大不等于更听话”的问题，把基础模型转成面向用户意图的产品能力。（Source: [[sources/instructgpt-rlhf-2022]]）
- 蒸馏是模型构建层的成本压缩机制：把 ensemble 或大模型能力压入更易部署的小模型；在现代 API 平台中，蒸馏已经变成数据收集、fine-tune、eval 的工作流。（Source: [[sources/distilling-knowledge-neural-network-2015]], [[sources/openai-model-distillation-2024]]）
- RAG 和 context engineering 处理的是“任务现场知识如何进入模型”的问题，属于上下文与知识层，而不是模型构建层。（Source: [[sources/rag-2020]], [[sources/anthropic-context-engineering-agents-2026-05-26]]）
- ReAct 把 reasoning trace 和 action 交错起来，是从上下文层进入 Agent 系统层的经典桥梁。（Source: [[sources/react-2022]]）
- Agent 的可靠性不能只看输出，要评估 trace、工具调用、最终环境状态、成本和回归表现。（Source: [[sources/anthropic-demystifying-evals-agents-2026-05-26]]）
- 2026 年 AI Index 显示 AI 能力和社会采用仍在加速，因此学习体系需要稳定结构，而不是依赖某个年度工具清单。（Source: [[sources/stanford-ai-index-2026]]）
- OpenAI Agents SDK 的新方向把 harness、文件/工具操作、沙盒执行组合成标准化基础设施，说明 agent 工程正在从 prompt 技巧走向运行时工程。（Source: [[sources/openai-agents-sdk-evolution-2026]]）

## 初始来源组

| 来源 | 贡献 |
|---|---|
| [[sources/attention-is-all-you-need-2017]] | 基础架构：Transformer |
| [[sources/scaling-laws-neural-language-models-2020]] | 基础理论：规模律 |
| [[sources/instructgpt-rlhf-2022]] | 模型构建：指令微调与 RLHF |
| [[sources/distilling-knowledge-neural-network-2015]] | 模型构建：蒸馏 |
| [[sources/huggingface-peft-docs]] | 模型构建：参数高效微调 |
| [[sources/rag-2020]] | 上下文知识：外部记忆 |
| [[sources/react-2022]] | Agent 系统：reasoning + acting |
| [[sources/openai-agents-sdk-evolution-2026]] | Agent 系统：harness 与沙盒运行时 |
| [[sources/anthropic-context-engineering-agents-2026-05-26]] | 上下文工程：长期任务上下文管理 |
| [[sources/anthropic-demystifying-evals-agents-2026-05-26]] | 评估可靠性：agent eval |
| [[sources/yc-root-access-self-improving-company-2026-05-22]] | 自我改进：组织闭环 |
| [[sources/gemini-coleads-origins-2026-05-30]] | 模型产品化：单模型、蒸馏、自我学习 |

## 为什么八层稳定

八层不是按流行词分组，而是按“信息被处理的位置”分组：

1. 理论决定什么可训练。
2. 训练把数据和反馈写入权重。
3. 推理把权重转化为能力表现。
4. 上下文把任务现场接到能力上。
5. Agent 把能力转化为行动。
6. Eval 判断行动是否可靠。
7. 产品组织决定可靠能力如何创造价值。
8. 自我改进把运行反馈变成下一轮数据、上下文、工具和 eval。

因此，新知识一般只是在某层内部更细，或在两层之间起桥接作用；它很少真正需要新增顶层。

## Open Questions

- 微调、RAG、长上下文、memory 的边界会随模型窗口和成本变化而移动，需要单独深挖。
- Dream / self-improvement 中哪些已经是工程实践，哪些仍是愿景，需要继续分辨。
- 多模态和世界模型是否仍归入推理与能力层，还是未来需要二级分类，需要等更多稳定工程模式出现。
- Agent harness 的标准接口尚未统一，OpenAI、Anthropic MCP、LangChain/LangGraph、DSPy 等路线需要后续比较。

## Next Topics

1. 微调 vs RAG vs context engineering。
2. Agent harness 与 trace。
3. Eval 驱动开发在 agent 系统中的最小闭环。
4. Dream / self-improvement 的真实工程原语。
