# 方向、市场与能力矩阵

更新时间：2026-08-11。

## 1. 北极星岗位

主目标不是一个固定职位名，而是一组相邻岗位：

| 岗位族 | 主要交付 | 最关键能力 | 适合作为目标 |
|---|---|---|---|
| Agent Platform / Harness Engineer | 让不同 Agent 安全、稳定、低成本运行的平台 | 分布式系统、runtime、sandbox、identity、observability、evals | 主线 |
| Applied AI / Agent Engineer | 将业务问题变成可用 Agent 产品 | LLM、RAG、tool use、产品判断、全栈和实验 | 主线 |
| Agent Evals / Quality Engineer | 定义、测量并改善 Agent 行为 | eval 设计、统计、grader、trace 分析、数据 | 强副线 |
| AI Safety / Security Engineer | 限制 Agent 风险和权限 | threat modeling、authz、隔离、prompt injection、审计 | 强副线 |
| ML Systems / Inference Engineer | 模型训练、推理和 GPU 系统 | PyTorch、CUDA、serving、量化、性能 | 可选深挖 |
| Forward Deployed AI Engineer | 在客户现场交付端到端系统 | 快速产品化、云、沟通、领域建模 | 很好的就业入口 |
| Domain Agent Engineer | 金融、医疗、法律、工业等垂直 Agent | 领域知识、规则、可解释性、合规 | 差异化路线 |

建议形成 **T 型能力**：横向覆盖完整 Agent 系统，纵向选择“Harness/Evals”或“金融领域/安全”之一。

## 2. 为什么主线是工程系统，而不是框架

2026 年岗位样本的交集非常稳定：

- AWS 的 Agentic AI 岗位要求控制面、数据面、managed agent loop、工具编排、状态、隔离、identity、观测、版本、灰度、回滚、评测和成本控制。
- Google 的 AI Agents 岗位同时要求常规软件工程、ADK/GCP、MLOps、RAG、MCP、多 Agent、安全与可靠性。
- JPMorganChase 把 Python/Java/React、API、Kafka、Docker/Kubernetes、可解释结果、网络安全和受控工具调用放在同一工程体系中。
- NVIDIA 的 Agent 工具强调跨框架 profiling、可靠性、工具效率和成本，而不只关注某个编排库。
- xAI 的公开申请把 GitHub 和“最杰出的工作”作为核心信号，说明可证明的工程作品比证书堆叠更有辨识力。

结论：**模型和框架是依赖项，harness、eval、数据、可靠性、安全和工程判断才是产品护城河，也是长期职业资产。**

## 3. 能力模型

每项采用 0–4 级：

- L0：不了解
- L1：能解释和完成教程
- L2：能独立实现并测试
- L3：能上线、测量、诊断和权衡
- L4：能设计平台、制定标准、带人并推动跨团队决策

| 维度 | 6 个月目标 | 12 个月目标 | 资深岗位信号 |
|---|---:|---:|---|
| 软件工程：Python/TS、测试、API、Git | L3 | L3 | 大型代码库、review、工程规范 |
| CS 基础：DSA、网络、OS、数据库 | L2 | L3 | 系统设计中正确选型和权衡 |
| ML/LLM 基础 | L2 | L3 | 能解释 failure、训练/推理和优化边界 |
| Agent primitives | L3 | L4 | 可手写 loop、state machine、tool contract |
| RAG / Context / Memory | L3 | L3 | 数据质量、检索 eval、长期记忆策略 |
| Harness / Runtime / Distributed systems | L2 | L3 | 隔离、恢复、伸缩、幂等、durable execution |
| Evals / Observability | L3 | L4 | outcome/trajectory、grader 校准、线上闭环 |
| Security / Governance | L2 | L3 | least privilege、approval、审计、威胁模型 |
| Cloud / LLMOps | L2 | L3 | SLO、CI/CD、灰度、成本、容量 |
| Product / Domain / Communication | L2 | L3 | 模糊问题拆解、指标、英文设计文档和影响力 |

在 `TRACKER.md` 每月评分一次。评分必须链接证据，不能凭感觉上涨。

## 4. 各目标公司的“准备角度”

### Microsoft

- Python 与 C# 至少一门强项；企业集成、Azure、identity 和治理。
- 学习当前 Microsoft Agent Framework，而不是把 AutoGen/Semantic Kernel 的旧 API 当终点。
- 展示 workflow、durable execution、A2A/MCP、hosted agent、可观测和企业权限边界。
- 面试仍需扎实的软件工程、编码和系统设计。

### Amazon / AWS

- 最重视大规模分布式系统、ownership、operational excellence 和客户导向。
- 作品应有 control plane/data plane、session state、异步队列、tenant isolation、SLO、成本控制和 rollback。
- 准备 Leadership Principles 的 STAR 案例；每个案例量化影响并写清取舍。

### Google / DeepMind

- DSA、系统设计、ML 基础和工程质量不能因“会 Agent”而减配。
- 重点覆盖 ADK/GCP/MLOps、RAG、MCP、多模态、quality eval 和大规模系统。
- 展示严谨实验：数据切分、误差分析、指标置信度、可复现实验。

### NVIDIA

- 路线 A：企业 Agent、RAG、profiling、NIM/NeMo Agent Toolkit、GPU-aware serving。
- 路线 B：更深的 ML systems、PyTorch、CUDA、推理优化、量化和性能分析。
- 至少做一次 GPU profiling；不要只在 SDK 顶层停留。

### JPMorganChase

- Python/Java、React、API、Kafka、数据库、Docker/Kubernetes、云和安全工程是一体的。
- 差异化来自金融领域、可解释性、审计、数据治理、模型风险、human-in-the-loop。
- Capstone 应能展示：规则与概率模型如何共存、敏感数据如何隔离、决策如何被追溯。

### xAI

- 公开岗位强调 exceptional engineering、主动性、直接贡献和简洁准确的沟通。
- 最重要的求职资产是一个难度明显、数据真实、公开可验证的代表作，以及 100 词内说明“为什么杰出”。
- 增强算法、系统底层、性能和独立解决陌生问题的能力。

## 5. 2026–2030 职业趋势判断

### 高确定性趋势

1. **Agent 从应用功能变成平台能力。** identity、memory、sandbox、observability、versioning、policy 和 cost control 会成为标准组件。
2. **Harness engineering 的价值上升。** 同一个模型放进不同工具、环境、上下文管理和反馈循环，结果可以显著不同。
3. **Eval-driven development 成为 Agent 工程的单元测试。** 靠 demo 和直觉无法安全迭代非确定性系统。
4. **协议与互操作性进入主流。** MCP 解决 Agent 与工具/资源连接，A2A 解决独立 Agent 间发现、任务和协作；协议安全会成为必修课。
5. **单 Agent + 确定性 workflow 会长期存在。** 多 Agent 不是默认答案；只有并行、隔离专长或独立验证带来可测收益时才增加复杂度。
6. **Agentic coding 改变工程师工作内容。** 稀缺能力从逐行写代码部分转向规范意图、设计环境、建立反馈回路、review 和系统判断，但深厚编码能力仍用于验证和处理边界问题。
7. **领域和合规成为溢价。** 金融、医疗、工业和安全团队需要 auditability、可解释性、数据边界与业务规则，而非通用聊天界面。
8. **成本、延迟、能耗和模型路由成为架构问题。** 大模型、轻量模型、缓存、批处理、并行和本地推理需要通过 eval 做选择。
9. **多模态与 computer use 扩大 Agent 的动作空间，也扩大攻击面。** sandbox、权限、确认和 outcome validation 更重要。

### 职业风险

- 只会 prompt 和框架胶水：最容易被模型能力和框架升级替代。
- 只做玩具 demo：没有真实数据、异常路径、评测、监控和部署，无法证明生产能力。
- 框架收藏癖：同时浅学十个库，不如手写一次 loop，再深入一个框架并比较另一个。
- 忽略传统 CS：目标公司仍然筛选算法、系统设计、数据库、网络、并发和代码质量。
- 把自主性当目标：业务要的是可控结果；确定性、审批和安全常比“更 autonomous”重要。
- 只投 `Agent Engineer` 标题：相关岗位也会叫 Applied AI、AI Platform、ML Systems、GenAI、Forward Deployed、Developer Productivity 或 Software Engineer, AI/ML。

### 耐久职业组合

最稳健的组合是：

```text
强软件工程
+ LLM/Agent 原理
+ Harness/Evals/Security
+ 一个领域或系统纵深
+ 使用 AI 大幅提高自身交付速度
+ 清晰的英文技术沟通
```

## 6. 学历、证书与开源的优先级

- 本科或同等实践经验通常是基础门槛；研究型岗位更偏好硕博，但产品/平台工程可以用强作品和经历替代部分学历信号。
- 证书只用于建立学习结构或通过 HR 关键词，不应超过总学习时间的 5–10%。
- 开源贡献优先选择：修 bug、加 eval、完善 tracing/security、写真实 benchmark；“新增一个 wrapper”价值较低。
- 两篇有实验数据的技术文章，通常优于二十篇概念复述。

## 7. 目标校准

从零开始在 12 个月内直接达到“大厂内部 Senior”职级通常不现实；Senior 通常还要求多年生产责任和跨团队影响。本路线的现实目标是：

- 技术能力达到可与中级 Agent Engineer 竞争；
- 作品和系统设计呈现部分 senior-caliber 信号；
- 若已有 3–8 年软件/ML 经历，把这些能力叠加到既有资历上，直接竞争 senior 更合理；
- 若是转行者，先进入 Applied AI、AI Platform、FDE 或后端 AI 团队，再用 18–36 个月生产影响升级。
