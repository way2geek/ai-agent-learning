# 执行、复盘和验收系统

## 1. 每周 18 小时默认模板

| 模块 | 时间 | 输出 |
|---|---:|---|
| 官方阅读与笔记 | 3h | 1 页概念/决策笔记 |
| 主项目实现 | 8h | 可运行 increment + tests |
| Evals / debug / trace review | 3h | 数据、失败分类、实验结论 |
| DSA / CS / system design | 2h | 2–4 题或一段设计 |
| 英文写作 / 求职 / 开源 | 2h | build log、联系、PR 或 mock |

建议节奏：

- 周一：定义本周可验收 outcome；阅读官方资料。
- 周二–周四：实现最小 vertical slice；每天保持测试可运行。
- 周五：运行 eval、读 traces、分类失败。
- 周六：修复最高价值 failure，做 DSA/system design。
- 周日：录 demo、写周复盘、排下周唯一重点。

## 2. 时间档位

### 每周 8–10 小时

- 保留主项目、eval 和 DSA；减少框架横向比较与文章频率。
- 每个四周阶段改为六周，预计 16–18 个月。
- 不牺牲测试、安全和复盘来“按时赶完”。

### 每周 25–30 小时

- 基础阶段可压缩，但 gate 不变。
- 增加真实用户访谈、开源贡献、云部署和 mock interview。
- 预计 8–9 个月形成可投递作品；生产经验仍无法纯靠时间压缩。

## 3. 每周 Definition of Done

一周只能在以下条件全部满足时标为 Done：

- 产物可运行，不只是一页笔记。
- tests/evals 有明确 pass/fail；记录命令和环境。
- 至少检查 3 条成功 trace 和 3 条失败 trace。
- 记录质量、延迟或成本中的至少一项变化。
- 写下一个错误判断和一个下周实验。
- 代码/文档已提交到版本控制；是否公开由学习者决定。

## 4. 学习闭环

```text
定义 outcome 与失败边界
→ 建最简单 baseline
→ 写 eval
→ 实现一个改动
→ 重复 trials
→ 读 trace / 做误差分析
→ 保留或回滚
→ 写 ADR / postmortem
```

一次只改一个主要变量。模型、prompt、retriever、tool 和 harness 同时变化，结果无法归因。

## 5. 月度检查点

每 4 周进行 90 分钟 review：

1. Demo：10 分钟，不解释不能运行的部分。
2. Metrics：10 分钟，展示 baseline 与当前值。
3. Trace review：选 2 个成功、3 个失败。
4. Architecture：说明本月新增复杂度是否值得。
5. Security：新增攻击面和控制。
6. Career：本月公开证据、岗位缺口、英文表达。
7. Plan：下月只保留 3 个主要 outcomes。

### 月度评分

每项 0–2，共 12 分：

| 项 | 0 | 1 | 2 |
|---|---|---|---|
| Build | 无可运行产物 | demo 可用 | 可复现、异常路径可用 |
| Eval | 凭感觉 | 有少量测试 | 有版本化 suite、baseline、trials |
| Reliability | happy path | 部分错误处理 | 故障注入、恢复、postmortem |
| Security | 未考虑 | 写了风险 | 权限/隔离/攻击 eval 有证据 |
| Communication | 无输出 | 有笔记 | 英文文档/demo/外部反馈 |
| Career | 无动作 | 零散刷题/投递 | 持续 mock、network、岗位校准 |

- 10–12：正常进入下一阶段。
- 7–9：下一阶段首周补缺口。
- ≤ 6：不升级，缩小范围并重做关键 gate。

## 6. Skills 评分规则

能力不能因为“学完课程”从 L1 升到 L2：

- L1 证据：能闭卷解释、完成引导练习。
- L2 证据：独立实现、测试、可复现。
- L3 证据：部署、eval、SLO、故障、安全和权衡。
- L4 证据：平台抽象、跨项目复用、技术标准、外部采用或带人。

每个评分在 `TRACKER.md` 放证据链接和日期。

## 7. 防止 tutorial hell

- 同一主题最多连续阅读 90 分钟，然后必须写代码或做闭卷解释。
- 新框架只有在当前项目暴露明确痛点时才能加入。
- 收藏资料不算进度；只有产物和能力 gate 算。
- 课程代码必须在 48 小时内脱离教程重写一个变体。
- 无法解释某个抽象替你处理的 state/failure，就回到 raw implementation。

## 8. 成本管理

建议个人阶段预算，不是硬要求：

- Months 1–3：20–50 USD/月；小模型、mock、缓存优先。
- Months 4–8：50–120 USD/月；把费用集中在 eval experiments。
- Capstone：一次性 100–300 USD 上限，先用小规模验证再扩任务数。

规则：

- 每次 run 记录 model、tokens、tool calls 和估算成本。
- 设置 daily/monthly hard cap。
- eval 先跑 5-task smoke，再跑完整 suite。
- 便宜模型负责结构化/分类等简单 stage，但必须以质量阈值验证。
- 不为了“本地模型”而购买昂贵 GPU；先租用或使用已有资源做 profiling。

## 9. 卡住时的诊断顺序

1. Spec：成功标准是否矛盾或含糊？
2. Data：输入是否缺失、过时、污染或权限错误？
3. Grader：是否把正确答案判错？是否可被 hack？
4. Tool：schema、description、error、权限、副作用是否清楚？
5. Harness：context、state、retry、budget、termination 是否错误？
6. Model：能力是否不够？换模型是否在 eval 上改善？
7. Product：这个任务是否根本不该 Agent 化？

把“调 prompt”放在正确层级，而不是默认第一反应。

## 10. 知识保持

- 每周：写 10 张自己的问答卡，只保留会影响设计的知识。
- 每月：闭卷画一张 Agent 系统图，解释每个 trust boundary。
- 每季度：从空目录重建 raw Agent loop 和 eval runner 的核心版本。
- 每半年：删除过时框架笔记，把长期知识抽象成 protocol/pattern/failure。

## 11. 季度市场刷新

每 13 周：

- 从六家目标公司和 4 家相邻公司各采样 2 个岗位，至少 20 个。
- 统计语言、cloud、framework/protocol、distributed systems、eval、安全、年限和领域要求。
- 只根据 ≥ 4 个岗位重复出现的信号调整主课程；单个岗位需求放入可选项。
- 更新 `resources/OFFICIAL_SOURCES.md` 日期和失效链接。

## 12. 何时可以开始投递

满足以下 6 项中的 5 项即可，不必等待 Week 52：

- 2 个可公开、可复现项目
- 1 个 50-task eval suite 和实验报告
- 能在 45 分钟完成目标级别 coding 题
- 能完成 Agent system design mock
- 有 4 个量化 STAR 故事
- 简历经 3 位工程师 review 后定位一致

投递本身是获取市场数据的实验，不是对自我价值的评分。
