---
address: c-000424
type: source
title: "Anytime-Valid Confidence Sequences in an Enterprise A/B Testing Platform"
source_url: https://arxiv.org/abs/2302.10108
source_type: paper
author: "Akash V. Maharaj et al."
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - statistics
  - ab-testing
  - confidence-sequences
status: active
related:
  - "[[concepts/EvalResultInterpretationDecisionThreshold边界]]"
---

# Anytime-Valid Confidence Sequences in an Enterprise A/B Testing Platform

**来源**：arXiv / ACM Web Conference Companion 2023
**URL**：https://arxiv.org/abs/2302.10108

## 摘要

这篇论文讨论在企业 A/B testing 平台中使用 anytime-valid confidence sequences，解决固定样本量方法在连续监控和数据依赖停止时容易产生假阳性的问题。

## 关键贡献

- 说明传统 fixed-horizon 检验在频繁查看结果时会膨胀 type-I error。
- 提供持续监控实验时仍保持有效置信推断的工程方案。
- 对本 vault 的意义：continuous eval、canary 和线上实验都需要明确停止规则；边看边停会让 eval threshold 变成噪声放大器。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/EvalResultInterpretationDecisionThreshold边界]]
- [[Research: Eval result interpretation decision threshold 边界]]
