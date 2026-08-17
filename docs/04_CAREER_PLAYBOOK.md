# 求职与面试打法

## 1. 先选择进入市场的楔子

目标可以广，但简历必须有清晰标签。建议根据既有经历选择：

| 既有背景 | 首选定位 | 作品重点 |
|---|---|---|
| 3+ 年后端/平台 | Agent Platform / Harness Engineer | P4，分布式系统、SLO、安全、成本 |
| 前端/全栈 | Applied AI Product Engineer | P1 + UI + P4 vertical slice，端到端用户指标 |
| 数据/ML | Applied ML / Agent Evals Engineer | P1/P3，数据、实验、grader、ML 基础 |
| 安全/SRE/云 | Agent Security / Reliability | P2/P4，隔离、identity、observability、incident |
| 金融/风控 | Financial Agent Engineer | P5A，审计、规则、可解释、治理 |
| 无工程经历 | 后端/Applied AI entry-level 或 FDE | 先做强软件工程，求职周期按 18–24 个月看 |

不要同时在简历标题写六种岗位。保留一份 master resume，再为两个相邻岗位族定制。

## 2. 年度求职节奏

### Months 1–2：建立公开轨迹

- GitHub profile、英文 bio、主 README。
- 每周英文 build log；开始 DSA。
- 建立 30 家公司池，不急着海投。
- 每周联系 2 位工程师，问题必须具体到其文章、项目或技术选择。

### Months 3–5：用项目换反馈

- 发布 P0/P1 的 demo 和第一篇实验文章。
- 每月 1–2 个带测试的开源 PR。
- 做 3 次 informational interview，询问真实工作和面试缺口。
- 可投 3–5 个低风险岗位校准，不把最想去的公司当练习场。

### Months 6–8：建立专业标签

- P2/P3 发布；做一次线上分享或长文。
- 每两周 mock interview。
- 建立 60 个目标岗位的 requirements 数据表，统计关键词和缺口。
- 开始有选择地投递 3–5 份/周。

### Months 9–10：Capstone 与内推

- P4/P5 beta；邀请 3–5 位真实工程师试用/review。
- 用反馈形成 issue、修复和 postmortem。
- 针对目标团队准备 1 页“我如何贡献”说明。
- 每周 5–8 份高质量申请，优先有团队匹配和 warm intro 的机会。

### Months 11–12：面试循环

- 每周一次 coding、一次 system/agent design、一次 behavioral mock。
- 一次只维护 8–12 个活跃机会，记录 stage、contact、next action、feedback。
- 面试当天写复盘；同类失误出现两次即进入一周专项训练。

## 3. 岗位搜索关键词

不要只搜 `Agent Engineer`：

- Agent Platform Engineer / Agent Runtime / Agent Infrastructure
- Applied AI Engineer / Applied ML Engineer
- Generative AI Engineer / LLM Engineer
- Software Engineer, AI/ML / AI Agents
- AI Quality / Evals / Model Behavior
- ML Systems / Inference / AI Infrastructure
- Forward Deployed Engineer, AI
- Developer Productivity / Coding Agent
- AI Security / AI Safety Engineering
- RAG / Search / Information Retrieval Engineer

## 4. 简历

### 一页主结构

1. 一行定位 + 2 个最强关键词
2. Experience：优先生产影响
3. Selected AI Systems：2–3 个主项目
4. Open Source / Writing：有质量才写
5. Skills：按 Languages / Systems / AI / Cloud 分类
6. Education

### Bullet 公式

```text
Built [system] for [user/problem], using [only essential technical detail],
improving [quality/latency/cost/reliability] from X to Y on [dataset/traffic],
while satisfying [security/SLO/scale constraint].
```

示例：

> Built a multi-tenant agent execution service with checkpointed workers and scoped tool credentials; recovered 100% of injected worker failures without duplicate side effects across 1,000 eval runs, at a p95 orchestration overhead of 180 ms.

如果没有真实线上用户，就写 `eval runs`、`load test` 或 `pilot users`，不要写成 production impact。

### xAI 风格的 100-word exceptional work

结构：问题难度 20 词，个人贡献 35 词，可验证结果 25 词，为什么重要 20 词。删掉形容词，让数字、链接和技术决策证明“exceptional”。

## 5. GitHub 和项目展示

招聘者 60 秒路径：

1. Profile README 看懂定位。
2. pinned capstone 首屏看到 architecture + 3 metrics + demo。
3. `make demo` 或一条命令运行。
4. `evals/report.md` 看到 baseline、结果、失败和限制。
5. `docs/adr/` 和 postmortem 看到判断深度。

保持 issue/commit 历史自然。一次性上传完成品不如可追踪的迭代。

## 6. 面试能力分布

| 面试面 | 目标标准 | 训练方式 |
|---|---|---|
| Coding / DSA | 45 分钟完成 medium，测试边界，分析复杂度 | 120–150 题 + mock |
| Practical coding | 调试现有服务、API、并发、测试 | 每月一次 2 小时 repo task |
| System design | API/data/scale/failure/security/ops/cost 完整 | 每月一份，后期每周 mock |
| Agent/LLM design | baseline、data、tools、eval、安全、rollout | 15 个常见场景反复讲 |
| ML fundamentals | 指标、数据切分、Transformer、训练/推理 | 闭卷解释 + 小实验 |
| Behavioral | 具体、量化、反思、ownership | 8 个 STAR 故事 |
| Communication | 简洁英文解释复杂系统 | 每周 build log + 月度 demo |

## 7. Agent System Design 答题框架

按顺序回答，避免一上来报框架名：

1. 用户、任务、成功指标和不可接受失败是什么？
2. 普通软件或 workflow 是否足够？为什么需要 Agent？
3. 输入/数据质量、隐私、freshness 和 ground truth 是什么？
4. model、tools、RAG、memory 和 state 如何分工？
5. tool 权限、副作用、审批、幂等和补偿如何做？
6. harness/runtime 如何处理 timeout、retry、checkpoint、cancel、isolation？
7. offline eval 如何覆盖 outcome、trajectory、安全和非确定性？
8. 线上 trace、SLO、用户反馈、A/B 和 incident 如何闭环？
9. latency、cost、availability 和 quality 如何权衡？
10. 如何 version、canary、rollback，以及新模型如何升级？

## 8. 12 周面试冲刺模板

| 周 | Coding | Design | Agent/ML | Behavioral / Career |
|---:|---|---|---|---|
| 1–2 | array/hash/tree | API/cache/queue | LLM lifecycle、RAG | resume、2 个 STAR |
| 3–4 | graph/heap | storage/stream | tool loop、memory | ownership/failure |
| 5–6 | recursion/DP | multi-tenant SaaS | eval/grader | conflict/ambiguity |
| 7–8 | timed mixed | agent runtime | security/MCP | leadership/customer |
| 9–10 | company mock | eval platform | inference/cost | full behavioral mock |
| 11–12 | full loop | full loop | full loop | application calibration |

## 9. 公司定制

### Amazon

- Coding + distributed system 深度。
- 8 个 Leadership Principles 故事，每个准备追问和数据。
- 设计时主动讨论 operations、blast radius、on-call、rollback 和成本。

### Google

- DSA 和算法表达要稳定；不要用 Agent 知识弥补基础短板。
- 实验严谨：数据、指标、ablation、error analysis。
- 系统设计关注大规模、质量、安全和跨产品抽象。

### Microsoft

- 企业 identity/governance、Azure、C# 或 Python、Agent Framework。
- 强调兼容、可维护、开发者体验和跨团队沟通。

### NVIDIA

- 根据岗位选择企业 Agent 或 ML systems；后者要补 GPU、PyTorch、profiling 和 inference。
- 讲性能时给出测量环境，不引用营销 benchmark。

### JPMorganChase

- secure-by-default、audit、explainability、data governance、resilience。
- 展示你理解金融场景中“拒绝/升级给人”也是正确 outcome。

### xAI

- 准备陌生问题现场解题、代码质量和工程底层。
- 代表作必须足够难且个人贡献清晰；沟通短而精确。

## 10. 地域、签证与现实策略

- 建立三层公司池：理想、强匹配、可进入赛道；不要只投六家公司。
- 在职位表中记录 location、onsite/remote、work authorization、sponsorship、语言和级别。
- 如果目标美国岗位但暂时无工签，平行考虑中国/新加坡/香港/伦敦/加拿大团队、跨国公司本地办公室、远程开源和内部转岗路径。
- 英文不是附加项。设计文档、demo、面试和开源协作都应持续用英文训练。

## 11. Offer 评估

优先考虑能累积以下资产的岗位，而非只看职位名：

- 是否对生产 outcome、eval、reliability 或 platform 有真实 ownership？
- 是否接触真实用户和高质量数据？
- 是否能做 end-to-end，而非永久停留在 prompt 配置？
- 是否有强工程师、code review、incident 和设计文化？
- 技术是否可迁移：distributed systems、security、ML systems、domain？
- 公司是否把 AI 当核心产品/平台，而不只是短期 demo？

## 12. 每周求职仪表盘

- 精准申请数、回复数、screen 数、onsite 数、offer 数
- warm intro 比例
- coding/design/behavioral mock 得分
- 高频缺口及修复动作
- 项目访问、demo、开源 PR 和技术文章反馈

申请数量不是北极星；**有效面试率和反馈后能力提升速度**才是。
