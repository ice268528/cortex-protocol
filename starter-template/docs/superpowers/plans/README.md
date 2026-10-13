# Plans

只保存正式 Work Item 的 implementation Plan / Task decomposition。

Task 不进入 TODO。

## Lifecycle

Plan 默认在 Gate B accepted 后，以 approved Spec 为 baseline 创建/更新：

```text
Gate B accepted
→ Plan
→ Implementation / Tests / Review / Verification
```

不改变 approved semantics 的 plan-local 调整可以由 Coding Agent 自主完成；只有影响后续执行/跨 session 恢复时才需要更新 Plan。

如果正确实现必须改变 approved Spec / Milestone / project baseline，不要只改 Plan：

```text
→ Gate A
```
