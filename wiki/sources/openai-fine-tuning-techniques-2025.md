---
address: c-000188
type: source
title: "Fine-Tuning Techniques - Choosing Between SFT, DPO, and RFT"
source_url: https://developers.openai.com/cookbook/examples/fine_tuning_direct_preference_optimization_guide
source_type: cookbook
author: "OpenAI"
published: 2025-06-18
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - fine-tuning
  - sft
  - dpo
  - rft
status: active
related:
  - "[[concepts/微调RAG上下文工程选择框架]]"
---

# Fine-Tuning Techniques - Choosing Between SFT, DPO, and RFT

**来源**：OpenAI Cookbook
**URL**：https://developers.openai.com/cookbook/examples/fine_tuning_direct_preference_optimization_guide
**发布时间**：2025-06-18

## 摘要

该指南比较 SFT、DPO、RFT 的适用场景。它明确指出 fine-tuning 通常用于提升特定任务表现或效率，不适合直接添加全新知识；新知识更适合 RAG。

## 关键贡献

- SFT：适合响应结构、语气、复杂指令、格式和成本/延迟优化；不适合添加全新知识。
- DPO：适合主观偏好、语气、风格、礼貌程度等偏好对齐。
- RFT：适合有可度量奖励的复杂推理或决策任务。
- OpenAI 推荐常见流程：先 SFT 建立初始策略，再用 DPO 细化偏好。

## 对 AI 知识体系的归属

- 主归属：2. 模型构建层
- 交叉链接：6. 评估与可靠性层、7. 产品与组织层

## 关联

- [[concepts/微调RAG上下文工程选择框架]]
- [[sources/instructgpt-rlhf-2022]]
