# 52 周课程：从基础到 Production Agent Builder

默认每周 15–20 小时。每周结构：学习 3–4 小时、实现 8–10 小时、测试/评测 2–3 小时、写作与求职 2 小时。

## 路线调整

- A 档（基础补强）：基线测评 < 50。Weeks 1–8 各用两周，总路线延长到 60–68 周。
- B 档（标准）：50–79。按本文执行。
- C 档（加速）：≥ 80 且编程题、API、测试、Docker 均通过。Weeks 1–8 压缩为四周，把时间用于 capstone、开源和面试。

不能因为“看过”而跳级；必须通过阶段出口。

---

## Phase 0 — Week 0：基线和环境

### 目标

建立真实起点、时间预算和工具链。

- 完成 `docs/07_BASELINE_ASSESSMENT.md`。
- 安装 Python 3.12+、`uv`、Node.js 20+、Git、Docker、VS Code/Cursor 类编辑器。
- 建立 GitHub、英文 README 模板、学习日历和 API 成本上限。
- 在 `TRACKER.md` 填入初始分数和每周固定时间。

出口：测试环境可运行；第一次模型调用可复现；有明确的 A/B/C 档。

---

## Phase 1 — Weeks 1–4：软件工程底座

| 周 | 学习重点 | 必做产物 | 验收 |
|---:|---|---|---|
| 1 | Python typing、dataclass/Pydantic、exceptions、iterators、async 基础 | typed CLI：读取 JSONL、并发处理、结构化输出 | mypy/pyright 无关键错误；pytest ≥ 15 tests |
| 2 | HTTP、REST、JSON Schema、auth、streaming、timeout/retry | FastAPI 服务 + typed client + SSE 流 | contract tests；能解释 4xx/5xx 和幂等 |
| 3 | SQL/Postgres、索引、事务；Redis/queue 概念 | 带 repository layer 的任务服务 | migration、并发写测试、查询计划说明 |
| 4 | Docker、CI、logging、Git flow；TS 基础 | 容器化服务 + GitHub Actions 类 CI | 一条命令启动；lint/test/build 全绿 |

并行面试：每周 3 道 DSA，重点 array/hashmap、stack/queue、tree、graph 基础。

出口：在 120 分钟内从空目录交付 typed API、数据库、测试和容器；测试覆盖关键失败路径。

---

## Phase 2 — Weeks 5–8：ML、Transformer 与 LLM API

| 周 | 学习重点 | 必做产物 | 验收 |
|---:|---|---|---|
| 5 | 监督学习、train/val/test、loss、overfit、precision/recall、calibration | scikit-learn 文本分类实验 | 固定 seed；误差分析 ≥ 20 个样本 |
| 6 | 向量、矩阵、softmax、attention、Transformer、tokenization | 小型 attention/transformer notebook | 能手算一次 attention；解释位置编码 |
| 7 | pretraining、SFT、preference/RL、inference、sampling、quantization 概念 | 2 页模型生命周期说明 | 能判断 RAG、prompt、fine-tune 各自适用边界 |
| 8 | Responses/messages、structured output、tool calling、streaming、usage、rate limit | provider-neutral LLM client | 两家 provider 或 mock 可切换；错误和 usage 被记录 |

出口：能解释 temperature、top-p、context window、reasoning tokens、cache、embedding 与 reranker；API client 有 timeout、retry、schema validation、budget。

---

## Phase 3 — Weeks 9–12：RAG 与 Context Engineering

| 周 | 学习重点 | 必做产物 | 验收 |
|---:|---|---|---|
| 9 | ingestion、解析、chunking、metadata、embedding | 文档 ingestion pipeline | 增量更新、去重、删除和数据 lineage |
| 10 | BM25、dense/hybrid retrieval、reranking、query rewrite | 检索 benchmark | ≥ 30 queries；Recall@k/MRR/nDCG 至少两项 |
| 11 | context assembly、citation、groundedness、lost-in-middle | 带逐句证据的 answer service | 引用能回链原文；拒答策略有测试 |
| 12 | context budget、cache、conversation state、memory taxonomy | Project P1 v1 | 与 naive baseline 对比质量、延迟和成本 |

出口：不是“看起来回答得不错”，而是在固定测试集上报告 retrieval 与 answer 两层指标，并完成失败类别分析。

---

## Phase 4 — Weeks 13–16：从零实现 Agent

| 周 | 学习重点 | 必做产物 | 验收 |
|---:|---|---|---|
| 13 | ReAct、tool call、state machine、termination | 不用框架的最小 Agent loop | 能处理无效 schema、未知工具、重复调用 |
| 14 | tool contract、side effects、idempotency、approval | 工具注册表 + policy layer | destructive action 必须审批；权限有负向测试 |
| 15 | planning、reflection 的收益与风险；预算和停止条件 | 可插拔 planner、step/token/time budget | 对比无 planner baseline，证明是否值得 |
| 16 | session、checkpoint、短期/长期 memory、恢复 | Project P0 完整版 | 中断恢复；同一工具不重复产生副作用 |

出口：白板画出 loop 和状态转换；能从 trace 判断失败在模型、tool、state、policy 或 environment 哪层。

---

## Phase 5 — Weeks 17–20：Harness Engineering

| 周 | 学习重点 | 必做产物 | 验收 |
|---:|---|---|---|
| 17 | harness vs runtime vs sandbox；control/data plane | harness 架构设计文档 | API、state、identity、execution 边界清楚 |
| 18 | context compaction、artifact handoff、long-running task | 跨 5 个 session 的任务 runner | 每次恢复不依赖隐藏聊天历史 |
| 19 | sandbox、filesystem、network、secret、tenant isolation | 受限 code/tool executor | 越权文件/网络/secret 测试必须失败 |
| 20 | trace、checkpoint、replay、version、rollout/rollback | Harness P4 alpha | 任一 run 可重放关键步骤；版本可回滚 |

出口：完成一个 30–60 分钟任务，故意注入 timeout、tool failure 和进程中断；系统能恢复或明确失败，不产生不一致 outcome。

---

## Phase 6 — Weeks 21–24：框架、MCP 与 A2A

框架每季度会变。本阶段考察迁移能力，不考 API 背诵。

| 周 | 学习重点 | 必做产物 | 验收 |
|---:|---|---|---|
| 21 | 深入一个主框架：OpenAI Agents SDK、Google ADK、Microsoft Agent Framework 或 Strands | 把 Phase 4 Agent 重写一次 | 与 raw loop 比较代码量、可控性、trace、成本 |
| 22 | MCP 2026-07-28 core、tools/resources、auth、Tasks extension | Project P2：MCP server + client | schema、auth、超时、注入、恶意返回测试 |
| 23 | A2A：discovery、Agent Card、messages、tasks、artifacts | 两个异构 Agent 协作 | 不共享内部 memory/tool；任务状态可追踪 |
| 24 | 再选一个不同生态做 port；框架抽象泄漏 | compatibility report | 相同 eval suite 跑三种实现，给出选型结论 |

出口：能在不改业务任务和 graders 的情况下替换 Agent 实现；能清楚回答 MCP 与 A2A 分别解决什么、不解决什么。

---

## Phase 7 — Weeks 25–28：Agent Evals 与实验科学

| 周 | 学习重点 | 必做产物 | 验收 |
|---:|---|---|---|
| 25 | task/trial/trace/outcome、capability vs regression eval | 30-task eval suite | 每个 task 有可观察 success criteria |
| 26 | code/model/human graders、rubric、judge bias | 组合 grader | LLM judge 与人工标注一致率被报告 |
| 27 | 非确定性、重复 trial、pass@k/pass^k、置信区间、A/B | 实验 runner | 至少 3 configs × 3 trials；固定环境隔离 |
| 28 | transcript review、failure taxonomy、eval contamination/reward hacking | Project P3 eval lab | 从 10 个失败中提出并验证改进，保留回归集 |

出口：eval suite 至少 50 tasks；报告 task success、unsafe action rate、p50/p95 latency、cost/task、tool error rate；不能只报平均 LLM judge 分。

---

## Phase 8 — Weeks 29–32：Production LLMOps

| 周 | 学习重点 | 必做产物 | 验收 |
|---:|---|---|---|
| 29 | async worker、queue、webhook、durable workflow、backpressure | 长任务 API | crash 后不丢任务；幂等 key 和 dead-letter queue |
| 30 | OpenTelemetry、structured logs、trace、metric、SLO | 可观测 dashboard | 可按 tenant/model/tool/version 切片 |
| 31 | cache、batch、routing、fallback、rate limit、cost attribution | 模型路由实验 | 质量门槛下成本或延迟有可测改善 |
| 32 | K8s/managed container、CI/CD、canary、rollback、IaC | 云上 staging 部署 | load test、runbook、回滚演练、账单上限 |

出口：完成一次故障演练和 postmortem；SLO 有计算方法，告警不是“CPU 高”这类无用户含义指标。

---

## Phase 9 — Weeks 33–36：Agent Security、Safety 与 Governance

| 周 | 学习重点 | 必做产物 | 验收 |
|---:|---|---|---|
| 33 | prompt injection、indirect injection、data exfiltration、confused deputy | threat model | assets、trust boundaries、abuse cases、controls |
| 34 | authn/authz、least privilege、scoped token、secret broker、tenant isolation | policy enforcement point | 跨租户、越权、token replay 测试 |
| 35 | supply chain、MCP/tool poisoning、sandbox escape 思维、audit | adversarial eval set | ≥ 30 attacks；按风险而非字符串黑名单防御 |
| 36 | approval UX、policy-as-code、PII、retention、incident response | Project P2 security release | 高风险 action 展示参数、影响、证据并可拒绝 |

出口：红队成功率和正常任务成功率同时报告；安全措施不能以让系统完全不可用为代价。

---

## Phase 10 — Weeks 37–40：多 Agent 与长时任务

| 周 | 学习重点 | 必做产物 | 验收 |
|---:|---|---|---|
| 37 | router、supervisor-worker、planner-executor、map-reduce | 3 种 orchestrator 小实验 | 同一数据集比较，不凭架构图选优 |
| 38 | generator-evaluator、独立验证、debate 的适用边界 | evaluator loop | 证明独立 evaluator 对某类 failure 有提升 |
| 39 | parallelism、shared state、race、deadlock、cancellation、compensation | 并行 worker harness | 并发安全；取消和部分失败不破坏 outcome |
| 40 | durable execution、artifact handoff、人类接管、长时预算 | 2–4 小时 long-run demo | checkpoint、resume、审计和总成本报告 |

出口：若多 Agent 未超过单 Agent baseline，就公开记录负结果并采用更简单架构；能解释增加复杂度的量化理由。

---

## Phase 11 — Weeks 41–44：多模态、Computer Use 与 GPU 基础

| 周 | 学习重点 | 必做产物 | 验收 |
|---:|---|---|---|
| 41 | vision/audio/document inputs、OCR、grounding | 多模态文档任务 | 分模态 eval；错误不能被文本流掩盖 |
| 42 | browser/computer use、DOM vs pixels、action confirmation | sandboxed UI Agent | e2e outcome grader；防页面间接注入 |
| 43 | PyTorch、GPU memory、batch、KV cache、TTFT/tokens-per-sec | inference profiling notebook | 至少比较 batch/quantization 两项影响 |
| 44 | open-weight model、serving、quantization、cloud vs local | 小模型/大模型路由 | 在质量阈值下报告成本/延迟/隐私取舍 |

出口：能解释何时 API 模型、何时自托管；完成一次 GPU/serving profiler，而不是只引用厂商数字。

---

## Phase 12 — Weeks 45–48：领域 Capstone

默认选择以下之一：

- 金融/合规 Agent：面向 JPMorganChase 等受监管机构。
- Developer Agent Platform：面向 AWS、Microsoft、Google、xAI。
- GPU/AI Infrastructure Agent：面向 NVIDIA/ML systems。

| 周 | 学习重点 | 必做产物 | 验收 |
|---:|---|---|---|
| 45 | 用户研究、problem framing、success/failure、数据协议 | PRD + threat model + eval plan | 在写核心代码前确定 ≥ 50 tasks |
| 46 | vertical slice、数据与工具、核心 harness | Capstone alpha | 10 个 golden paths 和 10 个失败路径 |
| 47 | reliability/security/observability、load、cost | Capstone beta | eval ≥ 100 tasks；故障演练；SLO |
| 48 | UX、文档、demo、benchmark、ADR、postmortem | Capstone release candidate | 外部用户可从零复现；限制诚实明确 |

出口：满足 `docs/03_PROJECTS_AND_PORTFOLIO.md` 的 Capstone Definition of Done。

---

## Phase 13 — Weeks 49–52：求职冲刺与公开影响

| 周 | 学习重点 | 必做产物 | 验收 |
|---:|---|---|---|
| 49 | GitHub/repo polish、resume、LinkedIn、100-word exceptional work | 完整求职包 v1 | 3 位工程师可在 60 秒说出你的强项 |
| 50 | DSA 与 coding、debugging、test design | 3 次 mock coding | 45 分钟 medium；边界和复杂度说清楚 |
| 51 | system design、ML/Agent design、security | 3 次 mock design | 指标、容量、failure、安全、成本、eval 完整 |
| 52 | behavioral、company calibration、application pipeline | 3 次 full loop + 目标清单 | 基于反馈修正；开始稳定投递和内推 |

这四周不是第一次准备面试；DSA、写作、networking 和岗位采样从 Week 1 就开始。

---

## 全年并行轨道

### DSA / CS

- Weeks 1–12：每周 3 题
- Weeks 13–36：每周 2 题 + 每两周一次 45 分钟 mock
- Weeks 37–52：每周 4 题 + 每周一次 mock
- 总目标：120–150 道高质量复盘题，不追求无意义题量

### 系统设计

- 每月一份设计：URL shortener → queue → RAG → agent runtime → eval platform → multi-tenant harness。
- 每份都包含容量、API、data model、failure、security、observability、cost 和 rollout。

### 英文与技术写作

- 每周用英文写一份 200–500 词 build log。
- 每月录 8–12 分钟英文 demo。
- 每季度发布一篇带实验数据的长文。
- 面试前准备 8 个 STAR 故事：ownership、failure、conflict、ambiguity、speed、quality、leadership、customer impact。

### 开源与人脉

- Month 2 起每月阅读 4 个相关 PR。
- Month 3 起每月提交 1–2 个有测试的 PR。
- 每周联系 2 位目标领域工程师，以具体项目/文章问题为切入，不群发求内推。
- Month 6 后每月进行 2 次 informational interview 或社区分享。

## 阅读顺序

1. 官方协议/SDK 文档
2. 目标公司工程博客与论文
3. 高质量开源实现和测试
4. 课程与二手总结

资料不是一次性书单；以 `resources/OFFICIAL_SOURCES.md` 为起点，每季度刷新。
