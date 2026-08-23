# 05 — Gate B：你审的是系统行为，不是 Implementation Plan

假设 Claude Code + Superpowers 已经完成 FB-01 的 brainstorming，并形成 spec。

## 示例 Design Review Packet

看：[`final-state/review-packets/fb-01-gate-b.md`](final-state/review-packets/fb-01-gate-b.md)。

它应该让你看懂：

```text
Employee submits title + description
        ↓
Backend validates authenticated user
        ↓
Feedback created
        ↓
status = new
category = null
        ↓
Return created Feedback
```

同时说明失败行为：未登录、字段非法、持久化失败时用户会看到什么。

## YOUR JOB RIGHT NOW

只回答：

> **“这个系统设计是不是我要的？”**

你可以指出：

- 状态不对；
- 权限不对；
- 数据流不对；
- 用户可观察行为不对；
- persistence / external service 边界不对。

如果正确：

```text
Approved.
```

## DON'T DO THIS

```text
✗ “你准备改几个文件？”
✗ “先给我看 implementation plan。”
✗ “这个 service class 应该怎么拆？”
✗ “每个 test 具体写什么？”
```

这些属于后续 plan / execution 层。

Gate B 的价值，就是 Human 批准**行为**之后退出工程执行细节。

下一步：[`06-execution.md`](06-execution.md)。
