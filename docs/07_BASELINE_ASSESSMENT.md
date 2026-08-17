# 基线测评

总时长约 6–8 小时，可分两天完成。除官方语言/API 速查外，不使用 AI、不搜索题目答案。记录真实耗时、卡点和最终可运行证据。

## Part A — Python 与测试（20 分，90 分钟）

实现一个异步任务执行器：

- 输入 JSONL，每行包含 `id`、`url`、`timeout_ms`。
- 并发上限可配置；单任务 timeout；只对 429/5xx 重试，指数退避加 jitter。
- 保持最终输出与输入顺序一致。
- 结果区分 success、timeout、client_error、server_error、invalid_input。
- 支持 graceful cancellation。
- 写 tests，不发真实网络请求。

评分：正确性 8、typing/结构 4、async/cancel 3、tests 4、说明 1。

## Part B — API 与数据库（15 分，75 分钟）

设计并实现最小 FastAPI：

- `POST /jobs` 创建任务，支持 idempotency key。
- `GET /jobs/{id}` 查询状态。
- 数据持久化；可使用 SQLite，但说明迁移到 Postgres 的变化。
- 结构化错误、migration、至少 6 个 API tests。

评分：API contract 4、data model/事务 4、幂等 3、tests 3、说明 1。

## Part C — Agent loop（20 分，90 分钟）

用 mock model 实现，不使用 Agent framework：

- model 可能返回 final answer、合法 tool call、非法 JSON、未知 tool 或重复 tool call。
- 至少有 calculator 和 key-value lookup 两个 typed tools。
- 限制 max steps；记录 trace；任何 side effect 默认禁止。
- 写 10 个 tests 覆盖正常、失败和终止。

评分：loop/state 6、tool validation 4、termination/budget 3、trace 2、tests 5。

## Part D — LLM / ML 闭卷解释（15 分，45 分钟）

每题 2–4 句：

1. self-attention 在计算什么？时间复杂度主要来自哪里？
2. temperature 与 top-p 的差异？
3. embedding 和生成模型输出有什么不同？
4. 为什么 validation/test 不能与 prompt tuning 过程混用？
5. precision、recall 何时各自更重要？
6. RAG、fine-tuning、tool call 分别解决什么？
7. 为什么 context window 变大不等于 memory 问题消失？
8. `pass@k` 与 `pass^k` 各表达什么可靠性问题？
9. LLM-as-a-judge 有哪些偏差？如何校准？
10. 量化对显存、速度和质量可能有什么影响？

评分：任选五题，每题 3 分；其余用于诊断。

## Part E — System design（20 分，60 分钟）

设计“多租户企业研究 Agent”：用户上传私有文档，Agent 进行多步检索并生成带引用报告。

必须覆盖：

- requirements / non-goals / SLO
- API、data model、ingestion、retrieval
- agent loop、tool、state、memory、long-running job
- tenant isolation、identity、prompt injection、防数据泄露
- offline eval、online monitoring、version/canary/rollback
- latency、cost、availability 权衡

评分：需求/指标 3、架构/数据 5、Agent/harness 4、安全 3、eval/ops 3、权衡 2。

## Part F — Coding interview（10 分，45 分钟）

任选一道未做过的 LeetCode medium 级 tree/graph 题：

- 前 5 分钟澄清和给例子。
- 35 分钟编码并测试。
- 最后 5 分钟分析时间/空间复杂度和替代方案。

评分：正确 5、思路表达 2、边界测试 2、复杂度 1。

## 分档

- 80–100：C 加速档。基础压缩，尽快进入 P1/P3/P4。
- 50–79：B 标准档。执行 52 周路线。
- 30–49：A 基础补强档。Phase 1/2 加倍时间。
- < 30：先完成 8–12 周 Python/CS/后端基础，再重新测评。

### 硬门槛修正

即使总分高，以下任一项出现也不能进入 C 档：

- Part A 或 B < 50%
- Part C 无法实现稳定终止
- Part E 未考虑 tenant isolation 或 eval
- Part F 完全无法写出可运行解

## 测评后记录

在 `TRACKER.md` 写下：总分、各部分、真实耗时、三个最大缺口、采用档位、下次复测日期。保留原始代码，不要在复盘前美化。
