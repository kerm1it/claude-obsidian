---
address: c-000307
type: source
title: "Data sharing settings for model improvement"
source_url: https://help.openai.com/en/articles/10306912-data-controls-faq
source_type: documentation
author: "OpenAI"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - data-controls
  - privacy
  - feedback
status: active
related:
  - "[[concepts/DataFlywheelFeedbackLoop边界]]"
  - "[[concepts/ProductOrganizationLayer边界]]"
  - "[[concepts/DataRightsPrivacyConsent边界]]"
---

# Data sharing settings for model improvement

**来源**：OpenAI Help Center
**URL**：https://help.openai.com/en/articles/10306912-data-controls-faq

## 摘要

OpenAI 的数据控制说明区分不同产品和数据分享设置，强调用户或组织可以控制数据是否用于模型改进。它为 data flywheel 增加了权限和用途边界。

## 关键贡献

- 反馈、API 输入输出、文件上传和自定义 GPT 相关数据不应默认被视为同一类训练材料。
- 企业和组织环境需要独立的数据控制和管理边界。
- 对本 vault 的意义：第 7 层 telemetry 必须先经过 [[concepts/DataRightsPrivacyConsent边界|data rights / consent gate]]，再谈反哺第 2/4/6/8 层。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[concepts/DataFlywheelFeedbackLoop边界]]
- [[concepts/DataRightsPrivacyConsent边界]]
- [[Research: Data flywheel feedback loop 边界]]
