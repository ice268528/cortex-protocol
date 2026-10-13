# Prompt：Mid-flight Idea

```text
当前 Work Item approved scope 先保持不变。

我有一个新想法：
<内容>

请不要要求我先分类，也不要直接把它塞进当前 scope。

对照 Current Milestone / Work Item / Spec / Plan / relevant Architecture / code 后选择最小正确路径：

1. PLAN_LOCAL
   不改变 approved semantics：
   → 直接调整，只有影响后续执行/恢复时才更新 Plan。

2. DIRECT_CHANGE
   与当前 Work Item 无关但小、明确、低风险：
   → 不污染当前 branch/PR；按 Git policy 安排。

3. APPROVED_CAPABILITY_NEEDS_WORK_ITEM
   已在 Roadmap，但需要独立 design/acceptance：
   → new Work Item → Spec → Gate B。

4. APPROVED_DESIGN_CHANGE
   需要改变 approved project/Milestone/change design：
   → Gate A。

5. NEW_CAPABILITY_OR_DIRECTION
   → Proposal → Coding Agent Review → Gate R。

不要 silent expand 当前 Work Item。
```
