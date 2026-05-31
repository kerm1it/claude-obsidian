---
address: c-000248
type: source
title: "Prompt caching"
source_url: https://docs.anthropic.com/en/docs/build-with-claude/prompt-caching
source_type: documentation
author: "Anthropic"
published: 2026-05-30
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - prompt-caching
  - latency
  - cost
status: active
related:
  - "[[concepts/Serving成本延迟边界]]"
  - "[[concepts/上下文工程]]"
---

# Prompt caching

**来源**：Anthropic Docs
**URL**：https://docs.anthropic.com/en/docs/build-with-claude/prompt-caching

## 摘要

Anthropic prompt caching 允许开发者缓存长且重复的 prompt 前缀，尤其适合 tool definitions、system instructions、few-shot examples、长文档和 agent instructions。它把上下文工程直接连接到 serving 成本和延迟。

## 关键贡献

- 缓存不是语义记忆，而是重复上下文前缀的 serving 优化。
- 适合稳定前缀，不适合高变化的动态上下文。
- 对长文档、代码库、工具说明和多轮 agent instruction 可以显著降低重复处理成本。
- Prompt 结构会影响缓存命中率：稳定内容应放在前面，动态内容放在后面。

## 对 AI 知识体系的归属

- 主归属：4. 上下文与知识层
- 交叉链接：3. 推理与能力层、7. 产品与组织层
- 作用：说明 context engineering 如何通过缓存影响 serving unit economics。

## 关联

- [[concepts/Serving成本延迟边界]]
- [[Research: Serving 成本 延迟 边界]]
