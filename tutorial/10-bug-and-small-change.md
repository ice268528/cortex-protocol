# 10 — Bug / 前端小改：什么时候直接做

你说：

> “Submit 成功 toast 太靠上，往下移 12px。”

这是典型 Direct Change：

```text
inspect
→ CSS change
→ focused check
→ report
```

不需要：

```text
WI
Spec
Plan
Gate B
Gate C
```

## Bug

你说：

> “重复点击 Submit 会创建两条，但 approved behavior 明确应该只有一条。”

正确行为已经清楚：

```text
root cause
→ fix
→ regression
→ affected tests
→ report
```

也可以 Direct Change。

## 什么时候升级

你说：

> “删除时不要 confirmation，直接删，然后支持 undo。”

这改变 interaction semantics。

如果 confirmation 是 approved behavior：

```text
→ Gate A
```

如果这是新的独立 capability：

```text
→ Proposal → Review → Gate R
```

如果 change 本身很复杂、需要独立 design/acceptance：

```text
→ Work Item
```
