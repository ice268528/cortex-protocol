# 08. `docs/coding-guides/`：人工触发的事实旁路

`docs/coding-guides/` 不属于每个 Work Item 的默认上下文。

它的用途是：当你发现 Coding Agent 在某个具体技术点上凭记忆猜、出现幻觉，或者仓库里已经有经过验证的技术事实时，**明确指定它去读某一份 guide**。

```text
正常开发
→ 发现某技术点需要已验证事实
→ 人明确指定 docs/coding-guides/xxx.md
→ Agent 读取该 guide
→ 基于事实重新判断
→ 回到当前 spec/plan/implementation
```

不要：

- 每个任务扫描整个 `docs/coding-guides/`；
- 每轮会话都读取；
- 自动把整个目录放进 context。

这样可以减少无关上下文，同时保留“关键技术事实可人工注入”的能力。
