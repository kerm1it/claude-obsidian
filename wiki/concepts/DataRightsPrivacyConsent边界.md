---
address: c-000313
type: concept
title: "Data Rights / Privacy / Consent 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - data-rights
  - privacy
  - consent
  - governance
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/ProductOrganizationLayer边界]]"
  - "[[concepts/DataFlywheelFeedbackLoop边界]]"
  - "[[concepts/RAG与Memory边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
  - "[[concepts/Skill与ToolMemory边界]]"
  - "[[concepts/ToolRiskPermissioning边界]]"
  - "[[concepts/AISafetyOpsGovernance边界]]"
  - "[[concepts/MultiProviderGovernance边界]]"
  - "[[concepts/AgentIdentityDelegation边界]]"
  - "[[concepts/SyntheticDataGovernance边界]]"
  - "[[concepts/DatasetLineageProvenanceGraph边界]]"
  - "[[concepts/DataDeletionUnlearningImpact边界]]"
  - "[[concepts/HumanFeedbackAnnotationOps边界]]"
  - "[[concepts/EvidenceMinimizationPrivacyPreservingAuditPacket边界]]"
sources:
  - "[[sources/openai-api-data-controls-2026]]"
  - "[[sources/openai-model-improvement-data-policy-2026]]"
  - "[[sources/anthropic-privacy-policy-2026]]"
  - "[[sources/anthropic-consumer-model-training-controls-2026]]"
  - "[[sources/anthropic-commercial-data-controls-2026]]"
  - "[[sources/google-vertex-ai-data-governance-2026]]"
  - "[[sources/eu-ai-act-data-governance-2024]]"
  - "[[sources/gdpr-data-subject-rights-2016]]"
  - "[[sources/eu-gdpr-article-5-data-minimization-storage-accountability-2016]]"
  - "[[sources/nist-privacy-framework-data-minimization-audit-log-2020]]"
  - "[[sources/nist-sp800-53-au3-pii-audit-record-minimization-2025]]"
  - "[[sources/nist-genai-profile-data-privacy-2024]]"
  - "[[sources/aws-secure-agent-access-mcp-2026]]"
  - "[[sources/eu-ai-act-risk-management-post-market-2024]]"
  - "[[sources/w3c-prov-overview-2013]]"
  - "[[sources/machine-unlearning-sisa-2019]]"
  - "[[sources/label-studio-annotation-quality-2026]]"
---

# Data Rights / Privacy / Consent 边界

Data rights / privacy / consent 是第 7 层产品与组织层的数据用途闸门：它决定一条真实使用数据能否被收集、保存、检索、用于服务运行、用于 memory/personalization、用于 eval/monitoring、用于模型改进或训练，以及用户或组织是否能访问、删除、导出、退出或限制用途。

一句话：**“数据能被本次请求使用”不等于“数据能被长期保存、进入记忆、进入 eval，或训练未来模型”。**

## 主归属

- 主归属：7. 产品与组织层
- 上游输入：用户内容、文件、反馈、agent trace、telemetry、组织知识、产品设置、法律/合同边界
- 下游输出：允许/禁止的 logging、retention、memory、RAG、eval、training、vendor sharing 和 deletion/export 流程
- 质量门：6. 评估与可靠性层
- 交叉层级：4. 上下文与知识层，8. 自我改进与前沿层

## 稳定链路

```text
user/org data or feedback
    -> purpose classification
    -> consent / contract / policy check
    -> minimization and redaction
    -> allowed use path
    -> retention / deletion / export controls
    -> audit trail and periodic review
```

## 数据用途矩阵

| 数据用途 | 典型例子 | 需要的边界 |
|---|---|---|
| 本次服务运行 | 用 prompt、文件或工具结果回答当前请求 | 会话权限、最小化、tool/vendor 传输边界 |
| 安全与滥用监测 | 检测攻击、欺诈、政策违规 | 合理保留期、访问控制、审计 |
| 产品 telemetry | 成功率、延迟、成本、接受/拒绝 | 聚合、去标识、反作弊、退出或合同边界 |
| Memory / personalization | 用户偏好、组织惯例、长期目标 | 用户可见、可编辑、可删除、可关闭 |
| RAG / knowledge base | 公司文档、政策、产品手册 | 文档权利、权限继承、tenant isolation |
| Eval / regression | 失败案例、人工修正、trace | 数据集权限标签、脱敏、hold-out 隔离 |
| Model improvement / training | SFT、RLHF、蒸馏、router 训练 | 明确授权、来源追踪、删除影响策略 |
| Vendor / subprocessor | 多模型路由、外部工具、云服务 | DPA、数据出境、保留期、二次使用限制 |

## 与相邻概念区别

- 与 [[concepts/DataFlywheelFeedbackLoop边界]]：data flywheel 定义信号去哪里；data rights 定义信号是否允许去那里。
- 与隐私政策：隐私政策是组织承诺；本页关注 AI 系统中可执行的数据用途决策。
- 与安全：安全关注访问和攻击；privacy/consent 关注目的、权利、最小化和期限。
- 与 RAG / memory：RAG 和 memory 是第 4 层知识机制；它们必须继承用户、组织和文档权限。
- 与 agent identity / delegation：[[concepts/AgentIdentityDelegation边界]] 把用户、租户、agent 和 task delegation 带入每次访问；本页判断这些主体能否使用或保留数据。
- 与 eval：eval 可以消费真实失败样本，但样本要带权限标签、脱敏策略和 hold-out 边界。
- 与训练：训练是最强用途，因为删除、溯源和跨用户影响最难，必须比服务运行和 eval 有更高门槛。
- 与 synthetic data governance：[[concepts/SyntheticDataGovernance边界]] 判断合成样本能否使用；本页判断 seed data、prompt、teacher output 和生成样本是否仍受权利、隐私和 consent 限制。
- 与 tool permissioning：[[concepts/ToolRiskPermissioning边界]] 决定动作能否执行；本页决定动作涉及的数据能否被访问、传输或保留。
- 与 multi-provider governance：[[concepts/MultiProviderGovernance边界]] 把本页的数据用途、保留和地域要求映射到具体 provider、model、feature 和 subprocessor。
- 与 governance：[[concepts/AISafetyOpsGovernance边界]] 把 data rights 例外、删除失败、泄露事件和审计缺口纳入 risk register 和 incident response。
- 与 dataset lineage：[[concepts/DatasetLineageProvenanceGraph边界]] 提供来源、授权、保留、split、下游影响和删除路径证据；本页决定这些证据代表的用途是否允许。
- 与 data deletion / unlearning impact：[[concepts/DataDeletionUnlearningImpact边界]] 执行删除、限制、匿名化、重训或 unlearning；本页定义请求、权利、例外和用途依据。
- 与 human feedback / annotation ops：[[concepts/HumanFeedbackAnnotationOps边界]] 可能把用户内容、trace 或高风险样本发给人工标注员、专家或供应商；本页定义这些数据能否被查看、保留、导出、训练或跨境处理。
- 与 evidence minimization / privacy-preserving audit packet：[[concepts/EvidenceMinimizationPrivacyPreservingAuditPacket边界]] 是本页在 audit/evidence 用途上的具体落点，负责把最小化原则变成字段矩阵、private annex、选择性披露和处置记录。

## 工程实践

1. 给每条事件打用途标签：service、safety、analytics、memory、eval、training、vendor。
2. 给每条数据保存 provenance：来源、主体、组织、时间、权限、保留期、模型/工具版本和处理目的。
3. 默认最小化：能不收集就不收集，能脱敏就脱敏，能聚合就不保留原文。
4. 区分用户、组织和 public/owned data；企业租户默认不能被跨客户使用。
5. Memory 必须可见、可关、可删；不要把 memory 与训练数据混在一起。
6. Eval 数据集要保存 permission tag，防止未授权样本进入训练或公开 benchmark。
7. 多 provider 路由前先检查数据能否发送给该 provider、地域、子处理方和保留策略。
8. 设计 data subject request 流程：访问、删除、导出、纠正、退出模型改进；删除请求进入 [[concepts/DataDeletionUnlearningImpact边界]] 后再查询下游影响和验证完成。
9. 工具动作继承数据权限：只读客户记录、发送邮件、调用 MCP server、上传文件和执行 shell 都要检查数据用途边界。

## 评估方式

- Consent coverage：训练/eval/memory 样本是否都有可审计授权。
- Deletion/export test：删除、导出、关闭 memory 是否真实生效；涉及模型影响时是否触发 retraining、replacement、unlearning 或记录例外。
- Retention enforcement：过期数据是否自动清理，备份和下游数据集是否同步。
- Tenant isolation：A 组织数据是否影响 B 组织检索、记忆、router 或模型行为。
- Leakage tests：prompt injection、tool logs、RAG citation、模型输出是否泄露个人或组织数据。
- Data lineage：能否从模型改进样本追溯到来源、用途和授权状态。
- Privacy impact review：新数据路径是否经过 DPIA、风险评估或同等审查。

## 过时风险

- 法律、平台条款和供应商默认设置会变化；本页的稳定部分是用途分层、权限标签和审计链路。
- “匿名化/聚合”不是魔法护身符，重识别风险和小样本泄露仍要评估。
- 更强模型会提高从少量上下文中推断敏感信息的能力，因此最小化和隔离会更重要。
- 跨 provider 路由、agent 工具调用和 long-term memory 会持续扩大数据边界，必须定期复审。

## 一句话归类

Data rights / privacy / consent 主属第 7 层，是产品组织层的数据用途治理接口；它通过第 6 层审计和质量门约束第 4 层 memory/RAG、第 6 层 eval、第 8 层 self-improvement 和第 2 层训练。
