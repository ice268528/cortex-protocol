# Git Management

本文件集中定义 Git 管理要求，便于不同公司或仓库独立替换。

## 1. Work Item 隔离
- 不同 Work Item 使用不同 branch/worktree。
- 不在同一分支混入无关功能、修复或文档变化。
- 开始新 Work Item 前确认 base branch、当前 branch/worktree 和 `git status`。
- 发现来源不明或不属于当前 Work Item 的修改时，先确认归属，不覆盖、不清理、不顺手提交。

## 2. 分支命名
默认使用 ASCII：
`<type>/<work-item-id>-<short-description>`

常用 type：`feat`、`fix`、`refactor`、`test`、`docs`、`chore`

示例：
- `feat/claim-04-ai-assessment`
- `fix/claim-07-retry-state`

若仓库已有更具体约定，以仓库现有约定为准。

## 3. Commit
Commit 的自然语言描述统一使用中文，推荐：
`<type>(<scope>): <中文描述>`

示例：
- `feat(agent): 实现理赔上下文组装`
- `fix(claim): 修复状态重复推进`
- `test(document): 补充多页文档解析回归测试`
- `docs(project): 修正理赔数据流设计`

要求：
- 一个 commit 表达一个 coherent change；
- 不把无关修改塞进同一 commit；
- 不擅自改写已共享历史。

## 4. PR
正常 feature/fix 默认通过 PR 集成：
1. 独立 branch/worktree 完成当前 Work Item；
2. 完成必要验证；
3. push；
4. 创建 PR。

除非用户明确要求，不直接合入 base branch。
一个 PR 原则上对应一个 Work Item，或经明确确认的紧密相关变更集合。

PR 描述至少说明：做了什么、为什么、如何验证；存在风险、限制或后续事项时一并说明。

## 5. Review 复用
当前 PR HEAD 已完成等价且干净的最终 review 时，不因“刚创建 PR”机械重复完整 review。
HEAD、相关实现或 review 前提发生变化后，再按需重新 review。

## 6. Git 安全
未经用户明确授权，不执行：
- force push；
- destructive reset；
- 丢弃用户或其他 Agent 的本地修改；
- 重写共享历史；
- 删除无法确认归属的 branch/worktree；
- 将无关文件混入当前 commit/PR。

任何可能破坏他人工作或不可逆的 Git 操作，都应先确认。
