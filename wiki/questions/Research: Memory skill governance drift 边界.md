---
address: c-000575
type: question
title: "Research: Memory skill governance drift 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - research
  - memory
  - agent-skills
  - governance
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/MemorySkillGovernanceDrift边界]]"
  - "[[concepts/RAG与Memory边界]]"
  - "[[concepts/Skill与ToolMemory边界]]"
sources:
  - "[[sources/openai-agent-memory-2026]]"
  - "[[sources/anthropic-dreams-docs-2026]]"
  - "[[sources/skillsvote-2026]]"
  - "[[sources/under-the-hood-skill-md-2026]]"
  - "[[sources/secure-agent-skills-2026]]"
  - "[[sources/agent-skills-wild-security-2026]]"
  - "[[sources/memmorph-tool-hijacking-memory-poisoning-2026]]"
  - "[[sources/poison-once-exploit-forever-memory-poisoning-2026]]"
  - "[[sources/hidden-in-memory-sleeper-poisoning-2026]]"
  - "[[sources/shadowmerge-graph-memory-poisoning-2026]]"
  - "[[sources/memory-poisoning-attack-defense-llm-agents-2026]]"
---

# Research: Memory skill governance drift 边界

## 研究问题

第 4 层已经区分了 RAG、memory 和 skill，但长期运行后会出现新问题：memory 会过时、被投毒、跨权限泄露；skill 会因为 metadata、脚本、依赖和路由变化而漂移。问题不是“要不要记忆/技能”，而是：**长期 operational context 如何治理，才不会把过去的错误固化为未来的行为？**

## 稳定定义

Memory / skill governance drift 是 persistent memory 与 skill library 的长期治理边界。它把 memory entry、memory graph relation、skill package、SKILL.md metadata、scripts、references 和 routing hints 当作会影响未来 agent 行为的 versioned operational artifacts，要求它们具备 owner、scope、permission、provenance、freshness、eval、rollback、quarantine 和 retirement。

## 来源综合

- OpenAI Agents SDK memory 文档强调 summary、index、detailed summaries 的分层读取，并说明 memory 需要反映最新环境，过旧 raw memories 会被压缩或遗忘。
- Claude Managed Agents memory/dreaming 强调 workspace-scoped、observable memory，以及 dream 生成独立 output memory store，便于审查、替换或丢弃。
- SkillsVote 说明 skill library 需要 collection、recommendation、evolution 的生命周期治理；更新必须做 outcome attribution 和 evidence-gated admission。
- Under the Hood of SKILL.md 证明 SKILL.md metadata 不是被动文档，而是影响 discovery、selection 和 governance 的 operational text。
- Secure Agent Skills 与 Agent Skills in the Wild 说明 skill 的创建、分发、部署、执行各阶段都有供应链和权限攻击面。
- MemMorph、Hidden in Memory、Poison Once Exploit Forever、ShadowMerge 和 Memory Poisoning Attack and Defense 共同说明 persistent memory 是长期攻击面：攻击可通过环境观察、外部文档、图关系冲突或少量 crafted records 改变后续工具选择和行为。

## 分层归属

- 主归属：4. 上下文与知识层
- 运行时：5. Agent 系统层
- 质量/安全：6. 评估与可靠性层
- 权限/审计：7. 产品与组织层
- 自动更新：8. 自我改进与前沿层

它不是第九层，而是第 4 层长期知识资产进入可复用、可共享、可自动更新后必须补上的治理边界。

## 边界结论

1. **Memory 和 skill 都是 operational context，不是普通笔记。**
2. **写入和检索都要治理**：只检查写入不够，过时或投毒内容可能在未来被检索并激活。
3. **Metadata 是安全面**：skill description、trigger、tags 会影响 retrieval/selection/governance，必须回归测试。
4. **共享范围决定风险等级**：个人 memory、项目 memory、组织 memory、公共 skill registry 的准入门槛不同。
5. **Dream / self-improvement 只能生成 candidate diff**：长期 memory/skill 更新必须经过 drift checks 和 self-improvement gate。
6. **删除、退役和 quarantine 与新增同等重要**：没有退役机制的 memory/skill 库会积累隐性债务。

## 工程模板

| 字段 | Memory | Skill |
|---|---|---|
| Identity | memory id、source trace、scope | package id、version、hash |
| Scope | user、project、workspace、org、tenant | personal、team、org、public |
| Provenance | session、tool、document、agent、dream | author、repo、review、source trace |
| Permission | 可见、可删、可共享、可训练 | allowed tools、file/network scope、secret policy |
| Freshness | observed_at、valid_until、superseded_by | API/dependency/env compatibility |
| Quality | conflict/stale/poison scan | routing eval、task regression |
| Action | admit、quarantine、forget、merge、split | admit、pin、deprecate、retire、rollback |

## Open Questions

- 如何在不牺牲可用性的情况下设置 memory write threshold？过严会失去连续性，过松会放大投毒。
- Graph memory 的 conflict resolution 是否能被形式化验证？目前 ShadowMerge 显示输入侧过滤不足。
- Skill semantic governance 如何避免误杀合法安全文本？metadata-only 攻击和合法说明之间的边界仍需要基准和人类审查。

## 回填位置

- [[domains/AI知识体系]] 第 4 层新增 memory / skill governance drift。
- [[concepts/RAG与Memory边界]] 增加长期 memory governance。
- [[concepts/Skill与ToolMemory边界]] 增加 skill 生成/更新的 drift gate。
- [[concepts/SkillLibraryRouting生命周期]] 增加 drift、quarantine、retirement 和 semantic supply-chain 回归。
- [[concepts/SelfImprovementGateChangeRiskBudget边界]] 增加 memory/skill diff 的 target checks。

## 结论

本轮把第 4 层从“怎么取知识/经验”推进到“长期知识如何不漂移”。Memory 和 skill 提升 agent 连续性与复用能力，但一旦被长期信任，就会变成可持久影响未来行为的控制面。因此它们必须有 owner、scope、permission、provenance、freshness、eval、quarantine 和 retirement。
