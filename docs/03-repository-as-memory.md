# 03. Repository as Memory：让仓库而不是聊天记录保存状态

## 1. 四类核心状态源

### `CLAUDE.md`

告诉 Claude Code **怎么工作**：冷启动、Human Gates、按需加载、常驻约束、项目命令和项目级 standing policies。

### `docs/project/`

告诉 Agent **系统长期应该是什么样**。这是 current truth，不是历史日志。

### `docs/stages/`

告诉 Agent **当前阶段为什么做、要交付什么**：Goal、Scope/Non-goals、Work Items、Acceptance Criteria。

### `TODO.md`

告诉 Agent **现在做到哪里**。只跟踪项目级 Work Item，不复制 Superpowers plan 里的 implementation tasks。

## 2. 为什么新会话可以很短

理想情况下，Claude Code 冷启动后通过以下链路恢复：

```text
CLAUDE.md
→ TODO.md
→ 当前 Stage
→ 相关 project docs
→ 当前 spec/plan（如有）
→ branch/worktree + 真实代码
```

所以 Prompt 不需要承载完整历史。

## 3. 最小上下文原则

每个 Work Item 开始时，只加载：

- 当前 Work Item；
- 所属 Stage；
- 相关 `docs/project/`；
- 当前实际代码；
- 相关 tests/config/versions；
- 当前 change 已存在的 spec/plan。

不要默认扫描全部 `docs/`，尤其不要默认把 `docs/coding-guides/` 全部塞进 context。

## 4. 文档同步不再靠人提醒

Gate 通过后，Coding Agent 应主动 reconcile 真正受影响的文档：

- Gate A：设计修正后同步 project/stage/TODO/spec/plan 中受影响的部分；
- Gate C：Work Item accepted 后更新 TODO，并沉淀长期有效的新事实；
- Gate D：Stage accepted 后 final reconciliation、归档过时 Stage-scoped 文档、更新 README/index。

人不需要说“记得把 TODO 打勾”或“记得更新 domain 文档”。
