# 03 — 把设计变成可恢复的 Repository State

现在把已确认的信息落进 Repository。

## 最小结构

```text
CLAUDE.md
TODO.md

docs/
├── project/
│   ├── 00-product.md
│   ├── 01-domain-and-state.md
│   └── 02-data-flow.md
└── stages/
    └── stage-01-feedback-intake.md
```

示例最终状态在 [`final-state/`](final-state/)。

## TODO 的职责

示例：[`final-state/TODO.md`](final-state/TODO.md)。

它只回答：

```text
Current 是谁？
Next 是谁？
Blocked 是谁？
Done 是谁？
```

它不回答“这次具体改哪个文件”。

## 安装 Agent standing policy

把 [`../starter-template/`](../starter-template/) 合并进真实 repo，并替换所有占位符。

至少确保 Claude Code 知道：

- cold start 怎么做；
- Current Work Item 从哪里找；
- 什么情况进入 A/B/C/D；
- 哪些 instructions 按需加载；
- Gate 通过后由谁 reconcile；
- 项目真实启动/测试/验证命令。

## 成功标准

假设现在换一个完全新的 Claude Code session，它只看 Repository，应该能回答：

1. 现在做哪个 Work Item？
2. 它属于哪个 Stage？
3. 为什么做？
4. 相关长期设计是什么？
5. coding 前应该验证什么？
6. 什么情况下必须停下来找 Human？

如果答不出来，优先修 Repository state，而不是准备一个更长的 handoff Prompt。

下一步：[`04-first-handoff.md`](04-first-handoff.md)。
