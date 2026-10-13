# 13. 文档什么时候更新？

v2 采用 event-driven update。核心不是“哪个 Gate 要改哪些固定文件”，而是：

> **Gate / checkpoint 让某个 durable fact 正式成立时，Coding Agent 更新这个 fact 的 owner。**

## Durable fact → Owner

| Durable fact | Owner |
|---|---|
| authoritative product intent / product principle | `product.md` |
| Milestone commitment / capability / scope / DoD / AC / status | `roadmap.md` |
| Human-readable delivery checkpoint | `project-state.md` |
| live Work Item / Gate / Next / blocker | `TODO.md` |
| approved Work Item behavior / design | current Spec |
| implementation path / Task decomposition | current Plan |
| long-lived architecture truth / approved project baseline | `architecture/*` |
| every-session standing rule / critical boundary / minimal code map / stable run-verify command | root `CLAUDE.md` |
| candidate capability/direction + Review/disposition | Proposal |
| machine-readable engineering fact | source/schema/config/migrations/tests/CI |

不要因为 Gate 到了就机械更新全部文档；只更新实际改变的 owner。

## Gate / checkpoint matrix

| Event | Post-decision / checkpoint sync |
|---|---|
| Gate R pending | Proposal Review / recommendation only；不改 final disposition / roadmap commitment |
| Gate R confirmed | Proposal disposition；`START_NOW` 按需更新 roadmap，Work Item activated 时 TODO + project-state |
| Gate A triggered | TODO live blocker/evidence；durable pause 时 project-state；不改 approved truth |
| Gate A accepted | 更新实际受影响的 product / roadmap / architecture / Spec / Plan / TODO / project-state / CLAUDE owner |
| Gate B accepted | Spec → accepted；TODO live status；创建/更新 Plan；通常不改 project-state |
| PR opened / merged / closed / replaced | 如果改变 Human-visible Work Item checkpoint，则更新 project-state |
| Gate C accepted | TODO Work Item Done + project-state checkpoint + Verified Current architecture（如适用）+ standing CLAUDE fact（如适用） |
| Gate D accepted | roadmap Milestone accepted + project-state checkpoint + closeout + standing CLAUDE fact（如适用） |

## Project State checkpoint policy

`project-state.md` 由 Coding Agent 在 durable checkpoint 自动维护；Human 主要用于快速阅读，不承担日常同步。

它重点回答：

```text
已经完成到哪个 Milestone / Work Item？
当前正在做哪个 Work Item？
对应哪个 PR？
下一步是什么？
有没有持续 blocker / decision needed？
这份 snapshot 最后什么时候 reconcile？
```

以下通常不单独触发 project-state 更新：

```text
单个 commit
Plan Task 推进
Gate B accepted
短暂 test failure
review fix
Direct Change
```

`Recent Checkpoints` 只保留最近 3–5 条；完整历史留在 Git/PR、Roadmap、TODO Done、Proposal archive。

`Last Updated` 表示 Coding Agent 最后一次基于 durable checkpoint 完成 project-state reconciliation 的日期。

## CLAUDE.md 的更新条件

`CLAUDE.md` 不是普通 project status 文档。只有 every-session 都不能漏的 standing fact 真正改变时才更新，例如：

- project identity / critical boundary；
- minimal code map；
- stable Start / Fast verification / Full verification command；
- repository-wide safety/contract rule。

如果一个 Work Item 只是提出 future design，不要提前把它写进 CLAUDE。若它改变已有 standing boundary，应先经过相应 Human Gate（通常 Gate A），待 decision/implementation 达到正确状态后同步。

## Direct Change

默认不创建：

```text
TODO
Spec
Plan
Gate state
```

也不机械更新 project-state。

但 Direct Change 仍可能更新已有 owner，例如 stable run command 真实改变时应更新 `CLAUDE.md`。如果需要改变 approved semantics / architecture boundary，则已不是 Direct Change，应重新 routing。

## Metadata

设计文档推荐：

```md
> **Description:** stable responsibility
> **Last Updated:** YYYY-MM-DD
```

实质内容变化才刷新日期；纯格式化/只读不刷新。

README 只在 index/navigation/package-level state 真正变化时更新。
