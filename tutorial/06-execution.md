# 06 — Execution：这是 Human 应该安静下来的阶段

Gate B Approved 后，Superpowers 继续：

```text
writing-plans
→ isolated worktree / branch
→ implementation
→ TDD / tests
→ task-level review
→ whole-change review
→ fixes / verification
→ PR / CI / applicable E2E
```

具体能力以你安装的 Superpowers 版本为准；Cortex Protocol 不重新定义它的内部工程循环。

## YOUR JOB RIGHT NOW

```text
默认：不做任何流程调度。
```

只有两种典型情况 Human 会重新回来：

1. execution 暴露重大上游设计错误 → **Gate A**；
2. 工程验证完成，功能准备人工验收 → **Gate C**。

## DON'T DO THIS

```text
✗ 提醒 Agent “记得 TDD”
✗ 每个 implementation task 都人工 review
✗ 手动安排 subagent
✗ 提醒它修完再 re-review
✗ 反复问“TODO 更新了吗”
```

如果这些已经是 Superpowers 或 Repository standing policy 的职责，就不要再由 Human babysit。

下一步：[`07-gate-c.md`](07-gate-c.md)。
