# 04 — 第一次交给 Coding Agent

现在 project docs 已在 repo。

发送：

[`../prompts/first-handoff-to-claude-code.md`](../prompts/first-handoff-to-claude-code.md)

Coding Agent 第一件事不是写代码：

```text
Cold Start
→ Bootstrap Review
→ reality check
```

## 它应该检查

```text
Product / M1 是否一致？
有没有错误 repo assumption？
Architecture baseline 是否过早？
真实 dependency/version 是什么？
M1 最小第一个 coherent Work Item 是什么？
```

## Human 现在的工作

如果 Agent 只是发现：

```text
README typo
starter path 错
config 小修
```

让它 Direct Change。

如果 Agent 说 Product / M1 本身的承诺需要改变，Human 再回来判断。

## 第一个 Work Item

Feedback Inbox 可能先选择：

```text
FB-01 Submit Feedback
```

而不是一口气设计整个 M1。
