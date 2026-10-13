# Prompt：Gate B accepted → Execute

```text
Gate B accepted。

先执行 Gate B Post-decision sync：
- current Spec 标记 accepted / approved baseline；
- TODO 更新为真实 planning/execution status；
- 通常不更新 project-state；
- 不把 future implementation 提前写成 Verified Current architecture / CLAUDE standing truth。

然后以 approved Spec 为 baseline：
→ 生成/更新 Plan
→ implementation
→ tests
→ review/fix
→ applicable E2E
→ verification

Routine Plan/Task decisions 默认自主推进，不需要我逐项批准。

如果过程中真实证据要求改变 approved project design / Current Milestone / approved Spec，立即 Gate A。

完成后停在 Gate C 给我 Feature Acceptance Packet。
```
