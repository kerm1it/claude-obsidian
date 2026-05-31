---
address: c-000315
type: source
title: "OpenAI API data controls"
source_url: https://developers.openai.com/api/docs/guides/your-data
source_type: documentation
author: "OpenAI"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - ai
  - openai
  - data-controls
  - privacy
status: active
related:
  - "[[concepts/DataRightsPrivacyConsent边界]]"
  - "[[concepts/DataFlywheelFeedbackLoop边界]]"
---

# OpenAI API data controls

**来源**：OpenAI Developers
**URL**：https://developers.openai.com/api/docs/guides/your-data

## 摘要

OpenAI API 数据控制文档区分 API 输入输出、文件、缓存、应用状态、滥用监测和模型训练等数据用途，并说明 API 商业客户的数据默认不用于训练。它是 AI 工程中 data rights 的平台侧锚点。

## 关键贡献

- 将“服务运行”“安全/滥用监测”“应用状态”“模型训练”分开处理。
- 说明 zero data retention 等更严格保留策略需要特定资格或配置。
- 对本 vault 的意义：第 7 层必须先判断数据是否允许进入 logging、eval、memory 或 training，不能把 API 使用自动等同于训练授权。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层、4. 上下文与知识层

## 关联

- [[concepts/DataRightsPrivacyConsent边界]]
- [[Research: Data rights privacy consent 边界]]
