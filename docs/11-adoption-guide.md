# 11. v1 / Existing Project → v2

## 0. v2 保留什么、改变什么

v2 以 GitHub v1 为正式基线演化，不把中间未提交的实验包当作版本历史。

继续保留的核心：

- Repository as durable memory；
- Human Gate A / B / C / D；
- Work Item + Spec + Plan 分层；
- Superpowers workflow 不由 Cortex 重复实现；
- cold start / minimum context loading；
- Git / runtime / verification standing rules。

v2 的主要结构变化：

```text
Stage → Milestone
+ Proposal / Gate R
+ Direct Change
+ Human-readable project-state checkpoint
+ 按需 Architecture topics
+ Web ChatGPT File Output Contract
```

下面按迁移动作展开。
## 1. Stage → Milestone

删除正式 Stage 层。

把原 Stage 的：

```text
Goal
Scope / Non-Goals
Acceptance Criteria
Work Item list
```

迁入：

```text
docs/project/roadmap.md
```

作为对应 Milestone。

正式 taxonomy：

```text
Milestone → Work Item → Task
```

## 2. 建立 project-state

新增：

```text
docs/project/project-state.md
```

把它作为 Human-readable durable checkpoint snapshot：说明已经完成到哪个 Milestone/Work Item、当前 Work Item/PR、Next、durable blocker 和 `Last Updated`；同时供新 Agent 恢复坐标。它不是实时 event log。

## 3. 建 Proposal Inbox

```text
docs/proposals/
├── README.md
├── _TEMPLATE.md
├── _PACKAGE_TEMPLATE/
└── _archive/
```

## 4. 加 Gate R

Proposal Review 后不再由 Agent 自动 disposition。

所有 recommendation 都进入 Gate R。

## 5. A–D 语义基本保留

v1 的 Gate A/B/C/D 不需要推翻。

核心只调整：

```text
Stage
→ Milestone
```

Gate A 中：

```text
Stage scope / AC
→ Milestone scope / AC
```

Gate D：

```text
Stage Acceptance
→ Milestone Acceptance
```

## 6. 加 Direct Change

小 bug / UI polish / equivalent refactor 不再被迫建立 Work Item。

## 7. 重构 Architecture

不要把所有技术细节搬进 Markdown。

先建 `architecture/README.md`，按需拆 topic。

## 8. 精简 coding-agent-instructions

v2 starter 默认只保留两个真正按需的详细执行手册：

```text
verification-and-acceptance.md
documentation-lifecycle.md
```

Git / runtime / routing / Human Gates 等 standing behavior 直接常驻 `CLAUDE.md`；Proposal Review schema 放在 Proposal template。只有当项目以后出现“CLAUDE 不适合展开、且不读会系统性做错”的复杂条件规则时，才新增 instruction。

## 9. 迁移 CLAUDE.md

旧项目不要覆盖。

保留：

- project-specific hard boundaries；
- cold start；
- quick run/verify；
- Git/runtime/service/artifact rules；
- security/frozen contract；
- Gate R/A/B/C/D；
- right-sized delivery。

## 10. Web ChatGPT File Output Contract

从长期对话整理成文件时，统一：

- 每个文件有 `Description` 与 `Last Updated`；
- 写正文前先给 Path / Description / Why Needed / Required Headings；
- 简单主题用 single-file Proposal；
- 复杂主题用 README-led Proposal Package；
- Package README 最后生成，只做 overview / navigation / cross-cutting state，不复制 supporting 文件正文。

## 11. Version

GitHub 正式 v1 → 本次正式候选 v2。

不要引用中间未提交实验包的版本号。
