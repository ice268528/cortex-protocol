# 11 — 新 Session 怎么恢复

有 active Work Item：

```text
继续当前 Work Item。
```

Coding Agent：

```text
CLAUDE
→ project-state（最近一次 Human-readable checkpoint）
→ TODO（live Work Item/Gate state）
→ current Milestone in roadmap
→ relevant architecture
→ current Spec/Plan
→ code/tests/Git（验证 Last Updated 之后的真实变化）
```

恢复。`project-state.md` 是 snapshot，不应覆盖 Git/PR/TODO 中更新的真实状态。

如果没有 active Work Item，而你只给一个小 bug：

> 直接描述 bug。

Agent 应判断 Direct Change，而不是因为“新 session”先创建 Work Item。

## Graduation Check

你应该能回答：

1. 新项目怎么从 starter → ChatGPT → project docs？
2. Proposal Review 为什么最后必须 Gate R？
3. Gate A 与 Gate R 的职责差异？
4. Gate B/C 为什么分别审设计和真实功能？
5. Gate D 为什么看 Milestone AC？
6. Direct Change 为什么不强制 Spec + Plan？
7. `architecture/` 为什么不复制 full API/DB schema？
