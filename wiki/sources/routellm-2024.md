---
address: c-000290
type: source
title: "RouteLLM: Learning to Route LLMs with Preference Data"
source_url: https://arxiv.org/abs/2406.18665
source_type: paper
author: "Isaac Ong et al."
published: 2024-06-26
updated_source: 2025-02-23
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - model-routing
  - llm-routing
  - cost-quality
status: active
related:
  - "[[concepts/ModelRoutingMixture边界]]"
  - "[[concepts/Serving成本延迟边界]]"
---

# RouteLLM: Learning to Route LLMs with Preference Data

**来源**：arXiv
**URL**：https://arxiv.org/abs/2406.18665
**提交**：2024-06-26，v4 修订：2025-02-23

## 摘要

RouteLLM 研究在强模型和弱模型之间动态选择的 router。目标是在推理时根据请求选择足够强但成本更低的模型，以优化 response quality 与 cost 的平衡。

## 关键贡献

- 明确 LLM routing 的核心 trade-off：强模型质量高但贵，弱模型便宜但能力不足。
- 使用 human preference data 和 data augmentation 训练 router。
- 报告在若干 benchmark 上能显著降低成本，同时维持响应质量。
- 观察到 router 对更换 strong/weak 模型存在一定 transfer 能力，说明 routing policy 不完全绑定单一模型对。

## 对 AI 知识体系的归属

- 主归属：3. 推理与能力层
- 交叉链接：6. 评估与可靠性层、7. 产品与组织层
- 作用：提供 learned runtime router 的代表性研究。

## 关联

- [[concepts/ModelRoutingMixture边界]]
- [[Research: Model routing mixture 边界]]
