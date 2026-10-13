# WHY — Cortex Protocol v2 为什么这样设计

Cortex 不是为了增加流程，而是解决 Agent-driven development 中几类反复出现的问题。

## 1. 聊天历史不是可靠项目记忆

长时间和 Web ChatGPT / Coding Agent 对话后，真正需要跨 session 保存的是：

```text
Product intent
Milestone commitment
Current Work Item
Approved design
Architecture truth
Open blocker
```

所以 Repository 必须成为 durable memory。

---

## 2. Human 不应该 babysit housekeeping

Human 应该把注意力留给：

```text
Proposal 是否接受这个判断？    → Gate R
重大 approved design 是否要改？ → Gate A
Spec 行为是否正确？             → Gate B
真实功能是否成立？              → Gate C
Milestone 能力是否完整？         → Gate D
```

而不是不断提醒 Agent：

- 更新 TODO；
- 同步某个 README；
- 再跑一次 review；
- 服务测试后记得关。

---

## 3. Proposal 不能偷偷变 Requirement

Web ChatGPT 很适合探索，但它不知道真实 repo。

所以已有项目中新 capability：

```text
Human + Web ChatGPT
→ Proposal
→ Coding Agent Review
→ Gate R
```

关键是：

> **Coding Agent recommendation 仍然只是 recommendation。**

如果它认为应该以后做、不能做、不值得做，Human 仍然需要确认这个判断，而不是 Agent 自动把想法归档掉。

这就是 Gate R。

---

## 4. Gate A 为什么不是正常下一步

大多数 Work Item：

```text
Spec → B → Plan/Code → C
```

不应该机械经过 Gate A。

Gate A 只在真实证据说明：

> **“继续正确实现，必须改变已经批准的重要设计。”**

时触发。

因此它是 interrupt。

---

## 5. 为什么 Stage 被删除

v1 使用：

```text
Stage → Work Item → Task
```

v2 收敛成：

```text
Milestone → Work Item → Task
```

Milestone 直接表达一整层 User Capability 和 Definition of Done。

不再额外保留一个含义接近的 Stage 管理层。

Milestone 默认放在 `roadmap.md`，避免目录继续膨胀。

---

## 6. 为什么小 bug 不应该强制 Spec + Plan

如果：

```text
改一个 spacing
修一个已经明确的 regression
修改 copy
做一个等价 refactor
```

也需要：

```text
TODO
Spec
Gate B
Plan
Gate C
```

那么流程会比改动本身更重。

所以 v2 正式允许 Direct Change。

但 Direct Change 不是逃避设计的借口：

```text
approved semantics 要变 → Gate A
new capability → Proposal → Gate R
needs independent design → Work Item
```

---

## 7. 为什么 Architecture 不能写成所有技术细节的副本

完整 API、DB schema、文件路径如果再复制一份 Markdown，很快会漂移。

Architecture docs 应保存：

```text
为什么这样分层
谁拥有数据/contract
哪些 invariant 不能破坏
关键数据流怎样跨边界
兼容性/一致性/安全边界是什么
```

而 exact endpoint / column / index / schema 让 source code、OpenAPI、migration 等表达。

---

## 8. 为什么 Spec 和 Plan 不一样

```text
Spec
= 这个 change 应该怎样工作

Plan
= 怎么把它实现出来
```

Human 默认需要审 Spec，而不需要审每个 implementation task。

否则 Human 又会变回项目经理/技术 babysitter。

---

## 9. 为什么 Gate B 与 Gate C 必须分开

```text
Gate B
= 设计上，这样工作对吗？

Gate C
= 真实运行起来，它真的这样工作并且是我要的吗？
```

测试全部绿色也不能替代真实产品验收。

---

## 10. 为什么还需要 Gate D

最后一个 Work Item Done 并不自动意味着整层能力完整。

Milestone Acceptance 要重新回到：

```text
User Capability
Definition of Done / Acceptance Criteria
整体系统 evidence
```

Human 明确 accepted 后才真正结束 Milestone。
