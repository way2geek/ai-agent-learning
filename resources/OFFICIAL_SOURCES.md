# 官方资料与岗位样本

最后核验：2026-08-11。技术 API、协议和岗位会变化；每季度刷新。优先读官方文档、原始论文和源代码，不把二手教程当规范。

## 1. 2026 年路线依据

### 岗位样本

- [AWS — Software Development Engineer, AWS Agentic AI](https://amazon.jobs/en/jobs/10486378/software-development-engineer-aws-agentic-ai)：control/data plane、managed agent loops、context/memory、identity、isolation、observability、eval、version/rollback、成本与大规模分布式系统。
- [Google — Software Engineer III, AI Agents](https://www.google.com/about/careers/applications/jobs/results/102213703012623046-software-engineer-iii-ai-agents)：Python/C++、ADK、GCP、MLOps、RAG、MCP、多 Agent、安全、可靠性。
- [JPMorganChase — Software Engineer Program role examples](https://www.jpmorganchase.com/careers/explore-opportunities/programs/software-engineer-summer)：Python/Java/React、Kafka、Docker/Kubernetes、secure API、Agent 工具调用、可解释性、AIOps 和 AI 安全。
- [NVIDIA — Senior Software Engineer, Agentic AI](https://nvidia.wd5.myworkdayjobs.com/en-US/NVIDIAExternalCareerSite/job/Senior-Applied-LLM-Engineer--AI---Chip-Design_JR1989138)：Applied LLM 与 Agentic AI 示例岗位；Workday 链接可能随招聘状态失效。
- [Microsoft AI Careers](https://microsoft.ai/careers/)：当前 Microsoft AI 岗位入口；具体岗位每季度重新采样。
- [xAI Careers](https://x.ai/careers)：公开强调 technical team review、GitHub/代表作和 exceptional engineering；申请流程与岗位会变化。

岗位不是永久课程。采样方法见 `docs/05_EXECUTION_SYSTEM.md`；只把多个岗位重复出现的信号升为主线。

### 劳动力市场

- [World Economic Forum — Future of Jobs Report 2025](https://www.weforum.org/publications/the-future-of-jobs-report-2025/digest/)：2025–2030 雇主调查；AI/big data、网络安全、技术素养增长快，同时分析、韧性、领导与协作仍重要。
- [U.S. BLS — 2024–2034 employment projections](https://www.bls.gov/opub/mlr/2026/article/industry-and-occupational-employment-projections-overview.htm)：AI 采用推动软件、数据、研究与云基础设施需求；它是职业大类趋势，不是 `Agent Engineer` 职位数预测。

## 2. Harness、Agent 与 Evals

- [AWS AgentCore Harness](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/harness.html)：当前最清晰的 production harness 组件定义之一。
- [AWS AgentCore Harness vs Runtime](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/harness-vs-runtime.html)：理解 orchestration loop 与托管执行环境的边界。
- [Anthropic — Effective harnesses for long-running agents](https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents)：跨 context/session 的 artifact handoff、incremental progress、testing 和失败模式。
- [Anthropic — Demystifying evals for AI agents](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents)：task、trial、trace、outcome、agent harness、eval harness、grader、非确定性和 transcript review。
- [OpenAI official model guidance](https://developers.openai.com/api/docs/guides/latest-model)：Responses、reasoning、tool orchestration、自治边界、prompt/context 和代表性 eval 的当前指导。

## 3. 当前主流框架：选一个深入，另一个用于迁移对照

- [Microsoft Agent Framework](https://learn.microsoft.com/agent-framework/)：agents、tools、skills、conversation、workflow、durable extension 与 A2A；官方文档含从 AutoGen 迁移入口。
- [Google ADK hands-on](https://codelabs.developers.google.com/codelabs/cloud-run/tools-make-an-agent)：model-agnostic ADK、工具、MCP 和部署起点。
- [Strands Agents documentation](https://strandsagents.com/docs/user-guide/quickstart/overview/)：Python/TypeScript、provider、MCP/A2A、session、OTel 与多 Agent。
- [NVIDIA NeMo Agent Toolkit](https://developer.nvidia.com/agent-intelligence-toolkit)：跨框架 profiling、工具效率、成本、可靠性和 NVIDIA 加速生态。
- [OpenAI API quickstart / Agents example](https://platform.openai.com/docs/quickstart)：Responses 与 Agents SDK 的官方入门；若路径变化，从 OpenAI Developers 导航进入 SDK。

学习方法：先完成 raw loop，再将同一 task/eval port 到框架；不要同时做四套教程。

## 4. 协议与互操作

- [MCP 2026-07-28 release](https://blog.modelcontextprotocol.io/posts/2026-07-28/)：当前版本变化，包括 stateless core、MRTR、header routing、authorization、extensions 和 Tasks。
- [MCP specification](https://modelcontextprotocol.io/specification/2026-07-28)：实现时以 schema/spec 为准，博客只用于理解变化。
- [Agent2Agent Protocol specification](https://google-a2a.github.io/A2A/specification/)：Agent discovery、messages、tasks、artifacts 与跨框架协作。
- [NSA — MCP Security Design Considerations](https://www.nsa.gov/Press-Room/Press-Releases-Statements/Press-Release-View/Article/4496698/nsa-releases-security-design-considerations-for-ai-driven-automation-leveraging/)：MCP 自动化的安全设计提醒；实现 P2 前阅读当前附带文档。

## 5. 云与生产工程

只选一家云做深度，另外两家能读架构即可。

### AWS 路线

- [Amazon Bedrock AgentCore documentation](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/what-is-bedrock-agentcore.html)
- [Strands Agents](https://strandsagents.com/docs/)
- IAM、ECS/EKS/Lambda、SQS、Step Functions、RDS、CloudWatch/OpenTelemetry 的官方文档按项目加载。

### Google Cloud 路线

- [Vertex AI Agent Builder documentation](https://cloud.google.com/products/agent-builder)
- [Google ADK](https://google.github.io/adk-docs/)
- Cloud Run/GKE、Pub/Sub、Cloud SQL、Cloud Trace/OTel、IAM 的官方文档按项目加载。

### Microsoft/Azure 路线

- [Microsoft Agent Framework](https://learn.microsoft.com/agent-framework/)
- [Azure AI Foundry documentation](https://learn.microsoft.com/azure/ai-foundry/)
- Container Apps/AKS、Service Bus、PostgreSQL、Application Insights/OTel、Entra 的官方文档按项目加载。

## 6. ML / LLM 核心论文

按课程周次读论文的 abstract、method、figures、experiments 和 limitations；不要求一开始逐行推导。

- [Attention Is All You Need](https://arxiv.org/abs/1706.03762)
- [Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks](https://arxiv.org/abs/2005.11401)
- [ReAct: Synergizing Reasoning and Acting in Language Models](https://arxiv.org/abs/2210.03629)
- [Toolformer: Language Models Can Teach Themselves to Use Tools](https://arxiv.org/abs/2302.04761)
- [Reflexion: Language Agents with Verbal Reinforcement Learning](https://arxiv.org/abs/2303.11366)
- [SWE-bench](https://arxiv.org/abs/2310.06770)
- [AgentBench](https://arxiv.org/abs/2308.03688)
- [τ-bench: A Benchmark for Tool-Agent-User Interaction](https://arxiv.org/abs/2406.12045)

读论文时问：实验评测的是 model、harness 还是两者？grader 是否公平？环境是否泄露答案？结果能否迁移到我的任务？

## 7. 安全、风险与治理

- [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
- [NIST AI RMF Generative AI Profile](https://www.nist.gov/publications/artificial-intelligence-risk-management-framework-generative-artificial-intelligence)
- [OWASP GenAI Security Project](https://genai.owasp.org/)
- [MITRE ATLAS](https://atlas.mitre.org/)
- 各云 provider 的 IAM、secret、network isolation、audit 官方文档。

安全资料用于 threat model 和 tests；不能用 prompt guardrail 替代授权、隔离与审计。

## 8. 数据库、分布式系统与可观测

- [Designing Data-Intensive Applications](https://dataintensive.net/)：书籍主页；重点是 storage、replication、partition、transactions、stream processing。
- [PostgreSQL documentation](https://www.postgresql.org/docs/)
- [Kubernetes documentation](https://kubernetes.io/docs/home/)
- [OpenTelemetry documentation](https://opentelemetry.io/docs/)
- [Temporal documentation](https://docs.temporal.io/) 或所选云的 durable workflow 官方文档。

## 9. 每季度刷新清单

- [ ] MCP/A2A 当前 spec/version 与安全变更
- [ ] 四个主框架的 stable status、migration、breaking changes
- [ ] OpenAI/Anthropic/Google/AWS/Microsoft/NVIDIA model 与 agent platform 文档
- [ ] 六家目标公司的 20+ 当前岗位样本
- [ ] eval benchmark 是否饱和或修订
- [ ] 安全指南、已知漏洞和云服务区域/计费变化
- [ ] 将过时链接和结论标为 archived，不悄悄覆盖历史实验
