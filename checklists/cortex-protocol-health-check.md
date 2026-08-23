# Checklist：Cortex Protocol 项目健康检查

适合每个 Stage 结束后，或感觉项目开始“越来越靠 Prompt 维持”时检查一次。

## Repository state

- [ ] `docs/project/` 描述 current truth，而不是聊天历史
- [ ] `docs/stages/` 能解释当前阶段承诺
- [ ] `TODO.md` 能明确指出 Current Work Item
- [ ] `TODO.md` 没有混入 implementation tasks
- [ ] 新 session 不需要粘贴长篇项目背景才能恢复

## Agent autonomy

- [ ] Agent 会主动做 cold start 和 reality check
- [ ] Agent 会主动 reconcile 受影响文档
- [ ] Human 不需要提醒 TODO / review / PR / archive 等 housekeeping
- [ ] Agent 只加载当前任务需要的上下文
- [ ] `docs/coding-guides/` 没有被默认全量加载

## Human control

- [ ] 重大设计变化一定经过 Gate A
- [ ] Spec 在 Gate B 由 Human 审系统行为
- [ ] Plan 默认不会制造额外人工 Gate
- [ ] Work Item 只有 Gate C accepted 后才 Done
- [ ] Stage 只有 Gate D accepted 后才收尾

## Workflow boundaries

- [ ] `CLAUDE.md` 没有重复实现 Superpowers 已有流程
- [ ] Project-level / change-level / implementation-level 没有混层
- [ ] PR review 不因“创建 PR”机械重复
- [ ] 有长期价值的 E2E 已沉淀为 regression asset

如果很多项失败，优先修 Repository rules 和 state，不要先加更长 Prompt。
