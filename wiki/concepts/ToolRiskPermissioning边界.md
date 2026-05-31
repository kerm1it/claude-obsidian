---
address: c-000324
type: concept
title: "Tool Risk / Permissioning 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - agents
  - tool-use
  - permissions
  - security
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/AgentHarness与TraceEval]]"
  - "[[concepts/DataRightsPrivacyConsent边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
  - "[[concepts/Skill与ToolMemory边界]]"
  - "[[concepts/ModelRoutingMixture边界]]"
  - "[[concepts/AISafetyOpsGovernance边界]]"
  - "[[concepts/MultiProviderGovernance边界]]"
  - "[[concepts/AgentIdentityDelegation边界]]"
  - "[[concepts/AIIncidentResponsePostmortem边界]]"
sources:
  - "[[sources/openai-agents-sdk-tool-guardrails-2026]]"
  - "[[sources/anthropic-computer-use-security-2026]]"
  - "[[sources/mcp-authorization-2025]]"
  - "[[sources/mcp-security-best-practices-2025]]"
  - "[[sources/owasp-llm-excessive-agency-2025]]"
  - "[[sources/nist-ai-agent-identity-authorization-2026]]"
  - "[[sources/aws-secure-agent-access-mcp-2026]]"
  - "[[sources/nsa-mcp-security-design-2026]]"
  - "[[sources/google-saif-controls-2026]]"
---

# Tool Risk / Permissioning 边界

Tool risk / permissioning 是第 5 层 Agent 系统层的动作权限边界：当模型从“回答”变成“调用工具、读写系统、执行代码、点击电脑、发邮件、改权限、付款、部署”时，系统必须先判断动作风险、权限范围、审批要求、凭证边界、审计和回滚路径。

一句话：**工具权限不是 prompt 约束；它是 agent runtime 外侧的动作准入系统。**

## 主归属

- 主归属：5. Agent 系统层
- 上游输入：用户意图、tool registry、tool schema、身份、凭证、数据权限、上下文风险、历史 trace
- 下游输出：allow / deny / ask approval / sandbox / dry-run / scoped credential / audit event
- 质量门：6. 评估与可靠性层
- 组织门：7. 产品与组织层

## 稳定链路

```text
proposed tool call
    -> intent and tool classification
    -> risk tier and data-scope check
    -> policy / permission / credential gate
    -> human approval or sandbox for high-risk actions
    -> execute with scoped authority
    -> trace, audit, rollback, and eval
```

## 风险分层

| 风险层 | 工具动作 | 默认权限策略 |
|---|---|---|
| R0 纯推理 | 不访问外部系统 | 直接执行 |
| R1 公开只读 | 搜索公开网页、读公开文档 | allowlist + citation |
| R2 私有只读 | 读组织文档、代码、工单、客户记录 | tenant 权限继承 + data rights |
| R3 可逆写入 | 创建草稿、写临时文件、开 staging PR | sandbox / dry-run / review |
| R4 外部副作用 | 发邮件、提交表单、创建订单、修改 CRM | human approval + audit |
| R5 高影响动作 | 支付、删除、部署、改权限、访问 secrets | 默认禁止或强审批 + scoped credentials |
| R6 通用执行 | shell、browser、computer use、代码执行 | dedicated VM/container + network/file allowlist |

## 与相邻概念区别

- 与 guardrails：guardrails 是检查机制；permissioning 是动作准入和授权机制。
- 与 agent identity / delegation：[[concepts/AgentIdentityDelegation边界]] 建立 actor、principal 和 delegation grant；tool permissioning 使用这些身份信号做动作准入。
- 与 tool use：tool use 是能力；tool risk 是对能力的风险分层和执行边界。
- 与 harness：harness 执行 agent loop；permissioning 是 harness 内必须经过的 policy gate。
- 与 data rights：[[concepts/DataRightsPrivacyConsent边界]] 决定数据能否被访问或发送；tool permissioning 决定动作能否被执行。
- 与 multi-provider governance：[[concepts/MultiProviderGovernance边界]] 决定外部模型、工具供应商和处理方是否可用；tool permissioning 决定具体 tool call 是否可执行。
- 与 eval：第 6 层 eval 测试工具选择、越权率、审批绕过和回滚；permissioning 在运行时阻止事故。
- 与 incident response：[[concepts/AIIncidentResponsePostmortem边界]] 消费工具事故 trace，反向调整风险层、approval、sandbox、credential 和 rollback 规则。
- 与 skill：skill 可以建议工具怎么用，但不能自行扩大工具权限。
- 与 governance：[[concepts/AISafetyOpsGovernance边界]] 定义哪些工具风险需要正式 owner、审批策略、事故响应和周期复审。

## 工程实践

1. 给每个工具标注风险层、数据域、可读/可写/可删能力、外部副作用和凭证需求。
2. 默认 least privilege：给 agent 专用身份，不复用人类管理员凭证。
3. 对高风险动作使用 human-in-the-loop approval，展示工具名、参数、资源、影响和回滚计划。
4. 用 scoped short-lived credentials、OAuth scopes、session policies 或 capability tokens，而不是长期全量 key。
5. 通用执行工具放进 dedicated VM/container，限制网络、文件系统、剪贴板、环境变量和 secrets。
6. 对 prompt injection 风险高的工具结果做隔离，外部网页/文档不能直接授权下一步写入或删除。
7. 每次工具调用都写 trace：actor、user intent、tool、arguments、policy decision、approval、result、resource。
8. 定期做 permission review，删除累积的未用权限和 shadow agents。
9. 将高风险 permission exception 进入 governance review，避免临时授权变成永久漏洞。

## 评估方式

- Tool-call precision：该调用时是否调用正确工具，不该调用时是否避免。
- Unauthorized-action rate：未授权读写、删除、发送、付款、部署是否被阻止。
- Approval quality：审批界面是否让人看懂影响，而不是机械点击。
- Sandbox escape：shell/browser/computer use 是否能访问不该访问的文件、网络或凭证。
- Prompt-injection resistance：外部网页、文档、tool result 是否能诱导越权动作。
- Audit completeness：能否重建每个动作的用户意图、权限、参数、结果和回滚。
- Blast radius：凭证泄露或工具中毒时可影响的资源范围。

## 过时风险

- 具体协议会变化，但“工具动作必须有外部准入边界”稳定。
- 模型越强，越能把多个低风险工具组合成高风险路径，所以组合权限和跨工具审计会更重要。
- 只靠 prompt 或模型自律会过时；身份、权限、沙箱、审批和审计是更稳定的工程边界。

## 一句话归类

Tool risk / permissioning 主属第 5 层 Agent 系统层，是 agent 从 reasoning 进入 action 前的动作准入层；它由第 6 层 eval/security 验证，并受第 7 层组织权限、数据权利和责任边界约束。
