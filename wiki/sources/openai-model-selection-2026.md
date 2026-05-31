---
address: c-000289
type: source
title: "Model selection"
source_url: https://developers.openai.com/api/docs/guides/model-selection
source_type: documentation
author: "OpenAI"
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - model-selection
  - cost
  - latency
status: active
related:
  - "[[concepts/ModelRoutingMixture边界]]"
  - "[[concepts/Serving成本延迟边界]]"
  - "[[concepts/ProductOrganizationLayer边界]]"
---

# Model selection

**来源**：OpenAI Docs
**URL**：https://developers.openai.com/api/docs/guides/model-selection

## 摘要

OpenAI 的 model selection 指南把模型选择定义为 performance 与 cost 的平衡问题。核心顺序是先优化 accuracy，直到达到生产目标，再在保持 accuracy 的前提下优化成本和延迟。

## 关键贡献

- 模型选择必须有明确 accuracy target 和 evaluation dataset。
- 实践上先用最强模型达到质量目标，并记录 prompt/completion 对，作为 few-shot、eval 或 fine-tuning 数据。
- 达到质量目标后，再比较小模型、减少请求、减少 token 或 distillation。
- 如果用例对成本或延迟极敏感，应先设阈值，再排除不符合约束的模型。
- 示例展示了用强模型/few-shot 达到准确率后，通过小模型 fine-tuning 达到相似准确率和显著低成本。

## 对 AI 知识体系的归属

- 主归属：3. 推理与能力层
- 交叉链接：6. 评估与可靠性层、7. 产品与组织层、2. 模型构建层
- 对 routing 的启发：先建质量上限和 eval，再讨论降本、路由、蒸馏和产品 SLO。

## 关联

- [[concepts/ModelRoutingMixture边界]]
- [[concepts/Serving成本延迟边界]]
- [[Research: Model routing mixture 边界]]
