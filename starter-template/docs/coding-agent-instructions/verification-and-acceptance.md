# Verification and Acceptance

> 仅在正式 Work Item 进入 verification、E2E 或 Gate C 时读取；Direct Change 只需按 impact 做 targeted verification，不为流程强行加载本文件全部步骤。

## 1. Impact → Verification
按实际影响选择最小充分验证，不按固定清单机械执行：
- behavior/logic：相关 unit/integration + regression；
- public/cross-module contract：同时验证 producer/consumer 与兼容性；
- persistence/migration：验证 schema/migration、失败/恢复和必要的数据一致性；
- security/permission：同时验证 allowed 与 denied path；
- build/config/dependency：执行受影响命令并验证最接近的回归面；
- user-visible flow：有长期回归价值时使用 E2E。

只汇报实际执行过的验证，不把“理论上应该通过”写成已验证。

## 2. Playwright / E2E
当前 Work Item 存在适合自动化的用户可见流程时：
1. 先检查现有 Playwright 覆盖；
2. 已覆盖则复用；
3. 预期行为变化则修改已有测试；
4. 只有新增长期有回归价值的行为才新增测试。

不要为了满足流程强行创建没有长期价值的 E2E。
有长期回归价值的 Playwright 测试应提交到仓库，不作为一次性验收脚本丢弃；优先验证用户可观察行为并复用已有 fixture/helper。
截图/快照按根 `CLAUDE.md` 放入 `otherfiles/`，除非它本身就是需要版本控制的正式测试基线。

## 3. Review 与 Gate C readiness
进入 Gate C 前至少确认：
- approved Spec scope 已实现；
- 必要自动验证已执行并有结果；
- review/fix 已完成；
- applicable E2E 已完成；
- 已知限制、未覆盖风险和无法自动验证内容已明确。

Gate C Packet 只提供当前 change 真正相关的信息：
- 本次实际完成内容；
- 已完成的自动验证 / review / E2E；
- Human 需要手动检查的最小场景；
- 操作方式与预期结果；
- 无法自动验证的内容和已知限制（如有）；
- 验收需要保持运行的服务/入口。

不要为了完整模板编造不适用场景。

## 4. Gate C failed
Human 验收失败后先判断反馈性质：
- implementation defect → 修复 → 重跑受影响验证 → 必要时更新/新增 E2E、重新 review → 再次 Gate C；
- plan-local implementation issue → 调整 → 验证 → 再次 Gate C；
- approved design / Milestone / accepted Spec 必须改变 → Gate A；
- new capability/direction → Proposal → Review → Gate R。

不要把产品语义变化伪装成普通 bug fix。
