---
address: c-000382
type: synthesis
title: "Research: Data deletion unlearning impact 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - data-deletion
  - machine-unlearning
status: developing
related:
  - "[[concepts/DataDeletionUnlearningImpact边界]]"
  - "[[concepts/DataRightsPrivacyConsent边界]]"
  - "[[concepts/DatasetLineageProvenanceGraph边界]]"
  - "[[concepts/DataQualityLabelQuality边界]]"
sources:
  - "[[sources/gdpr-data-subject-rights-2016]]"
  - "[[sources/machine-unlearning-sisa-2019]]"
  - "[[sources/google-machine-unlearning-challenge-2023]]"
  - "[[sources/machine-unlearning-comprehensive-survey-2024]]"
---

# Research: Data deletion unlearning impact 边界

## Overview

Data deletion / unlearning impact 的稳定核心是“删除请求如何穿透 AI 系统全链路”：从产品存储、日志、RAG、memory、eval、training dataset、synthetic derivatives、provider logs 到 model weights。它主属第 7 层，因为它是用户/组织/合同/保留策略的执行闭环；它依赖第 6 层 lineage 与 eval，并在必要时调用第 2 层 machine unlearning 或 retraining。

## Key Findings

- GDPR Article 17 提供删除权锚点，但删除权并非无条件；工程系统仍要记录请求范围、法律/合同基础、例外和通知链。（Source: [[sources/gdpr-data-subject-rights-2016]]）
- SISA training 的核心思路是预先限制单个数据点影响范围，通过 shard、slice、aggregation 和缓存降低未来 unlearning 成本。（Source: [[sources/machine-unlearning-sisa-2019]]）
- Google/NeurIPS 2023 Machine Unlearning Challenge 将 unlearning 定义为从模型中移除 forget set 影响，同时保持 retain/held-out utility；它指出 unlearning evaluation 长期缺少统一 protocol。（Source: [[sources/google-machine-unlearning-challenge-2023]]）
- 2024 survey 将 unlearning 方法分成 exact、approximate、distributed/federated/graph unlearning、verification、privacy/security 等方向，说明这不是单一算法问题。（Source: [[sources/machine-unlearning-comprehensive-survey-2024]]）
- 对工程系统，最重要的边界是“删除数据”不等于“模型遗忘”；RAG/memory/log 删除通常可直接执行，模型权重影响需要 retraining、unlearning、replacement 或至少 suppression + 风险说明。

## Stable Classification

- 主归属：7. 产品与组织层
- 上游：data rights、retention、incident、bad data report、copyright/privacy request、lineage impact query
- 下游：store deletion、RAG/memory/eval/training cleanup、provider deletion、model retraining/unlearning/replacement、audit
- 关键连接：第 6 层 lineage 找影响面，第 6 层 eval 验证删除和遗忘，第 2 层执行 weight-level 处理。

## Engineering Practice

1. 先验证 requester、scope、basis、tenant、resource 和 exception。
2. 用 lineage 查询所有下游：logs、RAG chunks、embeddings、memory、eval、training rows、synthetic derivatives、model versions、provider state。
3. 按位置选择动作：删除、限制处理、tombstone、匿名化、dataset manifest 更新、eval 重算、retrain/unlearn/replace。
4. 验证删除：数据不可检索、不可导出、不可再摄入；模型侧用 retain utility、forgetting quality、membership inference 和 regression eval。
5. 写入 audit：请求、处理路径、例外、owner、时间、验证证据、用户/组织通知。

## Open Questions

- 大模型中样本级 unlearning 的可证明性仍弱，尤其是 web-scale pretraining 和 instruction data 混合后。
- 删除训练样本与删除“概念/事实/风格”的边界仍不稳定。
- Provider、backup、customer-owned logs、fine-tuned models 和 distilled models 的删除影响需要更明确合同和工具支持。

## Sources

- [[sources/gdpr-data-subject-rights-2016]]：删除权、访问权、可携带权和数据主体权利基础。
- [[sources/machine-unlearning-sisa-2019]]：SISA 和 machine unlearning 经典工程思路。
- [[sources/google-machine-unlearning-challenge-2023]]：unlearning 评估和 challenge 设计。
- [[sources/machine-unlearning-comprehensive-survey-2024]]：unlearning 方法分类与 open problems。
