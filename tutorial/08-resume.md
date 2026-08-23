# 08 — 新 Session：验证 Cortex 是否真的起作用

假设 FB-01 已经 Accepted，TODO 现在是：

```text
Done: FB-01 Submit Feedback
Current: FB-02 Support Inbox
```

关闭当前 Claude Code session，开启一个新的。

## 发送

推荐：

```text
继续当前 Work Item，按 `CLAUDE.md` 冷启动并恢复当前状态。
```

当 Repository state 已经非常稳定时：

```text
继续当前 Work Item。
```

## 成功标准

新 session 不需要你重新讲 Feedback Inbox 的故事，就应该能：

1. 找到 FB-02；
2. 找到 Stage 1；
3. 找到相关 project docs；
4. 查看真实代码/测试/git；
5. 知道什么时候自主推进；
6. 知道什么时候回到 Gate。

如果做不到，不要先把 Prompt 加长。

先问：

> **Repository state 哪里不够可靠？**

## Tutorial Graduation Check

如果你现在能回答下面八个问题，就已经掌握 Cortex Protocol 的核心：

- 为什么项目记忆要进 Repository？
- Project design / Spec / Plan 有什么区别？
- 为什么 Spec 要审而 Plan 默认不用？
- 什么情况下进 Gate A？
- Gate C 和测试绿有什么不同？
- TODO 为什么不放 implementation tasks？
- Cortex 为什么不重复 Superpowers？
- 为什么新 session 最终只需要“继续当前 Work Item”？

下一步：把它用到自己的项目，见 [`../START-HERE.md`](../START-HERE.md)。
