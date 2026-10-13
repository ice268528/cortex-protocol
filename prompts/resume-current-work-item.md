# Prompt：Resume

```text
继续当前 Work Item。

请先按 CLAUDE.md 冷启动：
1. 先读 project-state，理解最近一次 Human-readable checkpoint 和 Last Updated；
2. 再读 TODO / Current Milestone / relevant architecture / current Spec/Plan；
3. 用真实 Git/PR/code/tests 验证 Last Updated 之后发生了什么，不把 project-state 当实时 truth。

告诉我当前实际坐标、下一步，以及是否存在需要 Human Gate 的事项。

如果当前没有正式 Work Item，而我给的是一个小 bug/change，请按 right-sized routing 判断是否 Direct Change，不要为了 resume 人为创建 Work Item。
```
