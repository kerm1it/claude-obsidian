---
address: c-000480
type: source
title: "A Subjective Logic-based method for runtime confidence updates in safety arguments"
source_url: https://arxiv.org/abs/2605.22530
source_type: paper
author: "Herd, Kelly, Heinemann, Zacchi"
date_published: 2026-05-21
fetched: 2026-05-30
created: 2026-05-30
confidence: medium
tags:
  - assurance-case
  - runtime-confidence
  - safety-performance-indicators
status: active
related:
  - "[[concepts/EvidenceFreshnessStaleProof边界]]"
  - "[[concepts/PostReleaseEvalDrift边界]]"
---

# Runtime Confidence Updates in Safety Arguments

**来源**：arXiv / SAC 2026
**URL**：https://arxiv.org/abs/2605.22530

## 摘要

论文提出用 Subjective Logic 将 design-time evidence 和 windowed runtime Safety Performance Indicators 结合，在运行时持续更新 safety argument 中 claim 的 confidence。

## 关键贡献

- 将静态 safety case 与 runtime evidence 放进同一个 assurance case。
- 用 windowed SPI 证据影响目标 claim confidence。
- 设计目标偏向安全响应：出现 violation 时快速降低 confidence。
- 对本 vault 的意义：stale proof 可以不只是二元 fresh/stale，也可以把运行证据转成 claim confidence 的更新。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/EvidenceFreshnessStaleProof边界]]
- [[Research: Evidence freshness stale proof 边界]]
