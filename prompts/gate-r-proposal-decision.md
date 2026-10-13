# Prompt：Gate R — Proposal Decision Packet

当 Coding Agent 已经 Review Proposal，但结论/理由不够清楚时发送：

```text
先不要归档 Proposal，也不要开始 implementation。

请按 Cortex Protocol Gate R 给我一个 Proposal Decision Packet：

- Proposal Summary
- 实际读取/验证过的 Repository Evidence
- Quality Review Findings
- Admission Review Findings
- Recommendation：START_NOW | ABSORB | DEFER | BLOCK | REJECT
- Recommendation 的理由
- 如果接受该 recommendation，会发生什么，以及哪些 owner 会在什么时点同步（尤其 START_NOW 后 Roadmap 与 Work Item activated 时的 TODO / project-state）
- 如果是 START_NOW：对当前 Milestone、Work Item、approved design 的影响
- 如果是 ABSORB：具体被什么覆盖，是否有 residual scope
- 如果是 DEFER：Revisit Trigger
- 如果是 BLOCK：Blocker / Evidence Needed / Recheck Trigger
- 如果是 REJECT：为什么不建议做

最后明确问我是否接受这个 recommendation。

我确认前不要把 recommendation 当最终 disposition。
```
