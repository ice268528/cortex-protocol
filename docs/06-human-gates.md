# 06. Human Gates：人什么时候必须回来

四个 Gate 的目标不是“增加审批”，而是把 Human judgment 集中在真正有价值的节点。

一个简单判断原则：

> **如果问题可以由工程证据 + 已批准设计直接决定，Agent 应自己处理。**
>
> **如果问题会改变 Human 曾经批准的产品/系统语义，或需要 Human 判断真实结果是否可接受，才回到 Gate。**

---

## Gate A — Design Divergence Review

### 触发

实际工程证据足以说明已批准的重要设计需要实质修改。

### Agent 应提交什么

- 原设计是什么；
- 新的工程证据是什么；
- 为什么两者冲突；
- 建议修改什么；
- alternatives；
- 影响哪些 `docs/project/`；
- 影响哪些 Stage；
- 影响哪些 TODO；
- 当前 spec/plan 是否需要作废或重做。

### Human 的工作

回答：**这个已批准的重要设计真的要改吗？**

批准后由 Agent 主动 reconcile 受影响文档，然后判断是否需要回到 brainstorming/spec/plan。

### Gate A examples / non-examples

| 情况 | Gate A? | 原因 |
|---|---:|---|
| 内部 API 方法名和设计文档不同 | No | implementation detail，业务语义未变 |
| DB 字段改名但语义不变 | No | storage implementation detail |
| ORM 需要额外 mapping 层 | 通常 No | 只要长期行为/边界不变 |
| error handling 结构需要重构 | No | change-level engineering detail |
| 原设计允许退款，但真实支付 API 不支持该行为 | Yes | 产品行为可能改变 |
| 为兼容真实 API，Domain 必须新增一个核心状态 | Yes | Domain semantics / state machine 改变 |
| 实际认证方案要求扩大受信任边界 | Yes | Security boundary 改变 |
| 当前 Work Item 实际需要跨出 Stage 原 scope 才能成立 | Yes | Stage scope / Goal 可能改变 |
| 单元测试目录结构与预期不同 | No | test structure 不属于上游设计 |

### 快速判断

问自己：

> “如果 Human 完全不知道这个变化，最后看到系统时，会不会发现自己批准过的行为、规则、状态、边界或 Stage 承诺已经变了？”

如果答案是 **会**，通常应该进入 Gate A。

---

## Gate B — Spec Review

### Agent 应提交什么

除 spec 本身，再给一份 **Design Review Packet**。只展示当前 change 真正相关的内容，例如：

- 业务流程；
- 数据流；
- 状态变化；
- 关键计算逻辑；
- Persistence 边界；
- External Service Interaction；
- 用户可观察的失败路径。

如果是 AI Agent 功能，还应解释：输入、context assembly、model context、tools、tool selection、tool execution、tool result 回流、agent state、最终 output、最终业务 decision ownership。

### Human 的工作

回答：**这个系统设计是不是我要的？**

不批准就回 brainstorming；批准就进入 plan/execution。

### YOUR JOB RIGHT NOW

```text
✓ 看业务流程
✓ 看数据流
✓ 看状态变化
✓ 看系统边界
✓ 看最终用户/业务行为

✗ 不 review 文件怎么拆
✗ 不指定函数怎么写
✗ 不手工设计测试步骤
✗ 不 review implementation plan（默认）
```

### Gate B examples / non-examples

| Human 反馈 | 适合 Gate B? | 原因 |
|---|---:|---|
| “这个审批状态不应该自动进入 approved。” | Yes | 系统行为/状态语义 |
| “失败时用户应该看到可重试，而不是永久失败。” | Yes | 用户可观察行为 |
| “这里应该由业务服务拥有最终 decision，而不是模型。” | Yes | decision ownership |
| “把这个 class 拆成两个文件。” | No | implementation detail |
| “我更喜欢这个测试放 integration 目录。” | No | implementation detail |

---

## Gate C — Feature Acceptance

### 前置条件

实现、必要自动验证、review、适用的 E2E 已完成。

### Agent 应提交什么

- Work Item / PR；
- 实际完成内容；
- 已执行的 unit/integration/CI/review/E2E；
- 需要手动验收的场景；
- 每个场景的操作与预期；
- 尚无法自动验证的内容；
- 人工验收所需的服务和入口。

### Human 的工作

回答：**这个真实功能是不是我要的？**

通过后，Agent 才把 Work Item 标为 Done。

### YOUR JOB RIGHT NOW

```text
✓ 按场景实际使用功能
✓ 看真实用户结果
✓ 看不可自动验证的产品体验
✓ accepted / not accepted

✗ 不重新做一遍 code review
✗ 不提醒 Agent 更新 TODO
✗ 不点名要同步哪份 Markdown
✗ 不把“测试绿了”当成 Feature accepted
```

### Gate B 和 Gate C 的区别

```text
Gate B：设计上，这个功能应该这样工作吗？
Gate C：真实运行起来，它真的这样工作，而且是我想要的吗？
```

---

## Gate D — Stage Acceptance

### Agent 应提交什么

基于 Stage 的 Goal、Acceptance Criteria、Work Items 和当前实际系统，说明为什么 Stage 已满足。

### Human 的工作

回答：**这个 Stage 承诺的能力是否完整交付？**

明确 accepted 后，Agent 才执行 final reconciliation、archive 和进入下一 Stage。

### YOUR JOB RIGHT NOW

```text
✓ 回到 Stage Goal
✓ 逐条看 Acceptance Criteria
✓ 看整个 Stage 的能力组合
✓ 明确 accepted / not accepted

✗ 不因为“最后一个 Work Item Done”就自动接受 Stage
✗ 不提前设计下一 Stage 的 implementation plan
```

---

## Mini Quiz：Is this a Gate?

先自己回答，再展开答案。

1. 数据库字段名与设计不同，但业务语义完全一致。Gate A？
2. 真实 API 要求核心状态机新增一个状态。Gate A？
3. Spec 行为已经批准，Agent 给出一个 20 步 implementation plan。需要新增 Human Gate review plan 吗？
4. 所有测试都绿了，但用户真实操作路径和预期不一致。Gate C 应该 accepted 吗？
5. Stage 最后一个 Work Item 完成，但一条 Acceptance Criteria 没有证据。Gate D 可以 accepted 吗？

### 答案

1. **通常 No。** 这是局部实现差异。
2. **Yes。** Domain semantics / state machine 改变。
3. **默认 No。** Plan 属于 Agent 工程执行层；只有它暴露重大设计偏差才转 Gate A。
4. **No。** 自动验证不能替代真实 Feature Acceptance。
5. **No。** Stage completion 不是“最后一个 Work Item Done”的同义词。
