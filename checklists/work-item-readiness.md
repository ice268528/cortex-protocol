# Work Item Readiness

在创建 Work Item 前先问：

## 是否可以 Direct Change？
- [ ] 正确目标已经清楚
- [ ] 不新增 capability
- [ ] 不改变 approved behavior/contract/state/security/persistence/architecture
- [ ] blast radius 小
- [ ] 没有重要 design fork
- [ ] 通常单 session 可完成

如果全部 Yes，优先 Direct Change。

## 如果必须 Work Item
- [ ] 有 coherent change boundary
- [ ] 能独立设计
- [ ] 能独立验证
- [ ] 能独立 Gate C acceptance
- [ ] 不是 implementation Task
- [ ] 属于当前 approved Milestone / capability

## 如果不属于 approved scope
- [ ] 是新 capability/direction → Proposal → Review → Gate R
- [ ] 是 approved design divergence → Gate A
