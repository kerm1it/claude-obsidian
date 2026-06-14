---
address: c-000464
type: source
title: "A Structured Approach to Safety Case Construction for AI Systems"
source_url: https://arxiv.org/abs/2601.22773
source_type: paper
author: "Sung Une Lee, Liming Zhu, Md Shamsujjoha, Liming Dong, Qinghua Lu, Jieshan Chen, Lionel Briand"
published: 2026-01-30
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - ai
  - safety-case
  - assurance
  - agentic-ai
status: active
related:
  - "[[concepts/SafetyCaseAssuranceCase边界]]"
  - "[[concepts/OfflineOnlineEvalCorrelation边界]]"
---

# A Structured Approach to Safety Case Construction for AI Systems

**来源**：arXiv
**URL**：https://arxiv.org/abs/2601.22773
**发布**：2026-01-30

## 摘要

论文指出传统 safety case 依赖清晰边界、稳定架构和已知 failure modes，而 generative / agentic AI 行为会随 prompt、fine-tuning、scaffolding 和 deployment context 改变。作者提出 AI-specific claim、argument 和 evidence taxonomy，以及可复用、可组合、可维护的 safety-case template。

## 关键贡献

- 将 AI safety case 的 claim、argument 和 evidence family 系统分类。
- 强调 AI safety case 必须可审计、可适应动态行为，并能处理 no ground truth、dynamic updates 和 threshold risk decision。
- 对本 vault 的意义：safety case 需要绑定模型/工具/上下文变更和 post-release monitoring，不能是静态文档。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层、5. Agent 系统层

## 关联

- [[concepts/SafetyCaseAssuranceCase边界]]
- [[Research: Safety case assurance case 边界]]
