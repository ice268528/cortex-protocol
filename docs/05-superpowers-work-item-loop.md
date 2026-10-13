# 05. Direct Change 与正式 Work Item

## Direct Change

适合：

- 已知正确行为的 bug；
- copy / spacing / color / alignment；
- non-semantic UI polish；
- 等价 refactor；
- 小型 test/build/config fix。

流程：

```text
inspect
→ change
→ targeted verification
→ review
→ report
```

不强制 Spec / Plan / Gate B / Gate C。

可以使用 Superpowers 的 debugging/testing/review 能力，但不要为了工具流程制造 durable artifacts。

## Work Item

需要独立设计/验收时：

```text
Repo Investigation
→ Spec
→ Gate B
→ Plan
→ Implementation
→ Tests / Review / Verification
→ Gate C
```

一个 Work Item 一个主要 Spec + Plan。

## 什么时候升级

Direct Change 中发现：

```text
approved semantics 要变
public/cross-module contract 要变
state/persistence/security semantics 要变
多个重要 design fork
需要跨 session coordination
需要独立 Human acceptance
blast radius 显著变大
```

则停止轻量路径。

- approved design change → Gate A
- new capability → Proposal → Review → Gate R
- capability 已批准但需要正式设计 → Work Item

## Plan-local

当前 Work Item 内的 implementation adjustment：

- 不改 Spec semantics；
- 不改 AC；
- 不改 public contract。

可直接处理。

只有它影响后续执行/恢复时才值得写回 Plan。
