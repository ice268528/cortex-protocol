# 15. `docs/project/architecture/` 到底放什么？

结论：

> **数据流、项目目录结构、模块边界、API contract、数据库设计都可以属于 architecture，但只写它们的长期架构层。**

推荐可选结构：

```text
docs/project/architecture/
├── README.md
├── system-overview.md
├── project-structure.md
├── domain-and-state.md
├── data-flow.md
├── interfaces-and-contracts.md
├── persistence-and-data.md
└── runtime-and-deployment.md
```

全部可选。

---

## `system-overview.md`

回答：

> 系统由哪些长期组件组成？它们的职责和大边界是什么？

写：

- frontend/backend/worker/provider 等 major components；
- component ownership；
- high-level dependency direction。

不写每个文件或 endpoint。

---

## `project-structure.md`

回答：

> Repository 长期如何分区？模块职责和依赖方向是什么？

写：

```text
frontend/
backend/
packages/
domains/
shared/
```

以及 allowed/forbidden dependencies。

不写“新增按钮去哪个文件”这种高漂移导航。

---

## `domain-and-state.md`

回答：

> 核心业务概念、状态、生命周期和 invariant 是什么？

写：

- core entities / value concepts；
- state machine；
- ownership；
- invariants。

未批准的 future Work Item design 留在 Spec。

---

## `data-flow.md`

回答：

> 关键业务流怎样跨模块/边界移动？

重点：

```text
source of truth
sync / async boundary
side effects
retry / idempotency
failure propagation
```

不需要给每个 CRUD endpoint 画图。

---

## `interfaces-and-contracts.md`

回答：

> 哪些跨边界 API / event / schema contract 是长期重要的？

写：

- ownership；
- versioning；
- auth boundary；
- compatibility；
- error/idempotency semantics；
- frozen/high-risk fields。

不要复制完整 OpenAPI。

Exact endpoint/schema 以 source/generated spec 为真。

---

## `persistence-and-data.md`

回答：

> 数据由谁拥有？一致性、迁移、保留、恢复规则是什么？

写：

- data ownership；
- conceptual relation；
- source of truth；
- consistency/transaction；
- migration/backfill；
- retention/deletion；
- cache/derived-data semantics。

不要复制完整 DDL、每个 column/index。

---

## `runtime-and-deployment.md`

只有 runtime/deployment 复杂到需要跨 session 恢复时创建。

---

## Status

推荐：

```text
Verified Current
Approved Baseline
UNDECIDED
```

### Verified Current

真实实现已经如此。

### Approved Baseline

Human 明确批准的长期 foundation。

### UNDECIDED

现在没有必要决定，附：

```text
Decision Trigger
```

Work Item future implementation 在 Gate C accepted 前不应该写成 Verified Current。

---

## 什么时候创建文件？

问：

1. 这个信息会跨多个 Work Item 使用吗？
2. 新 Agent 不知道会不会经常做错？
3. 它是长期 boundary/invariant，而不是 feature-local detail 吗？
4. code/schema/config 自己是否不足以解释“为什么/边界”？

多数 Yes 才建。

Architecture 文档数量应该跟长期误解风险增长，而不是跟 feature 数量增长。
