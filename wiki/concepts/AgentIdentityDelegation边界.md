---
address: c-000360
type: concept
title: "Agent Identity / Delegation 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - agents
  - identity
  - authorization
  - delegation
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/ToolRiskPermissioning边界]]"
  - "[[concepts/DataRightsPrivacyConsent边界]]"
  - "[[concepts/AISafetyOpsGovernance边界]]"
  - "[[concepts/MultiProviderGovernance边界]]"
  - "[[concepts/AIIncidentResponsePostmortem边界]]"
sources:
  - "[[sources/nist-ai-agent-identity-authorization-2026]]"
  - "[[sources/mcp-authorization-2025]]"
  - "[[sources/mcp-security-best-practices-2025]]"
  - "[[sources/aws-secure-agent-access-mcp-2026]]"
  - "[[sources/nsa-mcp-security-design-2026]]"
  - "[[sources/ietf-agent-identity-protocol-draft-2026]]"
---

# Agent Identity / Delegation 边界

Agent identity / delegation 是第 5 层 Agent 系统层的行动者身份边界：当 agent 代表用户、组织、另一个 agent 或服务执行工具动作时，系统必须能回答“谁在行动、代表谁、基于哪次授权、权限范围是什么、多久过期、如何撤销、如何审计”。

一句话：**identity 说明谁在行动；delegation 说明谁授权它行动；permissioning 决定这次动作能不能执行。**

## 主归属

- 主归属：5. Agent 系统层
- 上游输入：用户/组织 principal、任务授权、agent run、tool registry、data rights、policy、credential issuer
- 下游输出：agent identity、delegation grant、scoped credential、step-up authorization、audit event、revocation path
- 组织接口：7. 产品与组织层
- 质量门：6. 评估与可靠性层

## 稳定链路

```text
human / org / service principal
    -> delegation grant for task / workflow
    -> agent identity or run identity
    -> scoped short-lived credential / capability
    -> tool or provider request
    -> policy decision: allow / deny / step-up / approval
    -> audit trail and non-repudiation evidence
    -> revoke, rotate, review, or incident response
```

## 解决的问题

没有 agent identity，系统只能看到“某个人的 API key”或“一个万能服务账号”在行动。这样会产生三类失败：agent 和人类动作无法区分、agent 继承过宽权限、事故后无法还原委托链。多 agent 场景还会出现权限叠加、身份漂白和责任主体消失。

## 核心对象

| 对象 | 作用 |
|---|---|
| Principal | 授权主体，可以是用户、组织、服务、团队或上级 agent |
| Agent identity | 可识别的 agent / agent run / workload 身份，不能只复用人类身份 |
| Delegation grant | principal 对某个任务、时间窗、资源和动作范围的授权 |
| Scope / policy | 具体允许的工具、资源、数据、地域、风险等级和操作 |
| Credential | 短期 token、session、capability、role session 或 mTLS/OAuth 凭证 |
| Step-up authorization | 低风险先执行，高风险再增量授权或人工审批 |
| Audit event | actor、principal、grant、tool、resource、decision、result、trace id |
| Revocation | 取消 agent、grant、token、session、tool access 或 provider access |

## 与相邻概念区别

- 与 [[concepts/ToolRiskPermissioning边界]]：identity/delegation 建立“谁和凭什么”；tool permissioning 判断“这次动作能不能做”。
- 与 [[concepts/DataRightsPrivacyConsent边界]]：data rights 判断数据用途是否允许；delegation 把权限主体、租户和数据范围带入每次请求。
- 与 [[concepts/MultiProviderGovernance边界]]：provider governance 判断 provider 是否可用；identity/delegation 说明外部 provider 看到的是哪个应用、agent、租户或代表关系。
- 与 service account：service account 是实现选项；agent identity 需要更细的任务、时间、scope、principal 和审计绑定。
- 与 OAuth / IAM：OAuth、IAM、session tags、capability token 是机制；本概念是 agent 系统里的身份和委托边界。
- 与 [[concepts/AISafetyOpsGovernance边界]]：safety ops 负责 owner、exception 和 incident；agent identity 提供事故调查和责任追踪证据。
- 与 [[concepts/AIIncidentResponsePostmortem边界]]：事故响应用 agent identity / delegation 还原 actor、principal、grant、scope 和 revoke path。

## 工程实践

1. 给 agent 或 agent run 分配可追踪身份，不让所有动作都表现成同一个人类账号。
2. 每次授权都绑定 principal、task、scope、resource、expiry、risk tier 和 revocation path。
3. 使用短期、最小权限凭证；避免长期 API key、wildcard scope 和 full-access service account。
4. 对高风险工具使用 step-up authorization 或 human approval，并把 approval 与具体参数绑定。
5. 对 MCP / tool server 使用 audience-bound token，不做 token passthrough。
6. 在云资源侧用 session tags、condition keys、role session name 或等价机制区分 AI-driven 和 human-initiated actions。
7. 记录完整 audit event：agent id、run id、principal、grant id、tool、resource、policy decision、result、trace。
8. 对 multi-agent delegation 做权限衰减：子 agent 不得自动继承父 agent 的全量权限。
9. 给 agent 身份、token 和 delegation grant 提供 revoke / rotate / kill switch。

## 评估方式

- Attribution completeness：每个 tool call 是否能追溯到 agent、principal、grant、scope 和 trace。
- Over-privilege rate：agent 拿到的权限是否超过当前任务需要。
- Impersonation failure rate：系统是否能区分 agent、human、service 和代理调用。
- Step-up precision：增量授权是否只在需要时触发，且不被绕过。
- Revocation latency：撤销 grant/token/agent 后多久生效。
- Audit reconstruction time：事故后能否快速还原谁授权、做了什么、影响哪些资源。
- Confused deputy tests：代理、MCP server、第三方工具是否能被诱导代替攻击者拿权限。
- Direct-path bypass：bash、shell、browser、SDK 是否绕过 MCP/IAM 差异化控制。

## 过时风险

- NIST、MCP、IETF draft、云厂商 IAM 对 agent identity 的标准仍在快速变化；具体协议名会变。
- 稳定部分是 actor / principal / delegation / scope / audit / revocation 这条链。
- 如果模型能力继续增强，单个 agent 组合多个低风险权限形成高风险路径的概率上升，委托衰减和组合审计会更重要。

## 一句话归类

Agent identity / delegation 主属第 5 层，是 agent 从 reasoning 进入 tool action 前的身份和委托边界；它把第 7 层的责任主体和授权策略带入第 5 层 runtime，再由第 6 层 eval/security 验证。
