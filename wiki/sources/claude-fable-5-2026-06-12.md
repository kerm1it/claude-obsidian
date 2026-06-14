---
type: source
address: c-000605
title: "Introducing Claude Fable 5"
source_url: https://youtu.be/Y9Wz2PV404E
created: 2026-06-12
updated: 2026-06-12
source_date: 2026-06-12
tags:
  - anthropic
  - model-release
  - claude
  - safety
status: active
related:
  - "[[entities/ClaudeFable5]]"
  - "[[entities/ClaudeMythos]]"
  - "[[entities/Anthropic]]"
  - "[[concepts/安全重定向]]"
  - "[[concepts/负责任发布]]"
---

# Introducing Claude Fable 5

**来源**：[[entities/Anthropic]] 官方 YouTube  
**发布日期**：2026-06-12  
**类型**：产品发布公告视频

---

## 核心信息

Claude Fable 5 是 Anthropic "有史以来向公众发布的最强模型"（the most capable model we've ever released to the public）。

---

## 关键叙述

### Mythos 的未发布与原因

Anthropic 上一个达到此能力水平的模型是 **Claude Mythos preview**。训练和测试完成后，团队发现 Mythos 能发现**数千个网络安全漏洞**。一个能发现这些漏洞的模型也能被用来利用它们。

> 因此，Anthropic 没有公开发布 Mythos，而是将其交给保护关键软件的人，在漏洞被突破之前修复它们。

Anthropic 明确表示："这是当时正确的决定，但从来不是目标。"

### 负责任发布逻辑

1. 训练 Mythos（高能力，发现数千漏洞）
2. 不公开发布，交给安全团队修漏洞
3. 基于 Mythos 构建 Fable 5（同样能力级别，但加了更多 safeguards）
4. 公开发布 Fable 5

核心理念："强大的 AI 应该安全且可访问。"

---

## Fable 5 的关键能力

| 维度 | 描述 |
|------|------|
| **模型级别** | Mythos 级（最高能力层） |
| **超长持续** | 可以连续工作数天，无需人工干预 |
| **高度自主** | "highly autonomous, can operate for days without intervention" |
| **领域覆盖** | 不仅限于编码——可处理金融、研究、经济学、法律等复杂项目 |
| **复杂度** | "过去需要持续监督的复杂任务" |

---

## 安全机制：重定向

对于触碰到高风险领域的请求（如网络安全、生物学），Fable 5 的安全系统：

1. **自动审查**请求
2. **重定向到 Opus 4.8**——一个能力较弱但已充分验证的模型
3. 用户仍可受益于强大模型的能力，但绕过网络和生物风险

**设计意图**：今天的 safeguards 覆盖范围较宽；后续将持续细化，让安全请求能更精准地通过。

---

## 关键洞察

1. **Mythos→Fable 的发布范式**：不是"训练完就发"，而是"训练→发现过度能力→内部修复→发布安全版"。这是 Anthropic 负责任扩缩策略（RSP）的具体实例
2. **能力与安全的分离**：不削弱模型能力，而是在危险领域通过重定向"卸载"风险——模型本身仍然强大，但高风险查询走更安全的路径
3. **Opus 作为安全锚点**：Opus 4.8 在这里扮演的不是"最强模型"而是"最安全模型"的角色
4. **"不止是编程"**：Fable 5 的定位从编码工具扩展到通用复杂问题求解器（金融、研究、经济、法律）

---

## 来源

- [[entities/ClaudeFable5]] — 实体页
- [[entities/ClaudeMythos]] — 未发布的前身模型
- [[concepts/安全重定向]] — 高风险请求重定向机制
- [[concepts/负责任发布]] — Mythos→Fable 发布范式
