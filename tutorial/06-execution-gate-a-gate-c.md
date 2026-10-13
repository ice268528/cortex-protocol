# 06 — Execution、Gate A、Gate C

Gate B accepted 后：

```text
Plan
→ Code
→ Tests
→ Review
→ Fix
→ Verification
→ Gate C
```

## Gate A 在哪里？

它不是 B 前面的固定步骤。

例如 implementation 时发现：

> 已批准 Spec 认为 Feedback 可以同步确认持久化成功，但真实 provider/transaction boundary 无法保证该语义，必须改变用户可见行为。

Agent 应停下来：

```text
Original Approved Baseline
Evidence
Conflict
Suggested Change
Alternatives
Impact
```

→ Gate A。

Human accepted 后先做 owner reconciliation，再继续。例如这个变化影响了 accepted Spec，就先改 Spec；如果同时改变 long-lived architecture boundary，再更新对应 architecture。只有 every-session standing boundary 也变化时才更新 CLAUDE。


## 什么不是 Gate A

```text
文件拆分改变
helper 重构
implementation bug
test path 改变
pure visual polish
```

## Gate C

Work Item 完成后 Agent 给 Human：

```text
实际实现
实际 verification
手动操作步骤
expected result
known limitation
```

Human 从真实入口测试。

accepted 后才 Work Item Done，并自动执行 closeout：

```text
TODO → Done
project-state → Work Item checkpoint
architecture → only verified long-lived facts
CLAUDE → only if stable standing facts changed
```

