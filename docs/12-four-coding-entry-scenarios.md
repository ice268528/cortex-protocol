# 12. 四种现实 Coding 场景

## 1. New Project

```text
starter
→ Web ChatGPT Product Exploration
→ project docs
→ Coding Agent Bootstrap Review
→ first meaningful Work Item
→ Spec
→ Gate B
```

## 2. Existing Project + New Feature

```text
Web ChatGPT
→ Proposal
→ Coding Agent Review
→ Gate R
```

Gate R 不只是“允许开始”。

如果 Agent 建议：

```text
DEFER
BLOCK
REJECT
ABSORB
```

也必须问 Human 是否同意该判断。

## 3. Mid-flight Idea

Human 直接告诉 Coding Agent。

Agent 判断：

```text
PLAN_LOCAL
DIRECT_CHANGE
APPROVED_CAPABILITY_NEEDS_WORK_ITEM
APPROVED_DESIGN_CHANGE → Gate A
NEW_CAPABILITY → Proposal → Gate R
```

不要 silent expand 当前 Work Item。

## 4. Bug / Real-use Feedback / Small UI

Human 最简单输入：

```text
Actual:
Expected / Desired:
Context:
```

Agent 优先判断 Direct Change：

```text
明确 bug
copy / spacing / alignment / color
non-semantic UI polish
equivalent refactor
small test/build/config fix
```

流程：

```text
inspect
→ fix
→ targeted verification
→ review
→ report
```

如果“前端小改”其实改变：

```text
confirm
undo
loading
error
navigation
state transition
permission
```

就不能仅按视觉 tweak 处理。

如果是 approved design change → Gate A。
