# Prompt：New Project 第一次交给 Coding Agent

```text
这是一个全新项目。

Product / Roadmap / Project State 已放入 docs/project/；
Architecture 只包含 Human 明确选择的 baseline 或 UNDECIDED 项。

请按 CLAUDE.md 冷启动并做 Bootstrap Review：

1. 读取 project-state 了解最近一次可信 checkpoint 和 `Last Updated`，再用 TODO/Git/PR/code 验证之后的真实变化；检查 Product / Roadmap / Current Milestone 与当前实际状态是否一致；
2. challenge 错误假设和过早技术决定；
3. 对照真实 repo / config / dependencies；
4. 不改变产品意图的 factual/structural correction 可以直接完成；
5. 如果建议会改变 approved product intent / Milestone commitment，先停下来让我决定。

然后选择最小正确 delivery path：

- starter/config/docs 的小修，符合 Direct Change 就直接修 + verify；
- 第一个真正需要独立设计/验收的 vertical slice，创建 Work Item：
  Repo Investigation → Spec → 停在 Gate B。

不要穷举整个 Milestone backlog。
不要创建整个项目的巨大 Spec。
不要把 architecture templates 全部填满。

任意阶段真实证据要求改变 approved project design / Milestone / approved change design → Gate A。
```
