---
type: entity
address: c-000611
title: "PM Skills Marketplace"
created: 2026-06-12
updated: 2026-06-12
tags:
  - agent-skills
  - product-management
  - marketplace
  - open-source
  - claude-code-plugin
status: active
related:
  - "[[entities/PMBrain]]"
  - "[[concepts/技能市场]]"
  - "[[concepts/AgentSkillsStandard]]"
  - "[[entities/ScientificAgentSkills]]"
  - "[[sources/pm-skills-2026-06-12]]"
---

# PM Skills Marketplace

**类型**：Agent Skills 市场（PM 垂直领域）  
**作者**：phuryn  
**GitHub**：https://github.com/phuryn/pm-skills  
**许可**：MIT | ⭐ 16K | v2.0.0（2026-06-05）

---

## 定位

面向产品管理的 Agent Skills 市场。将已建立的 PM 框架（Teresa Torres、Marty Cagan、Alberto Savoia 等）编码为 68 个 Agent Skills 和 42 个 Commands，分布在 9 个可安装 Plugins 中。

---

## 三层架构

| 层 | 说明 | 数量 |
|----|------|------|
| **Skills** | 原子技能，上下文匹配自动加载 | 68 |
| **Commands** | 斜杠命令工作流，串联多个 skills | 42 |
| **Plugins** | 可安装的领域包，包含 skills + commands | 9 |

---

## 9 个 Plugins

1. **pm-product-discovery**：头脑风暴、假设验证、机会解决方案树
2. **pm-product-strategy**：画布、价值主张、五力、定价
3. **pm-execution**：PRD、OKR、路线图、用户故事
4. **pm-market-research**：用户画像、竞争分析
5. **pm-data-analytics**：SQL、队列分析、A/B 测试
6. **pm-go-to-market**：GTM 策略、增长飞轮
7. **pm-marketing-growth**：定位、北极星指标
8. **pm-toolkit**：简历审阅、NDA、隐私政策
9. **pm-ai-shipping**：意图文档化、代码-文档审计

---

## 配套项目

- [[entities/PMBrain]]：PM 第二大脑，纯 Markdown

---

## 同类对比

| 项目 | 定位 | 差异 |
|------|------|------|
| [[entities/ScientificAgentSkills]] | 135 科学研究 skills | 科研垂直；repository 模式（全装） |
| PM Skills Marketplace | 68 PM skills | 产品垂直；marketplace 模式（选装 plugins） |

---

## 来源

- [[sources/pm-skills-2026-06-12]]
