# Proposals

`docs/proposals/` 是已有项目的新 capability / direction Inbox。

> Proposal ≠ Requirement ≠ Approved Design ≠ Current Truth.

Proposal item：

```text
<name>.md
```

或：

```text
<name>/
├── README.md
└── supporting files...
```

Package README 是唯一入口和 package-level Review / Gate R disposition 载体。


## Templates / Navigation

- [Single-file Proposal template](_TEMPLATE.md) — 适合一个文件就能说清的问题空间。
- [Proposal Package template](_PACKAGE_TEMPLATE/README.md) — 复杂 Proposal 的唯一 package 入口；supporting files 从这里索引。
- [Archive rules](_archive/README.md) — accepted / absorbed / deferred / blocked / rejected 的 disposition 目录约定。

## Lifecycle

```text
Proposal
→ Coding Agent Quality Review
→ Admission Review
→ Recommendation
→ Gate R
→ Human confirms / overrides
→ disposition
```

**未经 Gate R Human 确认，不最终 archive。**

## Archive

```text
_archive/
├── accepted/
├── absorbed/
├── deferred/
├── blocked/
└── rejected/
```

DEFER 必须有 Revisit Trigger。
BLOCK 必须有 Recheck Trigger。
