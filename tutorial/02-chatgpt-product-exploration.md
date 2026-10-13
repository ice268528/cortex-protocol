# 02 — 和 Web ChatGPT 讨论项目需求

复制：

[`../prompts/chatgpt-project-bootstrap.md`](../prompts/chatgpt-project-bootstrap.md)

然后正常聊。

例如：

```text
Human:
我想做一个内部 Feedback Inbox。

ChatGPT:
谁可以提交？
谁负责处理？
M1 需要匿名吗？
最小闭环是什么？
什么明确不做？
```

你可以聊很多轮。

## 这一步要收敛什么

```text
Target User / Problem
Core Experience
Product Principles
M1 User Capability
M1 Definition of Done / Acceptance Criteria
Constraints
Non-Goals
Explicitly Not Now
```

不要因为 Prompt 里有模板，就让 ChatGPT 每轮都输出 Markdown。

## 什么时候进入下一步

当你觉得：

> “现在另一个人只看这些结论，也能理解我们到底要造什么。”

然后明确说：

> **“现在按 File Output Contract 整理成项目需求文档。”**
