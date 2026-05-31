---
address: c-000185
type: source
title: "Microsoft Foundry fine-tuning considerations"
source_url: https://learn.microsoft.com/en-us/azure/foundry/openai/concepts/fine-tuning-considerations
source_type: documentation
author: "Microsoft Learn"
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - fine-tuning
  - dpo
  - rft
status: active
related:
  - "[[concepts/微调RAG上下文工程选择框架]]"
---

# Microsoft Foundry fine-tuning considerations

**来源**：Microsoft Learn
**URL**：https://learn.microsoft.com/en-us/azure/foundry/openai/concepts/fine-tuning-considerations

## 摘要

该文档说明 fine-tuning 的适用场景、收益和局限。核心观点：fine-tuning 适合有小而高质量任务数据集时提升特定任务表现，并可降低 prompt 开销、稳定格式/语气、增强工具使用和检索结合能力。

## 关键贡献

- 适用数据规模：数百到数千条高质量任务示例。
- 典型用途：减少 prompt engineering 开销、修改风格语气、生成固定 schema、增强工具使用、提升 RAG 场景中使用外部知识的能力。
- 微调类型：SFT、RFT、DPO；SFT 适合有限解法的任务，RFT 适合有可度量奖励的复杂任务，DPO 适合偏好对齐。
- Distillation 被归为 fine-tuning 的一种效率路径：用强模型输出训练更小模型以降低成本和延迟。

## 对 AI 知识体系的归属

- 主归属：2. 模型构建层
- 交叉链接：4. 上下文与知识层、6. 评估与可靠性层、7. 产品与组织层

## 关联

- [[concepts/微调RAG上下文工程选择框架]]
- [[sources/huggingface-peft-docs]]
- [[sources/openai-model-distillation-2024]]
