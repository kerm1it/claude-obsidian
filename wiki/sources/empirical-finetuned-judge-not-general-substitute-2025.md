---
address: c-000434
type: source
title: "Can LLMs Substitute Human Labelers? An Empirical Study of Fine-tuned LLM Judges"
source_url: https://aclanthology.org/2025.findings-acl.306/
source_type: paper
author: "ACL Findings authors"
published: 2025-07-27
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - ai
  - evals
  - llm-as-judge
  - human-labelers
status: active
related:
  - "[[concepts/JudgeDriftGraderObservability边界]]"
  - "[[concepts/HumanFeedbackAnnotationOps边界]]"
---

# Can LLMs Substitute Human Labelers?

**来源**：ACL Anthology / Findings of ACL 2025
**URL**：https://aclanthology.org/2025.findings-acl.306/
**发布时间**：2025-07-27

## 摘要

论文研究 fine-tuned LLM judges 能否替代人类标注员。结论对生产系统很重要：即使模型裁判在某些数据上表现好，也不能直接当作通用人工替代品。

## 关键贡献

- 将 LLM judge 与人类标注替代问题拆成经验验证问题。
- 强调 fine-tuned judge 的可靠性受任务、数据分布和评估标准影响。
- 对本 vault 的意义：judge observability 必须持续看新分布上的 human agreement 和生产相关性，不能只依赖一次 fine-tune 后的基准分。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：human feedback / annotation ops

## 关联

- [[concepts/JudgeDriftGraderObservability边界]]
- [[concepts/HumanFeedbackAnnotationOps边界]]
- [[Research: Judge drift grader observability 边界]]
