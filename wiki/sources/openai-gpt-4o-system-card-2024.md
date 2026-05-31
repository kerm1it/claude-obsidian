---
address: c-000276
type: source
title: "GPT-4o System Card"
source_url: https://openai.com/index/gpt-4o-system-card/
source_type: system-card
author: "OpenAI"
published: 2024-08-08
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - multimodal
  - safety
  - evals
status: active
related:
  - "[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]"
  - "[[concepts/MultimodalEvalSimulationEval边界]]"
  - "[[concepts/多模态与世界模型边界]]"
sources:
  - "https://cdn.openai.com/gpt-4o-system-card.pdf"
---

# GPT-4o System Card

**来源**：OpenAI
**URL**：https://openai.com/index/gpt-4o-system-card/

## 摘要

GPT-4o system card 记录 OpenAI 对端到端文本、视觉、音频模型的能力、限制、安全评估和缓解措施。它特别强调语音模态带来的新风险。

## 关键贡献

- 把 text、vision、audio 的评估放到同一发布安全框架内。
- 重点评估 unauthorized voice generation、speaker identification、sensitive trait inference 和 disallowed audio content。
- 使用 Preparedness Framework 和外部红队作为发布质量门。
- 说明多模态产品评估必须覆盖安全、身份、隐私、实时互动和模态滥用。
- 对本 vault 的意义：system card 是 release/eval card 的系统级样例，展示能力、限制、风险评估和缓解措施如何进入发布沟通。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：3. 推理与能力层、7. 产品与组织层
- 作用：提供多模态模型发布与安全 eval 的官方样例。

## 关联

- [[concepts/MultimodalEvalSimulationEval边界]]
- [[concepts/EvalUncertaintyCommunicationReleaseCard边界]]
- [[Research: Multimodal eval simulation eval 边界]]
