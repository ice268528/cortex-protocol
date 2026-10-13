# 07. PR、E2E、Work Item Closeout、Milestone Closeout

## Work Item

正式 Work Item 正常：

```text
branch/worktree
→ implementation
→ tests
→ review
→ PR/CI as applicable
→ E2E as applicable
→ Gate C
```

### Gate C accepted

Agent：

1. Work Item → Done；
2. 更新 TODO，并形成一次 project-state checkpoint（最新 accepted Work Item / PR / Next / Recent Checkpoints）；
3. 将真正长期有效、已实际成立的新事实同步到 architecture；
4. 如果 stable run command / minimal code map / critical standing boundary 改变，同步 `CLAUDE.md`；
5. 更新必要 Proposal traceability；
6. 检查当前 Milestone AC / DoD。

不要把整个 Spec/Plan 复制进 Architecture。

## Direct Change

Direct Change 通常只需汇报：

```text
changed
actual verification
result
remaining risk
```

如果没有 durable state 变化，不做额外 Truth Sync 仪式。

## Milestone

当所有 Work Items / AC 满足：

```text
→ Gate D
```

Gate D accepted 后：

- roadmap status；
- project-state checkpoint（Latest Accepted Milestone / Current Milestone / Next / Recent Checkpoints）；
- archive 真正过时的 Milestone-scoped artifact；
- 如 every-session standing context 改变，同步 `CLAUDE.md`；
- next Milestone。

仍代表 Current Truth 的 project docs 不机械归档。
