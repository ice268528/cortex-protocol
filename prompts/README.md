# Cortex Protocol v2 — Prompt Pack

Prompt 是 **Human 的快捷指令和纠偏工具**，不是 Coding Agent 理解 Cortex Protocol 的必要依赖。

正常情况下，Coding Agent 应仅凭 `CLAUDE.md`、Repository truth、Proposal/Spec/Plan 和按需 instruction 自动完成 routing、触发 Gate，并生成相应 Packet。只有当你想**主动发起一个流程、明确当前意图，或让 Agent 重新按协议组织结果**时，才需要复制这里的 Prompt。

---

## 先按你的场景选择

| 你现在的情况 | 推荐 Prompt | 它解决什么 |
|---|---|---|
| 刚开始一个全新项目 | [`chatgpt-project-bootstrap.md`](chatgpt-project-bootstrap.md) | 先和 Web ChatGPT 讨论产品，再按 File Output Contract 生成 Product / Roadmap / Project State / optional Architecture |
| 项目文档已生成，第一次交给 Coding Agent | [`first-handoff-to-claude-code.md`](first-handoff-to-claude-code.md) | 让 Agent Cold Start + Bootstrap Review，并选择 Direct Change 或第一个正式 Work Item |
| 已有项目，想探索一个新功能/方向 | [`chatgpt-exploration-to-proposal.md`](chatgpt-exploration-to-proposal.md) | 把多轮 Web ChatGPT 讨论整理成 Proposal，而不是直接变成 Requirement |
| Proposal 已放进 Repository，准备让 Agent 审查 | [`review-proposal-inbox.md`](review-proposal-inbox.md) | 做 Quality Review + Admission Review，并停在 Gate R |
| Agent 给了 Gate R 结论，但解释不够清楚 | [`gate-r-proposal-decision.md`](gate-r-proposal-decision.md) | 要求重新给出 evidence、recommendation、理由和不同 disposition 的后果 |
| 正在做 Work Item，突然有新想法 | [`mid-flight-idea.md`](mid-flight-idea.md) | 防止 silent scope expansion，让 Agent 在 Plan-local / Direct Change / Work Item / Gate A / Proposal 之间重新 routing |
| 遇到 bug、真实使用反馈或小 UI 修改 | [`test-or-use-feedback.md`](test-or-use-feedback.md) | 优先判断是否可 Direct Change；不满足再升级到正确路径 |
| 明确就是一个很小的改动 | [`direct-small-change.md`](direct-small-change.md) | 快速确认 Direct Change 条件，避免机械创建 Work Item / Spec / Plan |
| 已经到某个 Human Gate，但 Agent 输出不够好审 | 对应 Gate Prompt | 让 Agent重新整理 Review / Acceptance Packet，而不是改变 Gate 本身 |

---

# 一、New Project

## `chatgpt-project-bootstrap.md`

**什么时候用：**  
你只有项目想法，还没有稳定的 `product.md / roadmap.md / project-state.md`。

**它会做什么：**
- 先和 Web ChatGPT 多轮讨论 Target User、Problem、Core Experience、Product Principles、M1 Capability、DoD/AC、Non-Goals；
- 不急着决定 database / queue / provider / framework；
- 只有 Human 明确说“整理成文件”后，才按 File Output Contract 输出项目文档；
- Architecture 只生成真正需要提前确定的长期 baseline。

**结束状态：**  
得到可放入 Repository 的 project docs；还没有自动创建正式 Work Item。

→ [`打开 Prompt`](chatgpt-project-bootstrap.md)

---

## `first-handoff-to-claude-code.md`

**什么时候用：**  
新项目的 project docs 已经放进 Repository，准备第一次让 Coding Agent 接手。

**它会做什么：**
- 按 `CLAUDE.md` Cold Start；
- 对 Product / Roadmap / Project State 与真实 repo 做 Bootstrap Review；
- challenge factual error 和过早技术决定；
- 小 starter/config/docs 修正允许 Direct Change；
- 识别第一个真正需要独立设计/验收的 vertical slice。

**结束状态：**  
如果需要正式 Work Item，做到 `Investigation → Spec` 并停在 **Gate B**；不会一次规划完整 Milestone backlog。

→ [`打开 Prompt`](first-handoff-to-claude-code.md)

---

# 二、Existing Project：新 capability / direction

## `chatgpt-exploration-to-proposal.md`

**什么时候用：**  
已有项目中出现一个新 capability / direction，你想先和 Web ChatGPT 探索。

**它会做什么：**
- 把讨论中的事实、Human 决定、建议、未验证假设分开；
- 不假装已经检查真实 repo；
- 不提前创建 Work Item / Spec / Plan；
- Human 明确要求整理时，生成 single-file Proposal 或 README-led Proposal package。

**结束状态：**  
得到 `docs/proposals/` 下的候选 Proposal，等待 Coding Agent Review。

→ [`打开 Prompt`](chatgpt-exploration-to-proposal.md)

---

## `review-proposal-inbox.md`

**什么时候用：**  
Proposal 已经进入 Repository，需要 Coding Agent 基于真实项目判断它是否合理、是否现在做。

**它会做什么：**
1. **Quality Review**：检查 repo facts、重复/覆盖、scope coherence、solution lock-in、assumptions、risks、conflicts；
2. **Admission Review**：判断 `Already planned? / Now? / Feasible enough?`；
3. 给出 `START_NOW | ABSORB | DEFER | BLOCK | REJECT` recommendation 和 evidence。

**结束状态：**  
必须停在 **Gate R**，等待 Human 确认 recommendation；不会自动归档、改 Roadmap 或开始 implementation。

→ [`打开 Prompt`](review-proposal-inbox.md)

---

## `gate-r-proposal-decision.md`

**什么时候用：**  
Coding Agent 已经审过 Proposal，但 Gate R Packet 太简略、理由不清楚，或你怀疑 recommendation 缺少证据。

**它会做什么：**
- 重新整理 Proposal Summary、Repository Evidence、Quality/Admission Findings；
- 明确 recommendation 和理由；
- 对 `START_NOW / ABSORB / DEFER / BLOCK / REJECT` 给出对应 impact、trigger 或 residual scope。

**结束状态：**  
再次停在 **Gate R**，明确问 Human 是否接受该 recommendation。

→ [`打开 Prompt`](gate-r-proposal-decision.md)

---

# 三、Mid-flight / Bug / Small Change

## `mid-flight-idea.md`

**什么时候用：**  
正在执行一个 Work Item 时，你突然想到“顺便再做一个东西”。

**它会做什么：**
保持当前 approved scope 不变，要求 Agent 在以下路径中选择：
- `PLAN_LOCAL`
- `DIRECT_CHANGE`
- `APPROVED_CAPABILITY_NEEDS_WORK_ITEM`
- `APPROVED_DESIGN_CHANGE → Gate A`
- `NEW_CAPABILITY_OR_DIRECTION → Proposal → Gate R`

**结束状态：**  
新想法被放到正确路径，不会 silent expand 当前 Work Item。

→ [`打开 Prompt`](mid-flight-idea.md)

---

## `test-or-use-feedback.md`

**什么时候用：**  
你遇到 bug、真实使用反馈、测试问题、UI/交互小改，希望直接描述 Actual / Expected，而不是先自己分类。

**它会做什么：**
- 优先判断能否走 Direct Change；
- 明确 bug 则做 regression / targeted verification；
- 如果是 active Work Item defect，则留在当前 WI 修；
- 如果需要改变 approved design → Gate A；
- 如果是新 capability → Proposal → Gate R。

**结束状态：**  
小问题直接修并验证；大问题自动升级到正确流程。

→ [`打开 Prompt`](test-or-use-feedback.md)

---

## `direct-small-change.md`

**什么时候用：**  
你已经高度确定这是 typo、copy、spacing、等价 refactor、小 config/test 修正等边界清楚的小改。

**它会做什么：**
先验证 Direct Change 条件；满足则执行：

```text
inspect → change → targeted verification → review → report
```

**结束状态：**  
正常情况下直接完成，不创建 Work Item / TODO / Spec / Plan / Gate B / Gate C；如果发现语义/风险升级则重新 routing。

→ [`打开 Prompt`](direct-small-change.md)

---

# 四、Human Gate Prompt

这些 Prompt **不是用来触发本来不会发生的 Gate**。Gate 应由 Coding Agent 按 `CLAUDE.md` 自动识别。它们主要用于 Human 想让 Review Packet 更清楚、重新组织或严格停在当前 Gate 时。

## `gate-a-decision.md` — Design Divergence Review

**什么时候用：**  
真实工程证据表明已经批准的 project design、Milestone scope/AC 或 accepted Spec 可能必须改变。

**它会做什么：**  
要求 Agent 给出 original baseline、verified evidence、conflict、suggested change、alternatives 和影响范围，并区分真正的 Design Divergence 与普通 implementation defect。

**结束状态：**  
停在 **Gate A**，Human 决定是否改变 approved baseline。

→ [`打开 Prompt`](gate-a-decision.md)

---

## `gate-b-spec-review.md` — Spec Review

**什么时候用：**  
正式 Work Item 的 Spec 已收敛，需要 Human 审设计，但 Agent 的说明太技术化或不够结构化。

**它会做什么：**  
围绕 User/Business Flow、Data/State/Control Flow、Source of Truth、Failure Semantics、Invariants、Design Forks、Non-Goals 生成简洁 Review Packet；不让 Human 审 implementation task decomposition。

**结束状态：**  
停在 **Gate B**，等待 Human accepted Spec。

→ [`打开 Prompt`](gate-b-spec-review.md)

---

## `gate-c-feature-acceptance.md` — Feature / Work Item Acceptance

**什么时候用：**  
Work Item 已完成 implementation、必要 verification/review 和 applicable E2E，需要 Human 验真实功能。

**它会做什么：**
- 列出实际完成内容；
- 只报告实际执行过的验证；
- 给出 Human 手动验收的最小场景、操作步骤和预期结果；
- 说明无法自动验证内容、已知限制和所需运行服务。

**结束状态：**  
停在 **Gate C**；Human accepted 前不得 Work Item Done。

→ [`打开 Prompt`](gate-c-feature-acceptance.md)

---

## `gate-d-milestone-acceptance.md` — Milestone Acceptance

**什么时候用：**  
当前 Milestone 的 required Work Items 看起来都完成，且 DoD/Acceptance Criteria 似乎已有证据。

**它会做什么：**
- 逐条 AC 映射真实 evidence；
- 汇总 Work Item final state；
- 说明当前系统如何兑现 Milestone User Capability；
- 列出 limitation / deferred scope；
- 说明 accepted 后的 roadmap / project-state / closeout 更新。

**结束状态：**  
停在 **Gate D**；Human accepted 后才能 Milestone closeout / next Milestone。

→ [`打开 Prompt`](gate-d-milestone-acceptance.md)

---

# 五、Gate accepted 后继续执行

## `gate-b-approved-execute.md`

**什么时候用：**  
Human 已明确 accepted Gate B，想直接告诉 Agent“按 approved Spec 继续”。

**它会做什么：**
- 生成/更新 Plan；
- implementation → tests → review/fix → applicable E2E → verification；
- routine Plan/Task decision 自主推进；
- 若真实证据要求改变 approved design，立即 Gate A。

**结束状态：**  
完成执行后停在 **Gate C**。

→ [`打开 Prompt`](gate-b-approved-execute.md)

---

## `gate-c-accepted-closeout.md`

**什么时候用：**  
Human 已完成 Gate C 验收并明确 accepted。

**它会做什么：**
- Work Item → Done；
- 更新 TODO；
- 形成新的 `project-state.md` checkpoint；
- 同步真正长期有效的 architecture truth；
- 检查 Current Milestone DoD/AC。

**结束状态：**  
Work Item closeout 完成；如果 Milestone 已满足，则停在 **Gate D**，不会自动 accepted。

→ [`打开 Prompt`](gate-c-accepted-closeout.md)

---

# 六、新 Session / Resume

## `resume-current-work-item.md`

**什么时候用：**  
换了新 Coding Agent session，想继续当前工作，但不希望重新解释项目背景。

**它会做什么：**
1. 先读 `project-state.md`，理解最近一次 Human-readable checkpoint；
2. 再读 TODO / Current Milestone / relevant architecture / current Spec/Plan；
3. 用真实 Git/PR/code/tests 验证 `Last Updated` 之后的变化；
4. 报告当前实际坐标、下一步和是否存在 Human Gate。

**结束状态：**  
Agent 恢复真实当前状态并继续正确路径；不会把 project-state 当实时 truth，也不会因为 resume 人为创建 Work Item。

→ [`打开 Prompt`](resume-current-work-item.md)

---

## 一句话记忆

```text
新项目 → chatgpt-project-bootstrap → first-handoff
新功能 → chatgpt-exploration-to-proposal → review-proposal-inbox → Gate R
做到一半有新想法 → mid-flight-idea
bug / 小 UI / 使用反馈 → test-or-use-feedback
Human Gate 输出不好审 → 对应 gate-*.md
Gate B/C 已 accepted → 对应 approved/accepted continuation prompt
新 session → resume-current-work-item
```
