# 06. Human Gates：R / A / B / C / D

Human Gate 的目标不是增加审批，而是把 Human 判断集中到真正有价值的节点。

---

# Gate R — Proposal Decision

## Trigger

Coding Agent 已经完成足够的 Proposal Review，并形成明确 recommendation。

## 关键原则

> **Agent 的 Review Result 不是最终决定。**

无论 Agent 建议：

```text
START_NOW
ABSORB
DEFER
BLOCK
REJECT
```

都必须告诉 Human：

- 审查发现了什么；
- 真实 repo evidence 是什么；
- 为什么给这个 recommendation；
- 接受 recommendation 后下一步是什么。

然后 Human 确认。

## START_NOW

Agent 说明：

- 为什么建议现在做；
- 对当前 Milestone 的影响；
- 是否已经存在前置条件；
- 是否需要改变 approved design；
- 建议的 Work Item 边界。

Human 回答：

> **现在开始做吗？**

## ABSORB

Agent 说明：

- 已经被哪个 Milestone / Work Item / existing capability 覆盖；
- Proposal 中还有没有未覆盖 residual scope。

Human 回答：

> **我同意它已经被覆盖了吗？**

## DEFER

Agent 说明：

- 为什么现在不做；
- Revisit Trigger。

Human 回答：

> **我同意延后的理由和重新考虑条件吗？**

## BLOCK

Agent 说明：

- blocker；
- 还缺什么 evidence / dependency；
- Recheck Trigger。

Human 回答：

> **我同意当前不能推进的判断吗？**

## REJECT

Agent 说明：

- 不建议做的理由；
- 与 product principle / scope / existing capability 的冲突。

Human 回答：

> **我同意这个“不做”的判断吗？**

## Human 可以不同意

Gate R outcome：

```text
ACCEPT_RECOMMENDATION
OVERRIDE
REQUEST_MORE_REVIEW
REVISE_PROPOSAL
```

**未经 Human 确认，不自动 archive / Roadmap admission / implementation。**

## Post-decision sync

Human 确认后：
- `START_NOW`：落 Proposal disposition；如形成新的 Milestone/capability commitment，更新 Roadmap；Work Item 真正 activated 时再更新 TODO + project-state checkpoint；
- `ABSORB`：traceability + absorbed disposition；
- `DEFER`：deferred disposition + Revisit Trigger；
- `BLOCK`：blocked disposition + Evidence Needed / Recheck Trigger；
- `REJECT`：rejected disposition + reason；
- Human 要求更多 Review / 修改 Proposal 时，不把原 recommendation 当最终 truth。

---

# Gate A — Design Divergence

## Trigger

实际工程证据表明已经批准的：

- project design；
- 当前 Milestone capability / scope / Acceptance Criteria；
- current approved change design（如 Gate B accepted Spec）；

需要实质修改。

## Agent Packet

```text
Original Approved Baseline
Verified Engineering Evidence
Why They Conflict
Suggested Change
Alternatives
Impact
Affected durable owners (product / roadmap / architecture / Spec / Plan / TODO / project-state / CLAUDE as applicable)
```

## Human

回答：

> **这个已批准的重要设计真的要改吗？**

Gate A 是 interrupt。

## Post-decision sync

Gate A pending 时只记录 live blocker/evidence；Human 决定前不把建议改动写成 approved/current truth。

Human accepted 后先按 durable fact 更新受影响 owner，再继续：
- Product intent → `product.md`
- Milestone scope/AC/DoD → `roadmap.md`
- long-lived architecture baseline → `architecture/*`
- current Work Item approved design → Spec
- implementation path → Plan
- live Work Item/Gate/Next/blocker → `TODO.md`
- Human-visible checkpoint → `project-state.md`
- every-session critical boundary/code map/run-verify/standing rule → `CLAUDE.md`

不是每次 Gate A 都修改全部文件，只更新真实受影响 owner。

## Examples

| 情况 | Gate A? |
|---|---:|
| 文件拆分改变，行为不变 | No |
| DB column 改名，语义不变 | No |
| approved state machine 必须新增核心状态 | Yes |
| 真实 provider 不支持 approved product behavior | Yes |
| 当前 Work Item 必须突破 Milestone scope 才成立 | Yes |
| 单纯 implementation bug | No |
| pure visual polish | No |

---

# Gate B — Spec Review

## Trigger

正式 Work Item Spec 收敛。

Agent 提供：

- Spec；
- 简洁 Design Review Packet。

Human 重点看：

```text
业务流程
用户行为
数据/状态/control flow
source of truth
failure semantics
persistence/external boundary
invariants
important design forks
non-goals
```

不看：

```text
文件怎么拆
helper 怎么命名
task 顺序
默认 Plan decomposition
```

Human 回答：

> **这个系统设计是不是我要的？**

## Post-decision sync

Gate B accepted 后：
1. Spec 标记 accepted / approved baseline；
2. TODO 更新 live status；
3. 创建/更新 Plan，以 approved Spec 为 baseline；
4. 通常不更新 project-state；
5. 不提前把 future implementation 写进 `Verified Current` architecture 或 CLAUDE standing truth。

如果 Human 要求修改 Spec，则继续修改并重新 Gate B；如果修改要求改变更上游 approved baseline，进入 Gate A。

---

# Gate C — Feature / Work Item Acceptance

## Trigger

Work Item：

- implementation 完成；
- 必要自动验证完成；
- review/fix 完成；
- 适用 E2E 完成。

Agent 提供：

- 实际完成内容；
- 实际执行过的 verification；
- Human 手动场景；
- 操作步骤；
- expected result；
- known limitations。

Human 回答：

> **这个真实功能是不是我要的？**

accepted 前不得 Work Item Done。

## Post-decision sync

Gate C accepted 后：
- TODO 中 Work Item → Done；
- project-state 形成 Work Item checkpoint；
- 只把已实际成立、跨 Work Item 长期有价值的事实同步为 `Verified Current` architecture；
- 更新必要 Proposal traceability；
- 若真实实现改变 stable run command / minimal code map / critical standing boundary，同步 `CLAUDE.md`；
- 检查 Milestone DoD/AC，满足则进入 Gate D。

Direct Change 默认不需要正式 Gate C。

---

# Gate D — Milestone Acceptance

## Trigger

当前 Milestone 的：

```text
Work Items
+
Definition of Done / Acceptance Criteria
```

都有 evidence。

Agent 提供：

- Milestone User Capability；
- AC / DoD 逐条证据；
- Work Item final states；
- 当前真实系统与 Milestone promise 的对应；
- known limitation / deferred scope。

Human 回答：

> **这个 Milestone 承诺的整层用户能力完整交付了吗？**

accepted 后执行 Post-decision sync：

- roadmap Milestone status → accepted；
- project-state 更新 Latest Accepted Milestone / Current Milestone / Next / Recent Checkpoints；
- final reconciliation；
- archive 过时 Milestone-scoped artifact；
- 如 every-session standing context 改变，同步 `CLAUDE.md`；
- 然后 move to next Milestone。

---

# 五 Gate 之间的关系

```text
Proposal
→ Review
→ R

Work Item
→ Spec
→ B
→ Implementation
→ C

Design Divergence anywhere after approved baseline exists
→ A

Milestone complete
→ D
```

其中：

> **A 是 interrupt；R 是 Proposal decision；B/C 是 Work Item design/acceptance；D 是 Milestone acceptance。**
