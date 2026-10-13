# TODO

> 只跟踪正式 Work Item。Direct Change 和 Plan Task 都不进 TODO。

## Current Work Item
- [ ] `【WORK-ITEM-ID】` 【标题】
  - Milestone：`【M1 / roadmap anchor】`
  - Goal：【独立 coherent change】
  - Gate / Status：`investigation | spec | gate_a | gate_b | planning | execution | gate_c | blocked`
  - Branch：`【branch】`
  - Spec：`【path / none】`
  - Plan：`【path / none】`
  - Origin Proposal：`【optional】`

## Next
- [ ] `【ID】` 【标题】

## Blocked
- [ ] `【ID】` 【标题】
  - 原因：【...】
  - 等待：【...】

## Done
- [x] `【ID】` 【标题】 — 【日期 / PR】

## Rules
- Milestone 定义在 `docs/project/roadmap.md`。
- Work Item 粒度必须能独立设计/验证/验收。
- Work Item 一个主要 Spec + Plan。
- Task 只在 Plan。
- Direct Change 不进 TODO。
- Gate C accepted 前 Work Item 不 Done。
- Gate D accepted 前 Milestone 不 accepted。
