# AI Agent Builder 学习工程

目标：用 12 个月、每周 15–20 小时，从当前基线成长为能够竞争一线科技公司和大型金融机构 **Agent / Applied AI / AI Platform Engineer** 岗位的工程师。

这不是“看完一批课程”的计划。项目以可验证证据为中心：每个阶段都必须留下代码、测试、评测数据、架构决策、线上指标或公开技术输出。

## 默认路线

- 主线：Agent Platform / Applied AI Engineer
- 副线：Agent Evals、Safety、Observability 与 Harness Engineering
- 默认技术栈：Python + TypeScript，FastAPI，PostgreSQL/Redis，Docker/Kubernetes，OpenTelemetry，一家主云平台
- 学习强度：15–20 小时/周；低于 10 小时采用 18 个月版，高于 25 小时采用 8–9 个月版
- 目标市场：微软、Amazon/AWS、Google、NVIDIA、JPMorganChase、xAI 及同等要求的团队

## 成功标准

到第 52 周，你应当能够：

1. 不依赖 Agent 框架，从零实现带工具调用、状态、预算、重试和终止条件的 Agent loop。
2. 解释并实现 model、agent、workflow、runtime、sandbox、agent harness、eval harness 的边界。
3. 构建带检索、记忆、MCP、异步任务、人类审批和多租户隔离的生产服务。
4. 用 50–200 个任务的 eval suite 比较模型、提示词、工具和 harness 版本，报告质量、延迟、成本和失败模式。
5. 对 prompt injection、越权工具调用、数据泄露、tenant crossing 和供应链风险做威胁建模。
6. 部署并运维服务：CI/CD、灰度、回滚、trace、SLO、告警、容量和成本分析。
7. 完成至少 4 个可公开项目，其中 1 个达到 production-grade capstone 标准。
8. 通过中高级编码、系统设计、LLM/Agent 设计、ML 基础和行为面试。

“会调用 API”不算完成；“可以被别人复现、评测、部署和审查”才算完成。

## 文档导航

1. [方向、市场与能力矩阵](docs/01_NORTH_STAR_AND_MARKET.md)
2. [52 周课程](docs/02_CURRICULUM_52_WEEKS.md)
3. [作品集项目](docs/03_PROJECTS_AND_PORTFOLIO.md)
4. [求职与面试打法](docs/04_CAREER_PLAYBOOK.md)
5. [执行、复盘和验收系统](docs/05_EXECUTION_SYSTEM.md)
6. [Agent / Harness 概念地图](docs/06_CONCEPT_MAP.md)
7. [基线测评](docs/07_BASELINE_ASSESSMENT.md)
8. [官方资料与岗位样本](resources/OFFICIAL_SOURCES.md)
9. [进度总表](TRACKER.md)

## 前 7 天立即执行

- [ ] Day 1：完成[基线测评](docs/07_BASELINE_ASSESSMENT.md)，记录真实耗时，不查答案。
- [ ] Day 2：把结果填入 [TRACKER.md](TRACKER.md)，确认每周固定学习时段。
- [ ] Day 3：完成 Git、Python、`uv`、Node.js、Docker、编辑器与测试环境。
- [ ] Day 4：用原生 Python 调一次模型 API，保存结构化输出、usage 和错误处理。
- [ ] Day 5：手写最小工具调用循环，不用 Agent 框架。
- [ ] Day 6：为它加入 10 个确定性测试和 5 个行为 eval。
- [ ] Day 7：写第一份周复盘；把失败归因到知识、实现、环境或评测，而不是笼统写“模型不行”。

## 学习原则

- 60% 构建与调试，20% 阅读，10% 复盘写作，10% 求职资产。
- 先手写基本抽象，再使用框架；先单 Agent，再多 Agent。
- 先建立 eval，再做“优化”；任何提升必须有基线和数据。
- 框架知识会过时，系统能力更耐久：协议、状态机、分布式系统、安全、测试、数据和产品判断优先。
- 每月删除一项已经不再带来性能收益的 harness 复杂度。
- 每季度重新采样目标公司的 20 个岗位，并更新能力矩阵。

## 仓库结构

```text
.
├── docs/           # 路线、课程、职业与概念文档
├── projects/       # 每个阶段的项目规格与后续代码
├── resources/      # 官方来源和季度岗位采样
├── templates/      # 周复盘、项目、评测和系统设计模板
├── TRACKER.md      # 唯一进度真相源
└── AGENTS.md       # 后续 AI 学习教练的协作约定
```

## 下一步

先做基线测评。不要因为“基础看起来熟悉”而跳过；路线将在测评后按 A（基础补强）、B（标准）或 C（加速）档执行。
