# Cortex Protocol v2 — Health Check

## Taxonomy
- [ ] 正式层级只有 Milestone → Work Item → Task
- [ ] 没有残留 Stage 管理层
- [ ] Task 不进 TODO

## Proposal / Gate R
- [ ] 新 capability/direction 使用 Proposal
- [ ] Coding Agent Review 有明确 evidence
- [ ] Recommendation 不会自动成为 disposition
- [ ] START_NOW / ABSORB / DEFER / BLOCK / REJECT 都会进入 Gate R
- [ ] Gate R 前不自动 archive / start implementation

## Gate A–D
- [ ] Gate A 是 interrupt
- [ ] Gate A 只处理 approved design divergence
- [ ] Gate B 审 Spec behavior，不审 Plan Task
- [ ] Gate C 是真实 Work Item acceptance
- [ ] Gate D 回到 Milestone DoD / AC

## Right-sized process
- [ ] 小 bug/UI polish/refactor 可以 Direct Change
- [ ] Direct Change 不机械创建 Spec/Plan/B/C
- [ ] 大/语义 change 不会伪装成 Direct Change

## Architecture
- [ ] Architecture topic 按需创建
- [ ] 不复制 full OpenAPI / DB DDL
- [ ] future Work Item design Gate C 前不标 Verified Current

## Repository memory
- [ ] product / roadmap / project-state 职责清楚
- [ ] `project-state.md` 是 Human-readable checkpoint snapshot，不是假装实时的 event log
- [ ] `TODO.md` 只跟踪正式 Work Item，并承担更细的 live Work Item/Gate state
- [ ] CLAUDE.md 没重复整个 Superpowers workflow
- [ ] 新 session 可通过 Repository 恢复
