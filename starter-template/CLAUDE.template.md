# CLAUDE.md

> 本文件按 Cortex Protocol 组织项目级 Agent standing policy；不要在这里重复 Superpowers 已经负责的 change-level workflow。
## 1. 项目概览
【用 3～5 行说明：这是什么系统、核心用户、核心流程、最重要的业务边界。】

代码结构：
- `【frontend】`：前端应用
- `【backend】`：后端服务
- `【agents/workers】`：AI Agent / 异步任务（如有）
- `【tests】`：自动化测试
- `docs/project/`：当前长期项目设计
- `docs/stages/`：Stage 与 Work Item
- `docs/superpowers/`：Superpowers spec / plan
- `docs/coding-agent-instructions/`：按需加载的开发规则
- `docs/coding-guides/`：仅用户明确要求时读取的技术参考
- `TODO.md`：当前 Work Item 状态

跨模块理解代码组织时，按需读取：
`docs/coding-agent-instructions/repository-and-code-organization.md`

## 2. 新会话冷启动
开始修改前：
1. 检查当前 branch/worktree 和 `git status`。
2. 读取 `TODO.md`，确认 Current Work Item。
3. 读取该 Work Item 所属 Stage。
4. 只读取与当前任务相关的 `docs/project/` 文档。
5. 检查相关代码、测试、配置和实际依赖版本。
6. 当前任务已有对应 Superpowers spec/plan 时，读取相关文件。

不要默认扫描全部 `docs/`。
不要默认读取 `docs/coding-guides/`。

## 3. 启动与基础验证
- 前端：`【启动命令】`
- 后端：`【启动命令】`
- Docker：`【启动命令】`
- 基础测试：`【测试命令】`
- 完整验证：`【完整验证命令】`

需要决定测试范围或完整验证方式时读取：
`docs/coding-agent-instructions/testing-and-verification.md`

## 4. 文档职责
- `docs/project/`：系统当前应该是什么样。
- `docs/stages/`：Stage、Work Item 与 Acceptance Criteria。
- `TODO.md`：项目级 Work Item 队列和状态，不记录 implementation tasks。
- `docs/superpowers/specs/`：当前 change 的工程设计。
- `docs/superpowers/plans/`：当前 change 的代码实施计划。
- `docs/coding-guides/`：按用户要求读取的具体技术参考。

## 5. Human Gates
### Gate A — Design Divergence
如果实际工程证据表明已批准的项目设计、Stage 划分或当前 change 设计需要实质性调整，立即停止并请求用户审查。
至少说明：
- 原设计是什么；
- 已验证的工程证据是什么；
- 为什么两者冲突；
- 建议如何调整以及理由；
- 可行 alternatives；
- 哪些 `docs/project/`、`docs/stages/`、`TODO.md` 或当前 spec/plan 受影响。
未经用户确认，不继续推进受该偏差影响的实现，也不静默修改重大设计。

### Gate B — Spec Review
Superpowers 到达 Spec Review Gate 时，除提供 spec 外，再提供一份简洁的 Design Review Packet，帮助用户判断“这个系统设计是不是我要的”。
按当前 change 实际相关性说明业务流程、数据流、状态变化、关键计算、persistence、external service interaction；AI Agent 功能还应说明 context、tools、state、output 和最终 decision ownership。
只说明有助于审查的内容；不适用的内容省略，不为补全说明而推测或编造。
等待用户明确批准 spec 后再进入 plan。Plan 默认不需要人工 review；如果 plan/implementation 暴露重大上游设计偏差，进入 Gate A。

### Gate C — Feature Acceptance
当前 Work Item 完成必要实现、自动验证、review 和适用的 E2E 验证后，停止并请求用户进行功能验收。
说明本次实现内容、已完成的验证，以及需要用户手动检查的功能、操作方式和预期结果。

### Gate D — Stage Acceptance
当当前 Stage 的 Work Items 和 Acceptance Criteria 均已满足时，停止并请求用户进行 Stage 验收。
只有用户明确 accepted 后，才能执行 Stage 收尾和归档。

## 6. 按需加载规则
- Git 写操作、branch/worktree、commit、push、PR、merge、rebase、reset：读取 `docs/coding-agent-instructions/git-management.md`
- 设计偏差、Work Item/Stage 推进或收尾：读取 `docs/coding-agent-instructions/work-item-and-stage-lifecycle.md`
- 启停前后端、Docker、数据库、临时服务或人工测试环境：读取 `docs/coding-agent-instructions/runtime-and-services.md`
- 测试范围和完整验证：读取 `docs/coding-agent-instructions/testing-and-verification.md`
- Playwright、E2E、人工功能验收：读取 `docs/coding-agent-instructions/e2e-and-human-acceptance.md`
- 更新或归档项目文档：读取 `docs/coding-agent-instructions/documentation-lifecycle.md`
- 跨模块理解代码结构：读取 `docs/coding-agent-instructions/repository-and-code-organization.md`
- `docs/coding-guides/`：仅用户明确指定具体 guide 或实现点时读取。

## 7. Gate 后主动 Reconcile
- Gate A approved：主动判断并同步真正受影响的 project/stage/TODO/spec/plan，无需等待用户点名文件。
- Gate C accepted：将 Work Item 标记为 Done，并沉淀仍长期有效的新事实。
- Gate D accepted：执行 final reconciliation、归档过时 Stage-scoped 文档、更新必要 README/index，再进入下一 Stage。
- 不为了形式一致无关地重写未受影响文档。

## 8. 常驻约束
- 不同 Work Item 不混在同一开发 branch/worktree。
- Commit 描述统一使用中文；完整 Git 规则见 `git-management.md`。
- 不丢弃、覆盖、reset 或提交不属于当前 Work Item 的修改。
- 只关闭当前任务由 Agent 启动的服务和临时进程。
- 人工测试期间保持必要服务运行；用户测试完成后关闭不再需要的 Agent-owned 服务。
- 未完成必要验证和对应 Human Gate，不得宣称 Work Item 或 Stage 完成。
