# 01. Mental Model：Human Gates + Right-sized Delivery

## 一句话

> **Human 提供意图和最终判断；Coding Agent 用真实 Repository 证据收敛；Repository 保存 durable truth。**

## 三层设计

```text
Project / Product level
→ product.md / roadmap.md / project-state.md / architecture

Change level
→ Work Item Spec

Implementation level
→ Plan / Task / code / tests
```

不要把三层揉成一个巨大 TODO 或 CLAUDE.md。

## 正式 taxonomy

```text
Milestone → Work Item → Task
```

没有 Stage。

Milestone 默认在 `roadmap.md` 中描述 User Capability + DoD / AC。

## Proposal line

```text
Human + Web ChatGPT
→ Proposal
→ Coding Agent Review
→ Gate R
→ Human confirms the recommendation
```

Gate R 是 Proposal 的最终 Human decision point，不只是“批准现在做”。

## Work Item line

```text
Work Item
→ Investigation
→ Spec
→ Gate B
→ Plan / Implementation / Verification
→ Gate C
→ Done
```

## Gate A

Gate A 不在 happy path 中：

```text
Investigation / Spec / Plan / Coding / Testing / Review / Gate C feedback
                    │
                    └── if approved design must change → Gate A
```

它问：

> **我们真的要改变之前已经批准的重要设计吗？**

## Milestone line

```text
Milestone Work Items done
+
Acceptance Criteria satisfied
→ Gate D
```

## Direct Change

小、明确、低风险、不需要独立设计/验收：

```text
inspect → change → targeted verification → report
```

Direct Change 不是 Work Item，也不要求 Spec + Plan。

## Human 日常只需识别四种输入

```text
New Project
Existing Project + New Feature
Mid-flight Idea
Bug / Real-use Feedback / Small UI Change
```

Human 不需要先替 Agent 判断 Gate / Proposal / Direct Change。
