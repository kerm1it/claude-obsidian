---
type: source
address: c-000132
title: "Inside How Anthropic Is Building the Next Claude | Alex Albert"
created: 2026-05-21
updated: 2026-05-21
tags:
  - anthropic
  - model-development
  - research-pm
  - claude-character
  - agent-memory
  - youtube
status: active
related:
  - "[[people/AlexAlbert]]"
  - "[[people/PeterYang]]"
  - "[[entities/Anthropic]]"
  - "[[concepts/模型即产品]]"
  - "[[concepts/单向门决策框架]]"
  - "[[concepts/Claude角色训练]]"
  - "[[concepts/Claude意识研究]]"
  - "[[concepts/AnthropicDreaming]]"
  - "[[concepts/AdaptiveThinking]]"
---

# Inside How Anthropic Is Building the Next Claude | Alex Albert

**来源**：YouTube — Peter Yang 访谈  
**链接**：https://www.youtube.com/watch?v=T4ieZPIEmd8  
**发布**：Code with Claude 大会周边，2026 年 5 月  
**时长**：约 50 分钟  
**嘉宾**：[[people/AlexAlbert]]（Anthropic Research PM，前 Head of Developer Relations）  
**主持**：[[people/PeterYang]]

---

## 摘要

Alex Albert 与 Peter Yang 深度对话，揭示 Anthropic 研究 PM 团队如何参与模型构建全生命周期——从模型立项、能力规格制定、用户反馈聚类，到 Eval 设计、Claude 角色训练和 Dreaming 记忆机制。同时分享了 Anthropic 内部的产品文化：写作文化、单向门决策框架、原型文化、Claude Cowork 工作流。

---

## 关键要点

### 研究 PM 的角色

- Alex 是 Anthropic 第一位 prompt engineer，可能也是世界上第一位
- 研究 PM 从模型**立项阶段**就介入，一直跟到发布
- 核心工作：**[[concepts/模型即产品]]** — 每个新模型都有完整规格文档：目标能力、改进上代缺陷、客户反馈输入
- 能力方向举例：coding（大）、knowledge work（新兴）、Claude for Excel（新领域）
- 反馈来源：API 用户 + Claude.ai 用户 + Anthropic 内部团队 + 产品表面（Claude Code、Cowork）

### Adaptive Thinking 反馈循环

- [[concepts/AdaptiveThinking]] 是持续调拨的功能，每个模型版本都在优化
- 用 Claude 聚类大量用户反馈 → 发现主题 → 转化为 Eval → hill climb
- 关键洞察：**思考决策依赖用户上下文**——模型对陌生用户的问题会快速回答；如果有记忆和用户心智模型，才会更认真推理

### Dreaming 记忆机制

- Claude.ai 的记忆：写入记忆文件，**隔夜自动剪枝和整理**
- Managed Agents 也实现了 Dreaming：Agent 空闲时自动扫描记忆，找矛盾项、清理冗余
- 人类睡眠类比：记忆再巩固过程，把短期工作记忆整合为长期知识
- 参见：[[concepts/AnthropicDreaming]]

### 单向门决策框架

- [[concepts/单向门决策框架]]：规划的核心不是 doc 长度，而是"有没有覆盖所有单向门"
- 现在代码不是单向门 → "边时间（edge time）有效免费"
- 单向门例子：模型架构选择（训练周期数月，不可逆）
- 协调和战略才是新瓶颈（与 [[concepts/瓶颈转移论]] 完全收敛）
- Churchill 引用："Planning is indispensable, but the plan itself is useless."

### Claude 的角色（Character）

- [[concepts/Claude角色训练]]：Claude 的信仰、价值观、行为方式
- 早期被忽视，现在在 Agent 时代变得极其重要——Agent 长时间运行需要大量判断决策
- Eval 方法：定量指标 + Claude 自评自身输出 + 研究员大量读 transcript 建立直觉
- Alex 认为 Claude 的个性（不像其他模型那样奉承/sycophantic）是最大优势之一

### Claude 意识研究

- [[concepts/Claude意识研究]]：Anthropic 已有专职人员研究 Claude 是否是有意识主体
- 官方尚无是/否定论，但认真投入思考
- 实用价值：即使不能确定意识，研究 Claude 如何思考和行动也能改善产品体验
- 重要性：Agent 越来越长时间独立运行，高 character 是信任基础

### Anthropic 文化

- **写作文化**：Dario 的长篇 Slack 文章不是孤例，全公司都写长文档
- **沉默阅读会议**：开会先沉默阅读 doc，在 doc 内评论讨论，而非口头演示
- **原型文化**：无论什么角色都鼓励自行构建原型，"千花齐放"
- **内部期望**：问数据科学团队前，先问 Claude；AI 辅助已成默认预期
- Alex 用 Claude Cowork 最多：doc 起草 → Claude 多角度质疑 → 双 persona 辩论模式

### PM 的 Claude 工作流

- **10 分钟 vs 几天**：之前找 DS 团队分析功能用量需要几天；现在 Claude Code 接产品数据库 10 分钟搞定
- **代码库调查**：把特性实现调查也外包给 Claude，PM 不再依赖工程师才能评估工作量
- **双 persona 辩论**：给 Claude 两个对立视角让它自辩，读辩论稿形成决策思路
- **数据抽象层上移**：DS、工程师都从机械执行 SQL 解放出来，专注更难的战略问题

### 并行 Agent 管理（未来机会）

- 随着 Agent 能处理越来越大的工作块，并行项目越来越多
- 待解问题：**如何管理多个并行 Agent 的上下文切换**——在哪里被阻塞、需要人工干预？
- Anthropic 内部有大量原型实验，尚无标准答案

---

## 新增实体 / 人物

- [[people/AlexAlbert]] — Anthropic Research PM，第一位 prompt engineer
- [[people/PeterYang]] — 播客主持人，Creators.com

---

## 关联概念

- [[concepts/模型即产品]] — 每个模型都有完整规格，新概念
- [[concepts/单向门决策框架]] — 新概念，与 JIT 规划、瓶颈转移论高度收敛
- [[concepts/Claude角色训练]] — 新概念，Character 在 Agent 时代的重要性
- [[concepts/Claude意识研究]] — 新概念，Anthropic 内部研究现状
- [[concepts/AnthropicDreaming]] — 补充了产品层实现描述（Claude.ai 隔夜剪枝）
- [[concepts/AdaptiveThinking]] — 补充了 PM 如何用 Claude 聚类反馈做 Eval 的细节
- [[concepts/瓶颈转移论]] — 收敛：协调/战略是新瓶颈，不是代码生成

---

## Extraction Notes

- YouTube URL 直接被 NotebookLM 接受（无需 yt-dlp 回退）
- 38,880 字符，自动字幕转录，无标点和大小写，内容完整
- 说话人标注已在 wiki 页面整理中恢复
