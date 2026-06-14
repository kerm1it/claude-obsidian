---
address: c-000470
type: source
title: "Deploy and operate generative AI applications"
source_url: https://docs.cloud.google.com/architecture/deploy-operate-generative-ai-applications
source_type: official-docs
author: "Google Cloud Architecture Center"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - genaiops
  - monitoring
  - continuous-evaluation
  - lineage
status: active
related:
  - "[[concepts/PostReleaseEvalDrift边界]]"
  - "[[concepts/DatasetLineageProvenanceGraph边界]]"
---

# Deploy and Operate Generative AI Applications

**来源**：Google Cloud Architecture Center
**URL**：https://docs.cloud.google.com/architecture/deploy-operate-generative-ai-applications

## 摘要

Google Cloud 的 GenAI 应用部署指南强调，生产级 generative AI 应用由多组件链路组成，必须对应用端到端和组件级输入、输出、中间状态、配置和 lineage 做日志与监控。文档还把 drift、skew、performance decay、alerting 和 continuous evaluation 作为生产运行的一部分。

## 关键贡献

- 要求对 chain 作为完整 artifact 进行版本管理和日志记录。
- 强调 application-level monitoring 优先，再深入到 prompt/model 组件。
- 把 drift/skew 与 evaluation dataset、production input、output data 和 continuous evaluation 连接。
- 对本 vault 的意义：post-release eval drift 需要绑定 lineage 和 artifact identity，否则无法判断哪份 release evidence 失效。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/PostReleaseEvalDrift边界]]
- [[Research: Post-release eval drift 边界]]
