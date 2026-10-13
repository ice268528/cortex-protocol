# 09 — 做功能途中突然有新想法

正在实现 Support Inbox 时，你说：

> “顺便加一个 Export CSV。”

不要自己先判断它属于什么。

直接发送：

[`../prompts/mid-flight-idea.md`](../prompts/mid-flight-idea.md)

Agent 判断：

```text
PLAN_LOCAL?
DIRECT_CHANGE?
APPROVED_CAPABILITY_NEEDS_WORK_ITEM?
APPROVED_DESIGN_CHANGE → Gate A?
NEW_CAPABILITY → Proposal → Gate R?
```

核心规则：

> **一句“顺便”不能 silent expand 当前 Work Item。**

如果 Export CSV 是新 capability：

```text
Proposal
→ Review
→ Gate R
```

当前 Work Item 默认继续，不被无关想法阻塞。
