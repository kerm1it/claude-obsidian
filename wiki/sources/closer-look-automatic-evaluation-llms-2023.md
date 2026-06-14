---
address: c-000433
type: source
title: "A Closer Look into Automatic Evaluation Using Large Language Models"
source_url: https://aclanthology.org/2023.findings-emnlp.599/
source_type: paper
author: "Cheng-Han Chiang, Hung-yi Lee"
published: 2023-12-06
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - ai
  - evals
  - llm-as-judge
  - automatic-evaluation
status: active
related:
  - "[[concepts/JudgeDriftGraderObservability边界]]"
  - "[[concepts/LLMJudgeAIFeedbackCalibration边界]]"
---

# A Closer Look into Automatic Evaluation Using Large Language Models

**来源**：ACL Anthology / EMNLP Findings
**URL**：https://aclanthology.org/2023.findings-emnlp.599/
**发布时间**：2023-12-06

## 摘要

论文系统研究用 LLM 做自动评估时，prompt、解释、参考答案、评分形式等设计选择如何影响与人工评分的相关性。

## 关键贡献

- LLM automatic evaluation 不是单一技术，而是一组会受 prompt 和程序细节影响的评分流程。
- 让模型先给解释、再给分数，常能提升和人工评价的相关性。
- 纯数字评分、CoT 或 reference 的使用并非总是稳定提升，需要按任务验证。
- 对本 vault 的意义：judge prompt/rubric/schema 是需要版本化和监控的 grader artifact。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：judge calibration、grader observability

## 关联

- [[concepts/JudgeDriftGraderObservability边界]]
- [[Research: Judge drift grader observability 边界]]
