# Prompt：Gate C accepted → Closeout

```text
Gate C accepted。

请执行 Work Item closeout：

- 将 Work Item 标记 Done；
- 更新 TODO，并形成一次 project-state checkpoint：Latest Accepted Work Item / 对应 PR / Current Snapshot / Next / Recent Checkpoints；
- 只把真正长期有效、已经成立的新事实同步到 architecture；
- 如果真实实现改变了 stable run command / minimal code map / critical standing boundary，同步 CLAUDE.md；
- 更新必要 Proposal traceability；
- Git closeout 按项目规则执行；
- 检查 Current Milestone 的 DoD / Acceptance Criteria。

如果 Milestone 已全部满足，停在 Gate D，不要自动 accepted。
```
