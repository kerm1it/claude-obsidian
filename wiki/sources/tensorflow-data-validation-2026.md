---
address: c-000346
type: source
title: "TensorFlow Data Validation"
source_url: https://tensorflow.google.cn/tfx/guide/tfdv
source_type: documentation
author: "TensorFlow / Google"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - ai
  - data-quality
  - validation
  - mlops
status: active
related:
  - "[[concepts/DataQualityLabelQuality边界]]"
---

# TensorFlow Data Validation

**来源**：TensorFlow / TFX Documentation
**URL**：https://tensorflow.google.cn/tfx/guide/tfdv

## 摘要

TensorFlow Data Validation 用于生成数据统计、推断 schema、检测异常，并比较训练和服务数据。它通常在 TFX pipeline 的多个阶段运行。

## 关键贡献

- 将数据质量从人工检查变成 pipeline 内的 schema/statistics/anomaly gate。
- 支持检测训练/服务数据异常和分布差异。
- 对本 vault 的意义：data quality 是第 6 层可自动化质量门，不是临时清洗脚本。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：2. 模型构建层、7. 产品与组织层

## 关联

- [[concepts/DataQualityLabelQuality边界]]
- [[Research: Data quality label quality 边界]]
