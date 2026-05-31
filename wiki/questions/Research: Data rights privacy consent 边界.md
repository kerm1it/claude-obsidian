---
address: c-000314
type: synthesis
title: "Research: Data rights privacy consent 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - privacy
  - consent
  - data-rights
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/DataRightsPrivacyConsent边界]]"
  - "[[concepts/DataFlywheelFeedbackLoop边界]]"
  - "[[concepts/ProductOrganizationLayer边界]]"
  - "[[concepts/RAG与Memory边界]]"
sources:
  - "[[sources/openai-api-data-controls-2026]]"
  - "[[sources/openai-model-improvement-data-policy-2026]]"
  - "[[sources/anthropic-privacy-policy-2026]]"
  - "[[sources/anthropic-consumer-model-training-controls-2026]]"
  - "[[sources/anthropic-commercial-data-controls-2026]]"
  - "[[sources/google-vertex-ai-data-governance-2026]]"
  - "[[sources/eu-ai-act-data-governance-2024]]"
  - "[[sources/gdpr-data-subject-rights-2016]]"
  - "[[sources/nist-genai-profile-data-privacy-2024]]"
---

# Research: Data rights privacy consent 边界

## Overview

Data rights / privacy / consent 主属第 7 层产品与组织层，是 data flywheel 前面的数据用途闸门。它回答“这条数据可以去哪里、保留多久、谁能访问、能否用于 memory/eval/training、用户或组织能否删除/导出/退出”。

## Key Findings

- OpenAI API 数据控制文档区分训练、滥用监测、应用状态和零保留等用途，说明同一条数据在服务、监控和训练之间必须有用途边界（Source: [[sources/openai-api-data-controls-2026]]）。
- OpenAI 模型改进政策区分个人服务与商业服务：商业数据默认不用于训练，消费者数据有 opt-out、临时聊天和记忆控制等机制（Source: [[sources/openai-model-improvement-data-policy-2026]]）。
- Anthropic 隐私政策列出访问、纠正、删除、导出、限制和退出等个人权利，并说明不同地区权利不同（Source: [[sources/anthropic-privacy-policy-2026]]）。
- Anthropic consumer 与 commercial 文档把免费/Pro 使用、商业服务、反馈、信任安全审查和数据保留分开处理，支持“用途标签”而不是“一个总开关”（Source: [[sources/anthropic-consumer-model-training-controls-2026]]，[[sources/anthropic-commercial-data-controls-2026]]）。
- Google Cloud Vertex AI 数据治理强调客户数据隔离、不用于训练基础模型，并提供 zero data retention 选项；这把 provider 层治理接到产品层 data rights（Source: [[sources/google-vertex-ai-data-governance-2026]]）。
- EU AI Act 对高风险 AI 系统要求训练、验证和测试数据集具备相关性、代表性、尽可能无错误、完整性和偏差治理（Source: [[sources/eu-ai-act-data-governance-2024]]）。
- GDPR 明确个人数据处理需要目的、合法基础、透明性和数据主体权利；AI 产品的数据飞轮必须能支持访问、删除、导出、反对和限制处理（Source: [[sources/gdpr-data-subject-rights-2016]]）。
- NIST GenAI Profile 将数据隐私、数据来源、数据质量、可追溯性和有害输出纳入生成式 AI 风险管理；这支持把 privacy 当作 eval/governance gate（Source: [[sources/nist-genai-profile-data-privacy-2024]]）。

## Stable Definition

```text
data or feedback
    -> classify purpose and subject
    -> check consent, contract, policy, law
    -> minimize, redact, isolate by tenant
    -> route to allowed path: service, memory, eval, analytics, training, vendor
    -> enforce retention, deletion, export, audit
```

## Boundary Decisions

| 问题 | 稳定答案 |
|---|---|
| 用户内容能否用于回答本次请求？ | 可以，但仍受会话、工具、provider 和组织权限约束 |
| 用户内容能否写入 memory？ | 需要 memory-specific 控制，可见、可删、可关闭 |
| 失败 trace 能否进入 eval？ | 需要权限标签、脱敏、保留期和 hold-out 隔离 |
| 显式反馈能否训练模型？ | 需要明确用途说明和可审计授权 |
| 企业客户数据能否跨客户改进模型？ | 默认应 tenant-scoped，除非合同或设置明确允许 |
| 匿名化数据能否随意使用？ | 不能；仍要评估重识别、小样本和目的限制 |

## Open Questions

- 多 provider model routing 如何自动比较不同供应商的 retention、training use 和 subprocessor 条款。
- 已进入模型权重的个人数据如何处理删除请求，工程上仍需要 provider、法律和模型治理共同定义。
- Agent 长期 memory 的用户可见、组织级审批和 tenant 权限继承还缺少行业统一模式。

## Sources

- [[sources/openai-api-data-controls-2026]]
- [[sources/openai-model-improvement-data-policy-2026]]
- [[sources/anthropic-privacy-policy-2026]]
- [[sources/anthropic-consumer-model-training-controls-2026]]
- [[sources/anthropic-commercial-data-controls-2026]]
- [[sources/google-vertex-ai-data-governance-2026]]
- [[sources/eu-ai-act-data-governance-2024]]
- [[sources/gdpr-data-subject-rights-2016]]
- [[sources/nist-genai-profile-data-privacy-2024]]
