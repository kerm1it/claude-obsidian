---
address: c-000574
type: concept
title: "Memory / Skill Governance Drift 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - memory
  - agent-skills
  - governance
  - drift
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/RAG与Memory边界]]"
  - "[[concepts/Skill与ToolMemory边界]]"
  - "[[concepts/SkillLibraryRouting生命周期]]"
  - "[[concepts/SelfImprovementGateChangeRiskBudget边界]]"
  - "[[concepts/DataRightsPrivacyConsent边界]]"
  - "[[concepts/DataQualityLabelQuality边界]]"
  - "[[concepts/ToolRiskPermissioning边界]]"
  - "[[concepts/DatasetLineageProvenanceGraph边界]]"
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

# Memory / Skill Governance Drift 边界

Memory / skill governance drift 是第 4 层上下文与知识层的长期知识治理边界：它管理 persistent memory、RAG-derived memory、skill packages、SKILL.md metadata、workflow hints 和 procedural knowledge 在长期写入、巩固、路由、更新、共享和退役过程中产生的过时、投毒、权限漂移、路由漂移和不可解释更新。

一句话：**memory 和 skill 不是静态笔记；它们是会改变未来 agent 行为的 operational context，必须像可执行资产一样治理。**

## 主归属

- 主归属：4. 上下文与知识层
- 运行时接口：5. Agent 系统层
- 质量与安全门：6. 评估与可靠性层
- 权限与组织接口：7. 产品与组织层
- 自我改进接口：8. 自我改进与前沿层
- 上游输入：trace、user feedback、dream output、memory write、skill update、tool outcome、RAG corpus、expert curation
- 下游输出：approved memory、quarantined memory、skill version、routing metadata、deprecation record、delete/forget action、regression eval

## 稳定链路

```text
memory / skill artifact inventory
    -> owner, scope, tenant, permission, source, version, and expiry labels
    -> write/update proposal from user, agent, dream, feedback, or curator
    -> provenance, rights, freshness, conflict, security, and routing checks
    -> drift classification: stale, poison, permission drift, routing drift, dependency/API drift, duplicate, orphan, overbroad
    -> action: admit, scope, quarantine, rewrite, split, merge, deprecate, delete, or retire
    -> retrieval/routing regression eval and runtime monitoring
    -> self-improvement gate for automated updates
    -> audit trail and periodic review
```

## 漂移类型

| 漂移类型 | 发生对象 | 典型风险 |
|---|---|---|
| Stale memory | memory / RAG-derived memory | 旧事实、旧偏好或旧环境覆盖当前状态 |
| Conflict drift | memory graph / summaries | 多条记忆冲突但被合并成错误结论 |
| Sleeper poisoning | memory | 外部网页、文档、repo 或工具结果诱导 agent 写入休眠恶意记忆 |
| Tool-selection hijack | memory + tool use | 被投毒记忆让 agent 自主选择攻击者偏好的工具 |
| Permission drift | memory / skill references | 私有用户/租户/项目内容进入共享 memory 或 skill |
| Routing drift | SKILL.md metadata / descriptions | metadata 让错误 skill 被召回、选择或绕过 governance |
| Dependency drift | scripts / tools / APIs | skill 依赖、API、环境或工具权限变化后旧 skill 仍被信任 |
| Update drift | self-improvement updates | 自动更新把一次偶然成功固化为长期知识 |
| Orphan drift | ownerless memory / skill | 没有 owner、expiry、review 的知识长期影响行为 |
| Overbroad skill | skill package | 一个 skill 包含太多任务，造成误召回、权限扩大和难以回归 |

## 与相邻概念区别

- 与 [[concepts/RAG与Memory边界]]：RAG/memory 边界区分事实检索和主体连续性；本页治理 memory 长期写入、冲突、污染、权限和退役。
- 与 [[concepts/Skill与ToolMemory边界]]：skill/tool/memory 边界区分对象；本页治理这些对象长期漂移后如何准入、隔离、更新和删除。
- 与 [[concepts/SkillLibraryRouting生命周期]]：skill library lifecycle 管 collection/recommendation/evolution；本页把 memory 与 skill 放到同一个 operational context 治理边界中，重点处理 drift。
- 与 [[concepts/SelfImprovementGateChangeRiskBudget边界]]：self-improvement gate 决定自动 diff 是否可落地；本页定义 memory/skill diff 应该检查哪些漂移和风险。
- 与 [[concepts/DataRightsPrivacyConsent边界]]：data rights 判断能不能记、能不能共享、能不能训练；本页执行这些标签在 memory/skill 生命周期中的继承、删除和审计。
- 与 [[concepts/ToolRiskPermissioning边界]]：tool permissioning 管一次工具调用；本页防止 memory/skill 长期影响工具选择和权限路径。

## 工程规则

1. 每条 memory 和每个 skill 都要有 owner、scope、source、created_at、updated_at、expiry/review_at、permission tag 和 version。
2. Memory 写入要分层：raw memory、candidate memory、consolidated memory、trusted memory，不把单次观察直接升为长期事实。
3. Skill metadata 是 routing surface，不是普通说明文字；description、tags、trigger、examples 都要做语义安全和路由回归。
4. Dream / consolidation 应输出新 memory store 或 diff，不能静默覆写唯一真相源。
5. 共享 memory 和共享 skill 默认更严格：必须证明没有 tenant leak、secrets、private examples 和越权 tool assumptions。
6. 对 skill 脚本、references 和依赖做版本锁定、hash、sandbox、allowed tools、network/file scope 和 dependency review。
7. 对长期 memory 做 poisoning scan、conflict resolution、staleness decay、source trust scoring 和 retrieval audit。
8. 对 skill 更新做 routing eval、task regression、security scan、environment compatibility 和 deprecation plan。
9. 自动 memory/skill 更新必须经过 [[concepts/SelfImprovementGateChangeRiskBudget边界|self-improvement gate]]，尤其不能自动扩大权限或修改共享 skill。

## 评估方式

- Memory write precision：写入的长期记忆是否真的值得长期保留。
- Stale retrieval rate：被检索并影响行为的过时 memory 比例。
- Poison write/retrieve/use rate：恶意或错误 memory 是否被写入、检索并改变行动。
- Conflict resolution accuracy：冲突记忆是否被正确保留、合并、标记或废弃。
- Skill routing precision/recall：该用 skill 时能召回，不该用时不误召回。
- Semantic supply-chain resistance：metadata-only 攻击是否能提高恶意 skill visibility、selection 或绕过 governance。
- Permission violation rate：memory/skill 是否跨用户、租户、项目或 provider 边界泄露。
- Update regression：memory/skill 更新后旧任务、工具选择、安全边界和成本是否退化。
- Quarantine/rollback time：发现投毒、过期、越权或错误 skill 后多久能隔离和回退。

## 过时风险

- 具体 memory store、skill registry 和 agent platform 会变，但 persistent operational context 的治理问题稳定存在。
- 长上下文会减少部分检索需求，但不会消除“什么值得长期记、谁能看、何时忘、如何防投毒”的问题。
- 更强模型会更擅长利用 memory/skill，也更可能被被污染的长期上下文长期牵引。

## 一句话归类

Memory / skill governance drift 主属第 4 层，是长期外部知识和程序性知识在写入、路由、共享、更新和退役时的漂移治理边界；它通过第 6 层 eval/security gate 和第 8 层 self-improvement gate，防止 memory 与 skill 从能力资产变成长期污染源。
