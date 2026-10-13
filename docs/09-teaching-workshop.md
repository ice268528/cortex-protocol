# 09. 如何教 Cortex Protocol v2

## 学完应该能回答

1. Milestone / Work Item / Task 的区别；
2. Proposal 为什么不直接变 Requirement；
3. Gate R 为什么要 Human 确认 Agent recommendation；
4. Gate A 为什么是 interrupt；
5. Gate B 与 C 为什么不同；
6. Gate D 为什么不能由最后一个 Work Item 自动触发完成；
7. 什么改动可以 Direct Change；
8. Architecture 为什么不复制完整 API/DB schema。

## 推荐 90 分钟

### 0–15：失败模式

- 长会话丢上下文；
- Proposal 被 AI 偷偷变成需求；
- 小改流程过重；
- Agent 静默改 approved design；
- 文档与代码漂移。

### 15–30：Repository Memory + Taxonomy

```text
Milestone → Work Item → Task
```

### 30–45：Web ChatGPT

演示：

```text
长期讨论
→ File Output Contract
→ project docs / Proposal package
```

### 45–60：Proposal Review + Gate R

让 Agent 给出 DEFER / START_NOW recommendation，再让 Human 明确确认或反对。

### 60–75：Work Item B/C + Gate A

演示：

```text
Spec → B → Execution → C
```

并插入一个真实 engineering conflict 触发 A。

### 75–85：Direct Change

对比：

```text
改 spacing
vs
改变 delete confirmation semantics
```

前者 Direct Change，后者可能 Gate A。

### 85–90：Milestone Gate D

回到 Milestone DoD / AC，而不是只看最后一个 PR。
