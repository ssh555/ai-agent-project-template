# Session {FROM_NO} 到 Session {TO_NO}：{TASK_NAME} 阶段交接

> 本文件必须自包含，使新 Session 不依赖旧聊天即可继续。  
> TODO 不构成开发授权；交接不代表任务完成、Git已提交或应用内会话已归档。

## 1. Session 身份

```text
项目：{PROJECT_NAME}
项目根目录：{PROJECT_ROOT}
任务编号：{TASK_ID}
来源Session：Session {FROM_NO} / {FROM_SESSION_NAME}
目标Session：Session {TO_NO} / {TO_SESSION_NAME}
交接时间：{YYYY-MM-DD HH:mm ZONE}
创建人：{AUTHOR}
```

目标 Session 必须完整阅读：

1. `{GLOBAL_INIT}`；
2. `{TASK_INIT}`；
3. 必须保留的历史 Switch：{PREVIOUS_SWITCHES}；
4. 本文件；
5. {AUTHORITATIVE_DOCS_AND_CODE}。

## 2. Git 与工作区快照

```text
当前分支：{BRANCH}
HEAD：{HEAD}
上游：{UPSTREAM}
领先/落后：{AHEAD_BEHIND}
最近相关提交：{COMMITS}
提交状态：{NOT_COMMITTED/COMMITTED/PUSHED}
```

交接时 `git status -sb`：

```text
{GIT_STATUS_OUTPUT}
```

差异归属和保护清单：

| 路径 | 状态 | 归属 | 是否与本任务相关 | 新Session处理规则 |
|---|---|---|---|---|
| {PATH} | M/A/?? | 用户/本任务/其他任务 | 是/否 | 保留/可继续/禁止触碰 |

## 3. 当前目标、阶段与授权

```text
最终目标：{GOAL}
当前阶段：{CURRENT_STAGE}
阶段状态：Draft / Approved / Implementing / Blocked / Completed
当前审核门禁：{REVIEW_GATE}
已获授权：{AUTHORIZED_ACTIONS}
尚未授权：{UNAUTHORIZED_ACTIONS}
明确非目标：{OUT_OF_SCOPE}
```

## 4. 已完成内容

| 批次/事项 | 实际结果 | 修改文件 | 提交ID | 审核状态 |
|---|---|---|---|---|
| {BATCH} | {RESULT} | {FILES} | {COMMIT_OR_NONE} | {STATUS} |

不得重新实施上述完成项。若发现缺口，以追加修正记录处理。

## 5. 关键架构、契约和决定

| 编号 | 决定/契约 | 证据 | 影响 | 不得误解为 |
|---|---|---|---|---|
| D-001 | {DECISION} | {EVIDENCE} | {IMPACT} | {NON_IMPLICATION} |

当前最短调用链：

```text
{ENTRY} → {CONFIG} → {CORE} → {OUTPUT} → {LIFECYCLE_END}
```

## 6. 验证证据

| 命令/人工步骤 | 配置与输入 | 真实结果 | 日期 | 覆盖范围 |
|---|---|---|---|---|
| `{COMMAND}` | {INPUT} | PASS/FAIL/BLOCKED + 摘要 | {DATE} | {SCOPE} |

未执行或不能宣称通过：

- {NOT_RUN_ITEM}
- {ENVIRONMENT_LIMITATION}

直接相关前序联动审查：

- {PREDECESSOR}: {RESULT_AND_EVIDENCE}

## 7. 未解决问题与失败尝试

| 问题 | 复现条件/证据 | 已尝试 | 为什么无效 | 下一建议 |
|---|---|---|---|---|
| {ISSUE} | {EVIDENCE} | {ATTEMPT} | {WHY_FAILED} | {NEXT_ACTION} |

不要无证据重复失败尝试。环境、权限或外部状态阻塞必须与代码缺陷区分。

## 8. 下一精确步骤

1. {NEXT_STEP_1}
2. {NEXT_STEP_2}
3. 到达 `{NEXT_REVIEW_GATE}` 后停止并等待负责人审核。

候选 TODO（不构成授权）：

- {FUTURE_TODO}

## 9. 回滚、风险与注意事项

- 回滚基线：{ROLLBACK_BASELINE}
- 配置/数据回滚：{CONFIG_DATA_ROLLBACK}
- 外部副作用：{EXTERNAL_SIDE_EFFECTS}
- 敏感信息或现场限制：{SECURITY_CONSTRAINTS}
- 已知风险：{RISKS}

## 10. 目标 Session 开始 Prompt

```text
继续项目“{PROJECT_NAME}”的任务“{TASK_ID} / {TASK_NAME}”。

项目根目录：{PROJECT_ROOT}
当前Session：Session {TO_NO} / {TO_SESSION_NAME}

首先完整阅读：
{GLOBAL_INIT}
{TASK_INIT}
{PREVIOUS_SWITCHES}
{THIS_SWITCH_FILE}
{AUTHORITATIVE_DOCS_AND_CODE}

不要依赖旧聊天记录。首先只读执行：
git status -sb
git log -5 --oneline --decorate
git branch --show-current
git rev-parse HEAD
git remote -v

核对HEAD、远程同步、提交基线和差异归属。保护交接清单中的用户及其他任务改动，不重新实施已完成批次。

当前阶段：{CURRENT_STAGE}
下一精确步骤：{NEXT_STEP_1}
当前审核门禁：{NEXT_REVIEW_GATE}
已获授权：{AUTHORIZED_ACTIONS}
尚未授权：{UNAUTHORIZED_ACTIONS}

先报告恢复核对结果，再执行获准的下一批；完成后联动审查直接相关前序任务，并按真实结果同步相关文档。未经明确授权不要提交、推送、合并、发布、部署或改写历史。
```

## 11. 交接完整性检查

- [ ] Session 编号连续且名称准确；
- [ ] 全局 Init、任务 Init、历史 Switch 和权威文档路径有效；
- [ ] Git 基线、远程状态、提交和差异归属来自当前命令；
- [ ] 已完成、未完成、未执行和失败项严格区分；
- [ ] 已记录关键决定、调用链、风险和失败尝试；
- [ ] 下一步只有一个清晰入口，且审核门禁明确；
- [ ] 开始 Prompt 可脱离旧聊天独立使用；
- [ ] 任务 Session Init 的 Session 名称登记表已同步。

