---
address: c-000379
type: source
title: "ML Metadata"
source_url: https://www.tensorflow.org/tfx/guide/mlmd
source_type: documentation
author: "TensorFlow / Google"
date_published: 2024-09-06
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - mlops
  - lineage
  - metadata
status: active
related:
  - "[[concepts/DatasetLineageProvenanceGraph边界]]"
  - "[[concepts/DataQualityLabelQuality边界]]"
---

# ML Metadata

**来源**：TensorFlow TFX Docs
**URL**：https://www.tensorflow.org/tfx/guide/mlmd

## 摘要

ML Metadata 是记录和检索 ML workflow metadata 的库。它记录 pipeline components、executions、artifacts、events 和 contexts，使平台能分析 pipeline lineage、调试异常并回答“哪个数据集训练了这个模型”等问题。

## 关键贡献

- 把 ML workflow 建模为 artifact、execution、event、context、attribution 和 association。
- event 记录 execution 使用了哪些 artifact、产生了哪些 artifact，从而支持 workflow lineage。
- 支持从 artifact 回溯上游输入，或查询某个 dataset 生成了哪些 model。
- 对本 vault 的意义：第 6 层 lineage graph 可以直接借用 artifact/execution/event 模型来追踪训练、eval、RAG、memory 和 skill 候选。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：2. 模型构建层、6. data quality、7. incident response

## 关联

- [[concepts/DatasetLineageProvenanceGraph边界]]
- [[Research: Dataset lineage provenance graph 边界]]
