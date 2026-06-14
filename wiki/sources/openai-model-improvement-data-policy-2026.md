---
address: c-000316
type: source
title: "How your data is used to improve model performance"
source_url: https://openai.com/policies/how-your-data-is-used-to-improve-model-performance/
source_type: policy
author: "OpenAI"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - ai
  - openai
  - model-improvement
  - privacy
status: active
related:
  - "[[concepts/DataRightsPrivacyConsent边界]]"
  - "[[concepts/DataFlywheelFeedbackLoop边界]]"
---

# How your data is used to improve model performance

**来源**：OpenAI Policies
**URL**：https://openai.com/policies/how-your-data-is-used-to-improve-model-performance/

## 摘要

OpenAI 的模型改进说明区分个人服务和商业服务的数据用途。商业产品的业务数据默认不用于训练；个人产品提供 model improvement 设置、临时聊天和记忆控制。

## 关键贡献

- 明确不同产品线的数据默认行为不同，不能只问“OpenAI 会不会训练”。
- 将用户反馈、聊天内容、文件、记忆和临时聊天拆成不同控制面。
- 支持本 vault 的稳定规则：模型训练是高强度用途，必须比服务运行、产品分析和 eval 有更高权限门槛。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：2. 模型构建层、4. 上下文与知识层

## 关联

- [[concepts/DataRightsPrivacyConsent边界]]
- [[Research: Data rights privacy consent 边界]]
