# Prompt：Bug / Real-use Feedback / Small UI Change

```text
Actual:
<现在怎样>

Expected / Desired:
<希望怎样>

Context:
<复现步骤或补充>

请不要要求我先分类。

优先判断是否可以 Direct Change：

- 正确行为已经清楚；
- 不新增 capability；
- 不改变 approved interaction/state/public contract/security/persistence/long-lived architecture；
- blast radius 小；
- 没有重要 design fork。

如果满足：
→ minimal inspection
→ direct change
→ regression / targeted verification
→ review
→ report changed + verification + remaining risk

不要机械创建 maintenance Work Item / TODO / Spec / Plan / Gate B / Gate C。

如果不满足：
- current Work Item implementation defect → current WI 内 fix；
- approved capability but needs independent design → Work Item；
- approved design 本身必须变 → Gate A；
- new capability/direction → Proposal → Review → Gate R。
```
