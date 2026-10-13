# Cortex Protocol — Core Protocol v2

本文定义 Cortex Protocol v2 的协议不变量。

- **MUST / 必须**：协议不变量；
- **SHOULD / 应该**：默认策略；
- **MAY / 可以**：项目可按实际情况调整。

## 1. Formal Taxonomy

正式项目层级只有：

```text
Milestone → Work Item → Task
```

### Milestone

Milestone 是一整层完整用户能力，包含：

- User Capability；
- Definition of Done / Acceptance Criteria；
- Scope / Non-Goals；
- Status；
- 必要的 Work Item 集合。

Milestone 默认在 `docs/project/roadmap.md` 中定义。

### Work Item

Work Item 是一项可以独立设计、实现、验证、验收的 coherent change。

一个 implementation-bearing Work Item **MUST** 有一个主要 Spec 和一个主要 Plan。

### Task

Task 是 Plan 内部 implementation step。

Task **MUST NOT** 进入 `TODO.md`。

### Direct Change

并非每个代码修改都是 Work Item。

小、明确、低风险、无需独立设计与验收的维护改动 **MAY** 走 Direct Change。

Direct Change 不是第四个正式项目层级。

---

## 2. Participants

### Human

Human **MUST** 保留：

- Proposal disposition 的最终确认权（Gate R）；
- 已批准设计变化的最终确认权（Gate A）；
- Work Item Spec 批准权（Gate B）；
- Work Item 真实功能验收权（Gate C）；
- Milestone 最终验收权（Gate D）。

Human **SHOULD NOT** 长期承担 TODO 更新、文档同步提醒、review 调度、服务清理等 housekeeping。

### Web ChatGPT

Web ChatGPT 用于：

- 全新项目 Product Exploration；
- 已有项目的新 capability / direction Exploration；
- 多轮讨论后的文档沉淀。

Web ChatGPT **MUST NOT** 把尚未经过真实 Repository 审查的候选想法描述成已批准 Requirement 或 Current Truth。

### Repository

Repository 是 durable state carrier。

### Coding Agent

Coding Agent 负责：

- cold start；
- reality check；
- Proposal Review；
- change routing；
- Direct Change；
- Work Item engineering；
- verification；
- documentation reconciliation。

### Superpowers

Superpowers 负责需要正式 Work Item 的 change-level engineering workflow。

Cortex **MUST NOT** 为了流程仪式感强迫 Direct Change 生成无价值 Spec / Plan。

---

## 3. Canonical State

### `docs/project/product.md`

保存 authoritative product intent。

### `docs/project/roadmap.md`

保存 approved Milestone、Capability Order、Definition of Done / Acceptance Criteria 和 Milestone status。

### `docs/project/project-state.md`

保存 **Human-readable durable project snapshot**：让 Human 快速理解最近一次可信 checkpoint——已经完成到哪个 Milestone / Work Item、当前正在做什么、相关 PR、Next 与持续 blocker；同时为新的 Coding Agent session 提供恢复坐标。

它不是 live control plane，也不承诺实时反映每个 commit / Gate / Task。更细的 Work Item/Gate 状态由 `TODO.md` 负责，最新工程事实由 Git/PR/code 负责。

Coding Agent **SHOULD** 在 durable checkpoint 自动维护本文件；Human 的主要职责是阅读/判断，不应承担日常状态同步。

典型内容：

- Current Milestone / Current Work Item；
- Active PR / current Human-visible status；
- Latest Accepted Milestone / Work Item / integrated PR；
- Next；
- durable Blockers / Decisions Needed；
- 最近 3–5 个 durable checkpoints；
- `Last Updated`（最后一次 checkpoint reconciliation 日期）。

### `docs/project/architecture/`

保存跨多个 Work Item 仍重要的 long-lived architecture truth / approved baseline。

### `docs/proposals/`

保存尚未完成 Gate R disposition 的候选变化及其审查历史。

### `TODO.md`

只保存正式 Work Item queue/state。

### `docs/superpowers/specs/` / `plans/`

只保存正式 Work Item 的 change-level design / implementation artifacts。

### code / tests / schema / config / Git

保存真实工程事实。

---

## 4. New Project Bootstrap

全新项目先由 Human + Web ChatGPT 收敛：

```text
product.md
roadmap.md
project-state.md
+ only-if-needed architecture baseline
```

Coding Agent 第一次接手后 **MUST** 做 Bootstrap Review，而不是直接把这些文件当作不可质疑事实。

如果只是 starter/config/docs 小修，可以 Direct Change。

第一个真正需要独立设计和验收的 vertical slice 才建立 Work Item。

---

## 5. Proposal Lifecycle

已有项目的新 capability / new direction **SHOULD** 先形成 Proposal。

Proposal 可以是：

```text
docs/proposals/<name>.md
```

或：

```text
docs/proposals/<name>/
├── README.md
└── supporting files...
```

Package 的 `README.md` 是唯一入口和 package-level Review/Disposition 载体。

### 5.1 Coding Agent Review

Proposal Review 至少分两层：

#### Quality Review

检查：

- Problem / Desired Capability 是否合理；
- repo facts 是否准确；
- 是否重复；
- scope 是否 coherent；
- 是否把 candidate implementation 当 requirement；
- assumptions / risks / conflicts；
- 是否需要 Human clarification。

#### Admission Review

在 Quality Review 足够完成后判断：

- Already planned?
- Now?
- Feasible enough?

### 5.2 Recommendation

Coding Agent **MUST** 给出一个明确 recommendation：

```text
START_NOW
ABSORB
DEFER
BLOCK
REJECT
```

它 **MUST** 给出依据。

但 Recommendation **MUST NOT** 自动成为最终 disposition。

---

## 6. Gate R — Proposal Decision

**Trigger:** Coding Agent 已完成足够的 Proposal Review，并形成 recommendation。

Gate R 是每个完成 Review 的 Proposal 的 Human decision point。

Agent **MUST** 提供：

```text
Proposal Summary
Repository Evidence
Review Findings
Recommendation
Reasoning
Impact
Next Action if Accepted
```

不同 Recommendation 还应附加：

### START_NOW

说明：

- 为什么建议现在做；
- 是否影响当前 Milestone；
- 是否需要改变已有 approved design；
- 建议创建/调整哪些 Work Item。

Human 判断：

> **现在开始做吗？**

### ABSORB

说明已被哪个 approved Milestone / Work Item / existing capability 覆盖。

Human 判断：

> **我同意这个“已覆盖”的判断吗？**

### DEFER

说明：

- 为什么现在不做；
- Revisit Trigger。

Human 判断：

> **我同意延后的理由和重新考虑条件吗？**

### BLOCK

说明：

- 当前 blocker；
- 缺少什么 evidence / dependency；
- Recheck Trigger。

Human 判断：

> **我同意当前不能推进的判断吗？**

### REJECT

说明：

- 为什么不建议做；
- 是否与 Product Principle / existing capability / scope 发生根本冲突。

Human 判断：

> **我同意不做的判断吗？**

### Gate R outcomes

Human 可以：

```text
ACCEPT_RECOMMENDATION
OVERRIDE
REQUEST_MORE_REVIEW
REVISE_PROPOSAL
```

在 Human 确认前：

- Proposal **MUST NOT** 被最终归档；
- Roadmap **MUST NOT** 因 recommendation 自动改变；
- implementation **MUST NOT** 自动开始。

Human 确认 Gate R disposition 后，Agent **MUST** 执行对应 Post-decision sync：

- `START_NOW` → 更新 Proposal disposition；如形成新的 Milestone/capability commitment，更新 roadmap；真正创建/激活 Work Item 时更新 `TODO.md` 并形成 project-state checkpoint；
- `ABSORB` → traceability + absorbed disposition；
- `DEFER` → deferred disposition + Revisit Trigger；
- `BLOCK` → blocked disposition + Evidence Needed / Recheck Trigger；
- `REJECT` → rejected disposition + reason；
- `OVERRIDE / REQUEST_MORE_REVIEW / REVISE_PROPOSAL` → 按 Human 决定继续 Review/修 Proposal，不把原 recommendation 当 final truth。

如果 `START_NOW` 要求修改已有 approved design，先进入 Gate A；否则进入 Work Item lifecycle。

---

## 7. Right-sized Change Routing

Coding Agent 收到日常 coding input 后 **MUST** 选择最小正确路径。

### 7.1 Direct Change

满足以下条件时可以 Direct Change：

- 正确目标已清楚；
- 不增加新的独立 capability；
- 不改变已批准 product behavior / state semantics / public contract / security boundary / persistence semantics / long-lived architecture；
- blast radius 小；
- design fork 少；
- 通常可在一个 session 内完成和验证。

流程：

```text
minimal repo inspection
→ change
→ targeted verification
→ review
→ report
```

默认不创建：

```text
Proposal
Work Item
TODO
Spec
Plan
Gate B
Gate C
```

### 7.2 Work Item

当 change 需要：

- 独立设计；
- 多个重要 design fork；
- cross-module contract；
- state/persistence/security/concurrency semantics；
- 跨 session durable coordination；
- 独立 Human acceptance；

应升级为正式 Work Item。

### 7.3 New Capability

真正新 capability / direction：

```text
Proposal → Review → Gate R
```

### 7.4 Approved Design Change

必须改变已批准设计：

```text
Gate A
```

---

## 8. Work Item Lifecycle

```text
Work Item
→ cold start + reality check
→ repo investigation
→ change-level Spec
→ Gate B
→ Plan
→ implementation / tests / review / verification
→ applicable E2E
→ Gate C
→ Work Item Done
→ check Milestone
```

如果任一阶段出现 Design Divergence：

```text
→ Gate A interrupt
```

---

## 9. Gate A — Design Divergence

**Trigger:** 真实工程证据表明已经批准的以下内容需要实质调整：

- `docs/project/` 中的 approved design / product rule / architecture boundary；
- 当前 Milestone 的 capability / scope / Acceptance Criteria；
- 当前 approved change design，例如 Gate B accepted Spec。

Agent **MUST** 立即停止受影响实现并提交：

```text
Original Approved Baseline
Verified Engineering Evidence
Why They Conflict
Suggested Change
Alternatives
Impact
Affected Documents / Milestone / TODO / Spec / Plan
```

在 Human 决定前，Agent **MUST NOT**：

- 继续受影响实现；
- 静默修改 approved semantics；
- 把建议变化写成 Current Truth。

Human 判断：

> **这个已批准的重要设计真的要改吗？**

不是 Gate A：

- implementation 没做到原 Spec；
- 等价 refactor；
- helper/file layout；
- 不改变交互语义的视觉 polish；
- 单纯 test structure 差异。

Gate A accepted 后，Agent **MUST** 先做 owner reconciliation，再重新选择正确执行路径。按实际变化更新：

- product intent → `product.md`；
- Milestone capability/scope/DoD/AC → `roadmap.md`；
- long-lived project/architecture baseline → relevant architecture docs；
- current Work Item approved design → current Spec；
- implementation path → current Plan；
- live Work Item/Gate/Next/blocker → `TODO.md`；
- Human-visible checkpoint → project-state；
- every-session critical boundary/code map/run-verify/standing rule → root `CLAUDE.md`。

只更新实际受影响 owner；Human 决定前不得把 suggested change 写成 approved/current truth。

---

## 10. Gate B — Spec Review

**Trigger:** 正式 Work Item 的 Spec 已收敛。

Agent **MUST** 提供 Spec，并 **SHOULD** 提供简洁 Design Review Packet。

Human 审：

- user/system behavior；
- business flow；
- data/state/control flow；
- source of truth；
- failure semantics；
- persistence/external service boundary；
- invariants；
- important design forks；
- non-goals。

Human 不审：

- 文件怎么拆；
- helper/function name；
- implementation task 顺序；
- 默认 Plan decomposition。

Human 判断：

> **这个系统设计是不是我要的？**

Human accepted 后，Agent **MUST**：

1. 将 current Spec 标记为 accepted / approved baseline；
2. 更新 `TODO.md` 的 live Gate/Status；
3. 创建或更新 current Plan，并以 approved Spec 为 baseline；
4. 通常不更新 project-state；
5. 不因 Gate B accepted 就把 future implementation 写成 `Verified Current` architecture 或 CLAUDE standing truth。

---

## 11. Gate C — Feature / Work Item Acceptance

**Trigger:** Work Item 已完成必要 implementation、自动验证、review 和适用 E2E。

Agent **MUST** 提供：

- 实际完成内容；
- 实际执行过的验证；
- 手动验收场景；
- 操作步骤；
- 预期结果；
- 已知限制；
- 需要保持运行的服务。

Human 判断：

> **这个真实功能是不是我要的？**

Human accepted 前，Work Item **MUST NOT** 标记 Done。

Human accepted 后，Agent **MUST**：
- Work Item 在 `TODO.md` → Done；
- 形成 project-state checkpoint；
- 只把已实际成立、长期有效的事实同步为 `Verified Current` architecture；
- 更新必要 Proposal traceability；
- 若真实实现改变 every-session standing fact，同步 root `CLAUDE.md`；
- 检查 Current Milestone DoD / AC，满足则进入 Gate D。

Direct Change 默认不经过正式 Gate C。

---

## 12. Gate D — Milestone Acceptance

**Trigger:** 当前 Milestone 的 Work Items 与 Definition of Done / Acceptance Criteria 看起来均已满足。

Agent **MUST** 基于：

- Milestone User Capability；
- Acceptance Criteria；
- Work Item final status；
- 当前真实系统 evidence；

说明为什么 Milestone 已完成。

Human 判断：

> **这个 Milestone 承诺的整层用户能力是否完整交付？**

Human accepted 后，Agent **MUST** 执行 Post-decision sync：

- `roadmap.md` 中 Milestone status → accepted / complete；
- project-state 更新 Latest Accepted Milestone、Current Milestone / Next、Recent Checkpoints；
- final reconciliation；
- archive 真正过时的 Milestone-scoped artifacts；
- 若 every-session standing context 改变，同步 root `CLAUDE.md`；
- 然后才能进入下一 Milestone。

---

## 13. Documentation Timing

文档更新 **MUST** 是 event-driven，但 Gate 不是“更新所有文档”的信号。

### Durable fact → Owner

```text
product intent
→ product.md

Milestone commitment / scope / DoD / AC / status
→ roadmap.md

Human-readable delivery checkpoint
→ project-state.md

live Work Item / Gate / Next / blocker
→ TODO.md

approved Work Item behavior/design
→ current Spec

implementation task decomposition/path
→ current Plan

long-lived architecture truth / approved project baseline
→ architecture/*

every-session standing rule / critical boundary / code map / stable run-verify command
→ CLAUDE.md

candidate capability/direction
→ Proposal
```

Human Gate accepted 后，Agent **MUST** 读取/执行对应 Post-decision sync，只更新实际改变的 owner。

`project-state.md` 不追求实时；只在 Work Item activation、PR checkpoint、Gate C/Gate D accepted、durable blocker/pause 等足以改变 Human 对项目状态理解的 checkpoint 更新。单个 commit、Plan Task、Gate B accepted、短暂 test/review 变化通常不触发 project-state。

Direct Change 默认不制造 TODO/Spec/Plan/project-state housekeeping，但如果它真实改变 stable run command 等已有 owner fact，仍更新对应 owner。

---

## 14. Architecture Documentation

`docs/project/architecture/` **MUST NOT** 成为完整技术百科。

可选主题：

```text
system-overview.md
project-structure.md
domain-and-state.md
data-flow.md
interfaces-and-contracts.md
persistence-and-data.md
runtime-and-deployment.md
```

API / DB：

```text
Architecture docs
→ long-lived ownership / boundary / invariant / compatibility / consistency

Source / OpenAPI / Models / Migrations
→ exact machine-readable facts
```

Architecture file **SHOULD** 标：

```text
Verified Current
Approved Baseline
UNDECIDED
```

Work Item future implementation 在 Gate C accepted 前 **MUST NOT** 被描述成 `Verified Current`。

---

## 15. Context Loading

每个判断只加载最小必要上下文。

新 session 通常：

```text
CLAUDE.md
→ project-state（先理解最近一次 Human-readable checkpoint）
→ TODO（获取 live Work Item/Gate state）
→ current Milestone in roadmap
→ relevant architecture
→ current Spec/Plan if any
→ code/tests/config/Git（验证 project-state Last Updated 之后的真实变化）
```

不默认扫描全部 `docs/`、Proposal archive 或 coding guides。

---

## 16. Protocol Invariants

1. **Proposal recommendation 不等于 Human decision；Review 后必须 Gate R。**
2. **重大 approved design 变化不能静默发生；必须 Gate A。**
3. **Spec approval 与 Feature acceptance 是不同判断；分别 Gate B / C。**
4. **Milestone completion 必须经 Gate D。**
5. **正式层级只有 Milestone → Work Item → Task。**
6. **Work Item 一个主要 Spec + 一个主要 Plan。**
7. **Direct Change 不因流程存在而被强迫升级成 Work Item。**
8. **大的/语义性的 change 也不能为了省流程伪装成 Direct Change。**
9. **TODO 只记录 Work Item，不复制 Plan Task。**
10. **Repository state 优先于聊天记忆。**
11. **Cortex 不重复 Superpowers 已负责的工程细节流程。**
12. **只加载当前判断需要的最小上下文。**
