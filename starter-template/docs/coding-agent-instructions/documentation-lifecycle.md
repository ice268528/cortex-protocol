# Documentation Lifecycle

> 在 Work Item / PR / Milestone 形成 durable checkpoint、Human Gate accepted、长期 blocker 变化或 closeout 时读取。核心原则：**先判断哪些 durable facts 真的改变，再更新各自 owner；Gate 不是“更新所有文档”的信号。**

## 1. Durable fact → Owner

| Durable fact | Owner |
|---|---|
| authoritative product intent / product principle | `docs/project/product.md` |
| Milestone commitment / capability / scope / DoD / AC / Milestone status | `docs/project/roadmap.md` |
| Human-readable delivery checkpoint：完成到哪里、当前 Work Item/PR、Next、durable blocker | `docs/project/project-state.md` |
| live Work Item / Gate / Next / blocker | `TODO.md` |
| current Work Item approved behavior / design | current Spec |
| current Work Item implementation task decomposition / execution path | current Plan |
| long-lived architecture truth / approved project baseline | relevant `docs/project/architecture/*` |
| every-session standing rule / critical boundary / minimal code map / stable run-verify command | root `CLAUDE.md` |
| candidate capability/direction + Review/disposition | Proposal item |
| machine-readable engineering fact | source / schema / config / migrations / tests / CI |

更新 owner 时遵守两个限制：
- **不提前写 future truth**：Work Item future design 在 Gate C accepted 前通常留在 Spec/Plan；如果它要求改变已有 approved project/Milestone/change baseline，走 Gate A。
- **不机械复制**：同一事实只在最合适的 owner 维护；其他文档只放必要引用/摘要。

## 2. TODO vs Project State

- `TODO.md` = Agent-facing live Work Item control plane，可随 Work Item/Gate/Next/Blocker 较频繁更新。
- `docs/project/project-state.md` = Human-facing checkpoint snapshot，不追求实时；只在值得 Human 重新理解项目状态的 durable checkpoint 更新。

`project-state.md` **MUST** 在这些 checkpoint 更新并刷新 `Last Updated`：
- Work Item 正式 activated / 切换 Current Work Item；
- active PR 创建，或 PR merged / closed / replaced 且改变当前 Work Item 的 Human-visible 状态；
- Gate C accepted：记录最新 accepted Work Item、对应 PR、Next；
- Gate D accepted：记录最新 accepted Milestone，并切换/清空 Current Milestone；
- 会跨 session 持续存在的 blocker / pause 出现或解除；
- 其他足以改变 Human 对“已经完成到哪里 / 正在做什么 / 下一步是什么”的 durable event。

通常 **不因为以下事件单独更新 project-state**：
- Gate B accepted；
- Plan Task 推进；
- 单个 commit / review fix / test 从 failing 到 passing；
- 短暂 blocker；
- Direct Change。

`Recent Checkpoints` 只保留最近 3–5 条。完整历史以 Git/PR、Roadmap、TODO Done 和 Proposal archive 为准。

## 3. Gate R — Post-decision sync

Gate R pending 时，只更新 Proposal Review / recommendation；recommendation 不是 final disposition。

Human 确认后：
- `START_NOW` → 落 Proposal disposition；如形成新的 Milestone/capability commitment，更新 `roadmap.md`；真正创建/激活 Work Item 时更新 `TODO.md` 并形成 project-state checkpoint。
- `ABSORB` → Proposal traceability + absorbed archive；若发现现有 Roadmap/TODO traceability 本身缺失，只补必要引用，不创建重复 Work Item。
- `DEFER` → deferred archive + Revisit Trigger。
- `BLOCK` → blocked state + Evidence Needed / Recheck Trigger。
- `REJECT` → rejected archive + reason。
- Human `OVERRIDE / REQUEST_MORE_REVIEW / REVISE_PROPOSAL` → 按 Human 决定继续 Review/修 Proposal；不要把原 recommendation 当 final truth。

Human 确认前不最终 archive、不改变 Roadmap commitment、不启动 implementation。

## 4. Gate A — Post-decision sync

Gate A triggered 时：
- 立即停止受影响实现；
- 把 live Gate/blocker/evidence 记录到 `TODO.md`；
- 只有形成跨 session durable pause/blocker 时才更新 project-state；
- Human 决定前不得把 suggested change 写成 approved/current truth。

Gate A accepted 后，**先做 owner reconciliation，再继续实现**：
1. product intent 改变 → `product.md`；
2. Milestone capability/scope/DoD/AC 改变 → `roadmap.md`；
3. long-lived project/architecture baseline 改变 → relevant `architecture/*`；
4. current Work Item approved behavior/design 改变 → current Spec；
5. implementation path/task decomposition 受影响 → current Plan；
6. live Work Item/Gate/Next/blocker 改变 → `TODO.md`；
7. Human-visible checkpoint 改变 → project-state；
8. every-session critical boundary/code map/run-verify/standing rule 改变 → root `CLAUDE.md`。

只更新实际受影响的 owner，不要求每次 Gate A 都改完上述全部文件。

## 5. Gate B — Post-decision sync

Gate B triggered 前，Spec 应已收敛到可供 Human Review 的状态。

Gate B accepted 后：
1. current Spec 标记为 accepted / approved baseline；
2. `TODO.md` 从 `gate_b` 切到 planning/execution 的真实 live status；
3. 创建或更新 current Plan，并以 approved Spec 为 baseline；
4. 通常不更新 project-state；
5. 不因为 Gate B accepted 就把 future implementation 写成 `Verified Current` architecture 或 CLAUDE standing truth。

如果 Human 要求修改 Spec：
- 继续修 Spec 并重新 Gate B；
- 如果修改本身要求改变更上游的 approved project/Milestone baseline → Gate A。

## 6. Gate C — Post-decision sync

Gate C pending 时，Work Item **MUST NOT** Done；future implementation 也不得提前同步成 `Verified Current` architecture。

Gate C accepted 后：
1. `TODO.md` 中 Work Item → Done；
2. project-state 更新 `Completed Through / Current Snapshot / Recent Checkpoints / Next`；
3. 只有已经实际成立、跨多个 Work Item 仍有价值的事实才同步到 architecture 并标记 `Verified Current`；
4. 更新必要 Proposal traceability；
5. 如果真实实现改变了 every-session standing fact（例如 stable run command、minimal code map），同步 root `CLAUDE.md`；
6. 检查 Current Milestone DoD / AC，满足则进入 Gate D。

不要把整个 Spec/Plan 复制进 architecture 或 CLAUDE。

## 7. Gate D — Post-decision sync

Gate D accepted 后：
1. `roadmap.md` 中 Milestone status → accepted / complete；
2. project-state 更新 `Latest Accepted Milestone`、Current Milestone / Next、Recent Checkpoints；
3. 执行必要 final reconciliation / archive；
4. 若 Milestone 完成后 every-session standing context 改变，再同步 `CLAUDE.md`；
5. 然后才能进入下一 Milestone。

## 8. Direct Change

Direct Change 默认只留下 code/tests/Git evidence，不创建 TODO/Spec/Plan，也不机械更新 project-state。

但 Direct Change 如果真实改变了某个已有 owner fact，仍应更新对应 owner。例如：
- stable run/verify command 改变 → `CLAUDE.md`；
- 修正文档中的 factual error → 对应 owner；
- 如果实际需要改变 approved semantics / long-lived boundary，则已不再是 Direct Change，应重新 routing（通常 Gate A / Work Item / Proposal）。

## 9. Metadata

设计文档推荐：
```md
> **Description:** stable responsibility
> **Last Updated:** YYYY-MM-DD
```

`project-state.md` 的 `Last Updated` 表示 Coding Agent 最后一次根据 durable checkpoint 完成状态 reconciliation 的日期，不等于最后一次 commit/test/文字修改。
其他设计文档在实质内容、status 或 conclusion 变化时刷新 `Last Updated`；纯格式化/只读不刷新。README 只在 navigation、file set 或 package-level state 真正变化时更新。
