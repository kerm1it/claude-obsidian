---
address: c-000584
type: source
title: "Log user feedback using the SDK"
source_url: https://docs.langchain.com/langsmith/attach-user-feedback
source_type: official-docs
author: "LangChain"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - langsmith
  - tracing
  - feedback
  - evals
status: active
related:
  - "[[concepts/ProductFeedbackClosureActionability边界]]"
  - "[[concepts/OfflineOnlineEvalCorrelation边界]]"
  - "[[concepts/DataFlywheelFeedbackLoop边界]]"
---

# Log User Feedback Using the SDK

**来源**：LangSmith Docs
**URL**：https://docs.langchain.com/langsmith/attach-user-feedback

## 摘要

LangSmith 文档说明如何把用户、标注员或自动 evaluator 产生的 feedback 附着到 trace 或 child run。它强调 feedback 对 monitoring 和 evaluating applications 很关键，并且可以针对 RAG pipeline 的 retrieval step 或 generation step 等具体子步骤记录。

## 关键贡献

- Feedback 不应只作为全局 thumbs-up/down，而应能绑定到 trace 或 child run。
- 绑定 run_id / trace_id 后，团队可以定位具体 retrieval、generation、tool 或 chain step 的问题。
- Client-side feedback 可以通过 scoped presigned token 收集，避免暴露 API key。
- 对本 vault 的意义：feedback closure 的最小证据单元应该包含 trace/run 绑定，否则无法归因和验证。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层、5. Agent 系统层

## 关联

- [[concepts/ProductFeedbackClosureActionability边界]]
- [[concepts/OfflineOnlineEvalCorrelation边界]]
- [[Research: Product feedback closure data flywheel actionability 边界]]
