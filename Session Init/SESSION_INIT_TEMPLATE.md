# {TASK_NAME} 工作流与开始 Prompt

> 建议Session名称：`{PROJECT_NAME}｜{SESSION_ID}｜{TASK_ID} {TASK_NAME}`
> 任务编号：`{TASK_ID}`  
> 项目：`{PROJECT_ROOT}`  
> 当前状态：`Draft`  
> 本文件定义当前任务范围和启动方式；不自动授权修改代码、Git 或外部系统。

## 1. 上位规范

新 Session 必须完整阅读：

1. `{PROJECT_ROOT}\.codex\Session Init\CODEX_AGENT_INIT.md`；
2. 本文件；
3. 若存在，最新 `{PROJECT_ROOT}\.codex\Session Switch\...md`；
4. 下方列出的权威项目文档和实现证据。

先按指令优先级、适用范围和现行版本核对冲突，不用“更严格”代替判断。初始化还须实际读取适用的用户级规则、工作区/目标目录规则、技能、工程规范、任务编号规范、任务登记与Git规范；真实路径及读取状态填入本地交接，不依赖旧聊天或自动注入。

## 2. 任务登记

```text
任务编号：{TASK_ID}
任务名称：{TASK_NAME}
业务目标：{GOAL}
发起人/负责人：{OWNER}
目标版本或里程碑：{MILESTONE}
当前阶段：{CURRENT_STAGE}
当前审核门禁：{REVIEW_GATE}
任务场景：{现场实施/联调验收/产品重构/功能开发/维护/其他}
专项规则入口及适用边界：{ACTUAL_RULE_PATHS_AND_SCOPE}
应分离的独立任务：{SEPARATE_TASKS_OR_NONE}
混用例外授权：{未授权，或负责人明确授权原文/范围/来源}
原任务暂停与返回点：{RETURN_POINT_OR_NONE}
```

## 3. 当前唯一范围

### 必须完成

- {IN_SCOPE_1}
- {IN_SCOPE_2}

### 明确非目标

- {OUT_OF_SCOPE_1}
- {OUT_OF_SCOPE_2}

### 允许修改

- {ALLOWED_PATH_OR_ARTIFACT}

### 默认禁止修改

- 用户或其他任务已有差异；
- {FORBIDDEN_PATH_OR_ARTIFACT}
- 未经单独授权的公共契约、数据、外部系统、Git历史和发布环境。

## 4. 权威基线与必读材料

```text
分支：{BRANCH}
基线HEAD：{BASELINE_COMMIT}
上游：{UPSTREAM}
已完成相关提交：{RELATED_COMMITS}
需求文档：{REQUIREMENT_DOCS}
架构/边界文档：{ARCHITECTURE_DOCS}
设计/接口文档：{DESIGN_DOCS}
测试/维护文档：{TEST_AND_MAINTENANCE_DOCS}
相关配置/样本：{CONFIG_AND_SAMPLES}
```

不得重新实现已完成阶段。发现缺口时记录证据并采用追加修正。

文档初始化时必须核对：

- `docs/README.md` 是否存在并能指向当前权威文档；
- 项目概述、术语/协议、现有架构、目标架构是否与代码一致；
- 是否需要新建或修订“系统全链路架构与边界”和“系统全链路使用与维护”；
- 当前任务是否已有需求、设计、修改记录、测试验收及版本记录；
- 涉及公共契约、数据或重大取舍时是否需要 ADR、兼容矩阵、迁移或安全文档。

## 5. 当前已确认决定

| 编号 | 决定 | 原因/证据 | 影响范围 | 确认人/日期 |
|---|---|---|---|---|
| D-001 | {DECISION} | {EVIDENCE} | {SCOPE} | {OWNER_DATE} |

## 6. 待确认事项

| 编号 | 问题 | 推荐方案 | 其他选项/影响 | 是否阻塞 |
|---|---|---|---|---|
| Q-001 | {QUESTION} | {RECOMMENDATION} | {TRADEOFF} | 是/否 |

## 7. 实施阶段与验收

| 阶段 | 输出 | 审核条件 | 状态 |
|---|---|---|---|
| 证据审核 | 工作区、调用链、现状差异 | 负责人确认事实与范围 | Draft |
| 需求 | 需求、非目标、风险、验收 | 负责人明确通过 | Pending |
| 设计 | 架构、接口、生命周期、迁移、回滚、测试 | 负责人明确通过 | Pending |
| 实施 | 分批代码与配置 | 每批单独审核 | Pending |
| 验证 | 定向、联动、集成、人工/发布证据 | 结果如实记录 | Pending |
| Git/发布 | 提交、推送、部署 | 分别明确授权 | Pending |

当前任务文档清单：

| 文档类型 | 路径 | 本批动作 | 状态/负责人 |
|---|---|---|---|
| 需求 | {PATH} | 新建/修订/不涉及 | {STATUS_OWNER} |
| 技术/全链路 | {PATH} | 新建/修订/不涉及 | {STATUS_OWNER} |
| 程序设计 | {PATH} | 新建/修订/不涉及 | {STATUS_OWNER} |
| 修改记录 | {PATH} | 追加 | {STATUS_OWNER} |
| 测试与验收 | {PATH} | 追加 | {STATUS_OWNER} |
| 使用维护/发布 | {PATH} | 新建/修订/不涉及 | {STATUS_OWNER} |

验收标准：

- {ACCEPTANCE_1}
- {ACCEPTANCE_2}
- 直接相关前序任务联动审查无未处理回归；
- 文档与实际提交、测试、部署/回滚状态一致。

## 8. Session 名称登记

| 编号 | Session名称 | 状态 | Switch文档 |
|---|---|---|---|
| {SESSION_ID} | `{PROJECT_NAME}｜{SESSION_ID}｜{TASK_ID} {TASK_NAME}` | {真实状态} | {交接路径或尚未生成} |

Session从项目总索引的上一编号接续，不能按每项任务重置为01。完整前后关系只在项目唯一的本地Session README登记，本表仅记录本任务关联。

## 9. 可直接复制的新 Session 开始 Prompt

```text
你正在处理项目“{PROJECT_NAME}”。

项目根目录：
{PROJECT_ROOT}

当前任务：
{TASK_ID} / {TASK_NAME}

首先完整阅读并严格遵守：
1. {PROJECT_ROOT}\.codex\Session Init\CODEX_AGENT_INIT.md
2. {THIS_FILE_ABSOLUTE_PATH}
3. {LATEST_SESSION_SWITCH_OR_NONE}
4. 本文件列出的README、权威规则、需求、架构、设计、测试与维护文档。

补充本机实际适用的用户级规则、工作区及目标目录AGENTS或其他真实名称规则、技能、任务编号/登记及Git规范路径，并按顺序实际读取；记录已读取、尚待读取和未核实状态。若本Prompt用于共享模板，保留占位符；实际个人路径仅填入Git忽略的本地副本。

不要依赖此前聊天记录。首先只读执行：
git status -sb
git log -5 --oneline --decorate
git branch --show-current
git rev-parse HEAD
git remote -v

随后：
1. 校验分支、HEAD、远程同步状态和基线提交；
2. 识别工作区现有差异的归属并保护用户修改；
3. 从真实入口、配置、构造、调用、输出和释放路径建立最短调用链，不凭命名猜测；
4. 汇报已完成架构、当前允许修改和禁止扩大的边界；
5. 完成当前阶段“{CURRENT_STAGE}”的输出，并停在“{REVIEW_GATE}”等待审核。

当前唯一范围：{IN_SCOPE_SUMMARY}
独立任务默认另开会话；如请求将导致混用，先提醒并说明任务、范围、规则、授权边界和返回点，取得负责人明确授权后才执行混用部分。授权不得扩大，“继续”不能代替混用授权。
明确非目标：{OUT_OF_SCOPE_SUMMARY}
已完成且不得重做：{COMPLETED_BASELINE}
需要保护的差异：{DIRTY_WORKTREE_OWNERSHIP}

未经明确授权，不要修改生产代码、创建Git提交、推送、合并、发布、部署或改写历史。TODO不是开发授权；“继续”只推进下一明确批次。
```

## 10. 首次替换示例（占位示意）

```text
{PROJECT_NAME} = 示例项目
{PROJECT_ROOT} = {实际项目绝对路径，仅填入本地任务文件}
{TASK_NAME} = 项目初始化与架构基线
{TASK_ID} = {按该项目已审核编号规则登记}
```

首次使用仍需先调查仓库的真实技术栈、入口、分支和规范，不在模板中预设前后端框架、数据库或部署平台。
