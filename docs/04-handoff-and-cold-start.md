# 04. Handoff and Cold Start

## 第一次交给 Coding Agent

新项目先具备：

```text
CLAUDE.md
product.md
roadmap.md
project-state.md
architecture/README.md
```

其中 `project-state.md` 是给 Human 优先阅读的最近一次可信 checkpoint snapshot，同时供 Agent 恢复坐标；它不是实时 control plane。Agent 仍需用 TODO/Git/PR/code 验证 `Last Updated` 之后的变化。

TODO 可以暂时没有 active Work Item。

使用：

[`../prompts/first-handoff-to-claude-code.md`](../prompts/first-handoff-to-claude-code.md)

Coding Agent 先做：

```text
Cold Start
→ Bootstrap Review
→ reality check
```

而不是直接 coding。

## Bootstrap Review

检查：

- Product / Roadmap / M1 是否一致；
- 是否有明显错误假设；
- Architecture baseline 是否过早；
- 真实 repo / dependency 与文档是否冲突；
- 第一个需要正式设计的 Work Item 是什么。

不改变 Human 产品意图的 factual correction 可直接修正。

如果要改变已批准 Product / Milestone commitment，则先交还 Human 判断。

## 新 Session

有 active Work Item：

```text
“继续当前 Work Item。”
```

Agent 根据 Repository 恢复。

没有 active Work Item，而 Human 只给一个小 bug：

> 直接按 bug 判断 Direct Change，不要为了“恢复流程”先创造 Work Item。
