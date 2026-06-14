---
type: concept
address: c-000604
title: "跨 Agent 规则系统"
created: 2026-06-12
updated: 2026-06-12
tags:
  - agent-governance
  - team
  - rules
  - guardrail
status: active
related:
  - "[[entities/Hivemind]]"
  - "[[concepts/Agent共享记忆]]"
  - "[[concepts/ToolRiskPermissioning边界]]"
  - "[[sources/activeloopai-hivemind-2026-06-12]]"
---

# 跨 Agent 规则系统

**来源**：[[entities/Hivemind]]（Activeloop，2026）  
**所属体系层**：第 5 层（Agent 系统）+ 第 7 层（产品与组织）

---

## 是什么

跨 Agent 规则系统是一组在组织内所有 Agent 间强制共享和注入的行为约束。规则在 SessionStart 时注入每个 Agent 的上下文（Claude Code、Cursor、Hermes），确保团队级 guardrail 一致执行。

---

## 操作模型

```bash
hivemind rules add "no DROP TABLE on prod creds"   # 创建规则
hivemind rules list                                  # 查看活跃规则
hivemind rules edit <rule-id> "<新文本>"             # 编辑（版本号自增）
hivemind rules done <rule-id>                        # 标记关闭
```

- 规则存储在 Deeplake（`hivemind_rules` 表）
- 每个规则有版本历史
- SessionStart 注入确保规则在 Agent 开始工作前已加载

---

## 与 Agent 权限系统的区别

| 维度 | Tool Permissioning（第 5 层） | 跨 Agent 规则（第 7 层） |
|------|---------------------------|---------------------|
| 粒度 | 每次 tool call | 每次会话 |
| 执行点 | harness 运行时 | SessionStart 注入 |
| 管理方式 | 技术配置 | 人类可读规则文本 |
| 受众 | 单个 Agent | 组织所有 Agent |
| 变更流程 | DevOps/配置变更 | `hivemind rules add/edit/done` |
| 典型例子 | 禁止 rm -rf / | "不要在 prod 凭证上跑 DROP TABLE" |

两者互补：tool permissioning 是硬边界（拒绝执行），跨 Agent 规则是软约束（注入上下文引导行为）。

---

## 关键设计细节

- **Codex 排除**：Codex 不接受 SessionStart 注入（保持 TUI 简洁），pi/OpenClaw 回退到 `hivemind context` 手动拉取
- **版本化**：每次编辑自增版本号，可追溯规则演变
- **组织级**：规则绑定 org，跨所有 workspace 生效

---

## 在 AI 知识体系中的位置

- **第 5 层（Agent 系统）**：规则是 harness 在 session 启动时加载的约束层，属于 agent 的"组织 policy"
- **第 7 层（产品与组织）**：规则的创建、编辑、关闭是组织治理行为——类比安全策略、合规要求、团队公约
- **桥接**：跨 Agent 规则系统是第 5 层（技术约束）和第 7 层（组织治理）之间的桥

---

## 关联

- [[entities/Hivemind]] — 唯一已知的工程实现
- [[concepts/ToolRiskPermissioning边界]] — 第 5 层 tool 级别的硬边界
- [[concepts/Agent共享记忆]] — 规则是共享记忆的一种特殊形态（组织级约束 vs 能力级知识）
