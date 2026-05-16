---
id: c-000108
address: c-000108
type: concept
title: "TokenJuice"
aliases: ["Token Juice", "智能Token压缩", "token compression"]
created: 2026-05-16
tags:
  - token-compression
  - llm
  - optimization
  - open-source
status: active
---

# TokenJuice

[[entities/OpenHuman]] 自研的 **Token 预处理压缩层**。每个工具调用、爬取结果、邮件正文、搜索载荷在进入任何 LLM 之前，都先经过 TokenJuice 处理，去除冗余内容。

## 处理流程

```
原始输入（HTML、邮件、搜索结果）
        ↓
  TokenJuice 预处理层
  - HTML → Markdown 转换
  - 长 URL 缩短
  - 非 ASCII 字符移除
  - 其他规范化操作
        ↓
   压缩后的 Markdown 块
        ↓
     LLM 处理
```

## 效果

- **成本与延迟最多降低 80%**
- 保留相同的信息量，仅去除格式冗余
- 对所有工具调用透明应用（无需用户配置）

## 适用场景

- Web 爬取结果（HTML → 干净 Markdown）
- 邮件正文（HTML 邮件去格式化）
- 搜索 API 响应（JSON 冗余字段移除）
- 集成工具调用返回值（Notion、Jira、GitHub 等）

## 与其他压缩方案的对比

TokenJuice 是**预处理层**，不是模型级压缩（如 Flash Attention 或 KV Cache 优化）。它通过清洁输入减少 token 数，而非改变模型推理方式。

类似思路：
- 自研 Markdown 清洗管道（如 [[entities/ClaudeCowork]] 内部做法）
- [[concepts/渐进式上下文注入]] — 按需注入上下文，与压缩互补

## 关联

- [[entities/OpenHuman]] — 出品方
- [[concepts/记忆自动拉取]] — 与 Auto-fetch 协同：拉取的数据经 TokenJuice 压缩后入 Memory Tree
- [[concepts/MemoryTree]] — 压缩后的 token 块存入 Memory Tree
- [[sources/openhuman-2026-05-16|来源：GitHub README]]
