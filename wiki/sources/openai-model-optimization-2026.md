---
address: c-000186
type: source
title: "Model optimization"
source_url: https://developers.openai.com/api/docs/guides/model-optimization
source_type: documentation
author: "OpenAI"
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - evals
  - prompt-engineering
  - fine-tuning
status: active
related:
  - "[[concepts/微调RAG上下文工程选择框架]]"
  - "[[concepts/Eval驱动开发]]"
  - "[[concepts/ProductOrganizationLayer边界]]"
  - "[[concepts/DataFlywheelFeedbackLoop边界]]"
  - "[[concepts/ProductFeedbackClosureActionability边界]]"
---

# Model optimization

**来源**：OpenAI Docs
**URL**：https://developers.openai.com/api/docs/guides/model-optimization

## 摘要

OpenAI 的模型优化指南将 eval、prompt engineering、fine-tuning 组合成一个反馈飞轮：先建立 eval 基线，再迭代 prompt、训练数据和模型结果。

## 关键贡献

- LLM 输出非确定，模型快照和模型家族变化会改变行为，因此需要持续测量和调优。
- 优化流程从 eval 开始：写 eval、提示模型、必要时 fine-tune、在代表真实输入的测试数据上评估、根据反馈调整，再重复。
- 对本 vault 的结论：微调/RAG/上下文工程的选择必须以 eval 为门，而不是凭直觉。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：4. 上下文与知识层、2. 模型构建层
- 产品组织接口：第 7 层 telemetry 和用户反馈需要回填到这个 eval/prompt/fine-tuning 飞轮，而不是直接无门槛进入训练。
- 数据飞轮接口：真实使用反馈先分流为 eval、prompt/context、RAG/memory、skill/tool 或 fine-tuning 候选。
- 反馈闭环接口：分流后的反馈还要有 owner、artifact、验证和关闭证据，才能算进入 model optimization flywheel。

## 关联

- [[concepts/Eval驱动开发]]
- [[concepts/微调RAG上下文工程选择框架]]
- [[concepts/ProductOrganizationLayer边界]]
- [[concepts/DataFlywheelFeedbackLoop边界]]
- [[concepts/ProductFeedbackClosureActionability边界]]
