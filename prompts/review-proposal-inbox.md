# Prompt：Review Proposal Inbox → Gate R

```text
请审核 docs/proposals/ 中所有尚未完成最终 disposition 的 Proposal items。

Proposal item 可以是：
- 单个 .md；
- 目录 package，其中 README.md 是入口。

Proposal 是候选输入，不是 Requirement / Approved Design / Current Truth。

对每个 Proposal：

## Phase 1 — Quality Review
结合最小必要的 Product / Roadmap / Project State / TODO / relevant Architecture / real repo evidence 检查：

- Problem / Desired Capability 是否合理；
- repo facts 是否准确；
- 是否重复或已覆盖；
- scope 是否 coherent；
- 是否把 implementation idea 当 requirement；
- assumptions / risks / dependencies 是否清楚；
- 是否和 approved product / architecture / security boundary 冲突；
- 是否需要 Human clarification。

不改变产品意图的事实纠错、结构整理、去重、把 implementation 与 requirement 分开，可以直接修并记录。

如果产品语义本身还无法确定，先向我提出 clarification，不要假装 Review 已完成。

## Phase 2 — Admission Review
Review 足够完成后判断：
1. Already planned?
2. Now?
3. Feasible enough?

然后必须给一个 recommendation：

START_NOW
ABSORB
DEFER
BLOCK
REJECT

对每个 recommendation 给出 evidence 和理由。

## Gate R
Review 完成后必须停在 Gate R，把 recommendation 交给我确认。

- START_NOW：问我“是否现在开始做？”
- ABSORB：问我是否同意“已经被现有能力/计划覆盖”
- DEFER：给 Revisit Trigger，问我是否同意延后理由
- BLOCK：给 blocker + Recheck Trigger，问我是否同意当前不能推进
- REJECT：给理由，问我是否同意不做

在我确认前：
- 不最终 archive；
- 不修改 Roadmap commitment；
- 不创建/启动 Work Item；
- 不开始 implementation。

如果我不同意，我可以要求：
OVERRIDE / REQUEST_MORE_REVIEW / REVISE_PROPOSAL。
```
