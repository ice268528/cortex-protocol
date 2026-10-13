# 03 — 让 ChatGPT 生成项目需求文档

ChatGPT 应先给你 File Plan，再生成内容。

默认三个核心文件：

```text
docs/project/product.md
docs/project/roadmap.md
docs/project/project-state.md
```

示例最终状态：

- [`final-state/docs/project/product.md`](final-state/docs/project/product.md)
- [`final-state/docs/project/roadmap.md`](final-state/docs/project/roadmap.md)
- [`final-state/docs/project/project-state.md`](final-state/docs/project/project-state.md)

`project-state.md` 是 Human-facing 的最近一次可信项目快照，不是实时 event log。它重点回答：已经完成到哪个 Milestone/Work Item、当前 Work Item/PR 是什么、下一步和 durable blocker 是什么，以及最后一次 checkpoint reconciliation 是哪一天。


## Roadmap 里 M1 长什么样

例如：

```text
M1 — Feedback Intake

User Capability:
员工能提交反馈，Support 能看到待处理 Inbox。

Definition of Done:
- Employee can submit
- Feedback durably exists
- Support can view new feedback
- Manual triage works
```

注意：

```text
Milestone
= capability / DoD

不是
= implementation task list
```

## Architecture 现在写什么？

只写已经明确、长期有价值的 boundary。

例如初始可能只确定：

```text
Frontend = Web UI
Backend API owns durable write boundary
Database = UNDECIDED
```

那么只创建一个小 `system-overview.md` 甚至什么都不建都可以。

不要在 Bootstrap 时提前写：

```text
所有 future API
所有 table
所有 data flow
```

这些可以在真正 Work Item 调查时确定。
