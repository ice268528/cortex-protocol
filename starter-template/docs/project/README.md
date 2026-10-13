# Project Documentation

> **Description:** authoritative project documents 的快速入口，不复制正文。
> **Last Updated:** YYYY-MM-DD

## Core files

| File | Responsibility |
|---|---|
| `product.md` | authoritative product intent |
| `roadmap.md` | Milestone / capability / Definition of Done / AC |
| `project-state.md` | Human-readable latest trusted checkpoint：完成到哪里、当前 Work Item/PR、Next、durable blocker；同时供 Agent 恢复坐标 |
| [`architecture/`](architecture/README.md) | long-lived architecture truth / approved baseline |

`project-state.md` 是 checkpoint snapshot，不是实时 control plane；更细的 Work Item/Gate 状态看 `TODO.md`，最新工程事实看 Git/PR/code。

Milestone 默认直接定义在 `roadmap.md`，不建立单独 Stage 层。

Architecture 先读 [`architecture/README.md`](architecture/README.md)，只按需创建 topic。
