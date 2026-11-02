# {TASK_OR_SESSION_NAME} 归档记录

> 状态：`Archived`  
> 本文件仅保存历史证据，不是当前任务入口或活动开发指令。现行规则和工作入口以“替代文件”部分为准。

## 1. 归档身份

```text
项目：{PROJECT_NAME}
项目根目录：{PROJECT_ROOT}
任务编号：{TASK_ID}
归档对象：{FILE_OR_SESSION}
原始状态：{ORIGINAL_STATUS}
归档时间：{YYYY-MM-DD HH:mm ZONE}
归档原因：任务完成 / 被新版本替代 / Session切换 / 范围取消 / 其他
负责人：{OWNER}
执行人：{EXECUTOR}
```

## 2. 替代文件与当前入口

| 类型 | 当前有效路径 | 说明 |
|---|---|---|
| 全局规范 | `{CURRENT_GLOBAL_INIT}` | 当前项目级规则 |
| 任务入口 | `{CURRENT_TASK_INIT}` | 当前任务工作流 |
| 最新交接 | `{LATEST_SWITCH}` | 当前继续点 |
| 权威文档 | `{AUTHORITATIVE_DOCS}` | 当前需求、设计和验收 |

替代文件未确认存在且内容完整前不得归档原文件。

## 3. 原始范围与历史背景

```text
原始目标：{ORIGINAL_GOAL}
原始范围：{ORIGINAL_SCOPE}
原始非目标：{ORIGINAL_OUT_OF_SCOPE}
原始基线：{ORIGINAL_BASELINE}
```

原始内容快照或原文件位置：

```text
{ORIGINAL_CONTENT_OR_REFERENCE}
```

## 4. 最终结果与证据

| 事项 | 最终状态 | 证据/提交/文档 | 备注 |
|---|---|---|---|
| {ITEM} | Completed/Cancelled/Superseded/Unresolved | {EVIDENCE} | {NOTE} |

```text
最终分支：{FINAL_BRANCH}
最终提交：{FINAL_COMMITS}
推送/合并/发布状态：{REMOTE_RELEASE_STATUS}
最终验证：{FINAL_VERIFICATION}
```

未执行项不得因归档而改写为通过。

## 5. 转移出去的未完成事项

| 原事项 | 转移到 | 新状态 | 是否已授权 |
|---|---|---|---|
| {TODO} | {NEW_TASK_OR_DOC} | Candidate/Pending | 是/否 |

未被转移的事项视为历史候选，不自动恢复为当前任务。

## 6. 被替代或废弃的决定

| 历史决定 | 新决定 | 替代原因与证据 | 生效版本/提交 |
|---|---|---|---|
| {OLD_DECISION} | {NEW_DECISION} | {REASON} | {VERSION_COMMIT} |

### 不应继续沿用

- {OBSOLETE_ASSUMPTION_OR_INSTRUCTION}
- 归档文件中的路径、分支、提交、配置和环境状态可能已经过期，使用前必须重新验证。

## 7. 历史风险与恢复说明

- 历史已知风险：{RISKS}
- 数据/配置影响：{DATA_CONFIG_IMPACT}
- 外部副作用：{EXTERNAL_SIDE_EFFECTS}
- 如需恢复调查，应从 `{CURRENT_ENTRY}` 新建 Session，而不是直接继续执行归档 Prompt。
- 如需恢复原文，保留本文件并追加恢复记录；不得删除或覆盖历史证据。

## 8. 归档完整性检查

- [ ] 归档对象、时间、原因、负责人和执行人已记录；
- [ ] 当前有效替代文件存在并可独立启动；
- [ ] 需求、实现、测试、提交、推送/发布状态如实区分；
- [ ] 未完成事项已转移或明确保留为未授权候选；
- [ ] 被替代决定及“不应继续沿用”已写明；
- [ ] 原始历史没有删除、压缩或改写；
- [ ] 敏感信息、客户数据和凭据未写入归档；
- [ ] 应用内会话归档状态由负责人另行处理。

## 9. 追加修订记录

| 版本 | 日期 | 修改负责人 | 修改执行人 | 说明 |
|---|---|---|---|---|
| 1.0 | {YYYY-MM-DD} | {OWNER} | {EXECUTOR} | 建立归档记录。 |

