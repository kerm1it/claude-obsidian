---
type: entity
address: c-000600
title: "Activeloop"
created: 2026-06-12
tags:
  - company
  - ai-infra
  - data-storage
  - yc
status: active
related:
  - "[[entities/Hivemind]]"
  - "[[sources/activeloopai-hivemind-2026-06-12]]"
---

# Activeloop

**类型**：AI 数据基础设施公司  
**产品**：Deeplake（面向 AI 的数据湖）、Hivemind（Agent 共享记忆）  
**背景**：Y Combinator-backed  
**网站**：https://activeloop.ai

---

## 核心产品

### Deeplake

面向 AI 工作负载的数据湖，支持张量格式存储、PyTorch/TensorFlow 直接读取、SQL 查询、向量搜索。Hivemind 的底层存储层。

### [[entities/Hivemind]]

2026 年发布的 Agent 共享记忆系统。基于 Deeplake 存储，提供 Capture→Codify→Propagate→Compound 循环。

---

## 技术方向

- **张量原生存储**：数据按 AI 训练/推理需要的格式存储，无需格式转换
- **BYOC**：支持 GCS、Azure、S3、本地部署，数据不出用户基础设施
- **Agent 基础设施**：从数据湖扩展到 Agent 运行时基础设施（Hivemind）

---

## 来源

- [[sources/activeloopai-hivemind-2026-06-12]]
