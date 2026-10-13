# Specs

只保存正式 Work Item 的主要 change-level Spec。

Direct Change 不需要为了流程制造 Spec。

## Lifecycle

```text
Investigation
→ Spec draft / converge
→ Gate B
→ Human accepted
→ Spec becomes approved Work Item baseline
```

Gate B accepted 后应明确记录 Spec 的 accepted/approved state，再进入 Plan。

如果后续真实工程证据要求实质改变 accepted Spec：

```text
→ Gate A
→ Human accepted change
→ revise Spec
→ continue from the correct path
```

不要把 future implementation 提前写成 `Verified Current` architecture。
