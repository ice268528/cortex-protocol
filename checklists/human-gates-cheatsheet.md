# Human Gates Cheat Sheet

| Gate | Trigger | Human 判断 | Accepted / Confirmed 后 Agent 自动同步 |
|---|---|---|---|
| **R** | Proposal Review 已形成 Recommendation | 我同意 Agent 对这个 Proposal 的 disposition 判断吗？ | Proposal disposition；`START_NOW` 按需 Roadmap，Work Item activated 时 TODO + project-state |
| **A** | approved project/Milestone/change design 必须实质改变 | 这个已批准设计真的要改吗？ | 只同步实际受影响 owner：product / roadmap / architecture / Spec / Plan / TODO / project-state / CLAUDE |
| **B** | 正式 Work Item Spec 收敛 | 这个系统设计是不是我要的？ | Spec → accepted；TODO live status；创建/更新 Plan；通常不改 project-state |
| **C** | Work Item implementation/verification/review 完成 | 这个真实功能是不是我要的？ | TODO Done；project-state checkpoint；Verified Current architecture；必要 Proposal/CLAUDE reconciliation |
| **D** | Milestone Work Items + DoD/AC 均有 evidence | 这一整层用户能力完整交付了吗？ | Roadmap accepted；project-state checkpoint；closeout；必要 CLAUDE reconciliation |

## Gate R

无论 recommendation 是：

```text
START_NOW
ABSORB
DEFER
BLOCK
REJECT
```

都必须让 Human 确认。Recommendation 不是 final disposition。

## Gate A

不是 happy-path stage，是 interrupt。Human 决定前不能把 suggested change 写成 approved/current truth。

## Gate B

Gate B accepted 的核心是 **Spec 成为 approved baseline**。不要因为 accepted 就把未来实现提前写成 `Verified Current` architecture。

## Gate C / D

这两个 Gate accepted 都是明确的 Repository reconciliation checkpoint：
- C = Work Item closeout；
- D = Milestone closeout。

## Direct Change

小改默认不经过 B/C。

如果它揭示 approved design 必须改变，仍然可以触发 A。Direct Change 如果真实改变 stable run command 等已有 owner fact，仍更新对应 owner。
