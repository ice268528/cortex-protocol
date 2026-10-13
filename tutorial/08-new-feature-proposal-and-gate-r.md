# 08 — 已有项目新功能：Proposal → Gate R

项目已经在做 M1。

你突然想到：

> “让 AI 自动给 Feedback 分类。”

先和 Web ChatGPT 探索：

[`../prompts/chatgpt-exploration-to-proposal.md`](../prompts/chatgpt-exploration-to-proposal.md)

形成：

```text
docs/proposals/ai-auto-categorization.md
```

然后 Coding Agent Review：

[`../prompts/review-proposal-inbox.md`](../prompts/review-proposal-inbox.md)

## 例 1：Agent 建议现在做

Agent：

```text
Recommendation: START_NOW

Reason:
M1 的 triage DoD 当前明确要求人工分类；
AI classification 是额外 capability，
不会阻塞 M1，但可以作为 M2...
```

如果它真的建议 START_NOW，Gate R 问：

> **现在开始做吗？**

## 例 2：Agent 建议以后做

```text
Recommendation: DEFER

Reason:
M1 不依赖它；
现在加入会扩大 scope；
真实分类数据还不足。

Revisit Trigger:
累计 500 条已人工分类反馈，且 M1 accepted。
```

重点：

> Coding Agent 不能因为建议 DEFER 就自动把 Proposal 扔进 archive。

它必须 Gate R 问：

> **你同意这个延后判断和 Revisit Trigger 吗？**

Human 可以：

```text
同意
不同意，要求现在做
要求更多 evidence
修改 Proposal
```

这就是 Gate R 的意义。
