# 02 — 从长期设计拆出 Stage 和 Work Item

Project design 已经足以支撑第一阶段开发后，再拆 Stage。

## 示例 Stage 1

目标：

> 让已登录员工能够提交反馈，并让 Support 团队看到一个可处理的 Inbox。

Stage 不写函数和文件任务，只定义：

- Goal
- Scope / Non-goals
- Work Items
- Acceptance Criteria

示例：[`final-state/docs/stages/stage-01-feedback-intake.md`](final-state/docs/stages/stage-01-feedback-intake.md)。

## 示例 Work Items

```text
FB-01 Submit Feedback
FB-02 Support Inbox
FB-03 Manual Triage
```

第一个 Current Work Item：

```text
FB-01 Submit Feedback
```

它的完成边界是“员工可以提交一条反馈，并且系统可靠保存为 `new` 状态”。

这和 implementation task 不一样：

```text
✗ 创建 migration
✗ 修改 feedback.ts
✗ 写 POST /api/feedback
✗ 写 integration test
```

这些应该由后续 Superpowers plan 拆。

## YOUR JOB RIGHT NOW

```text
✓ 判断 Stage 是否表达真实阶段承诺
✓ 判断 Work Item 是否是可独立验证的能力变化
✓ 选出 Current Work Item
```

## DON'T DO THIS

```text
✗ 把 TODO 变成文件级 task list
✗ 提前规定 implementation 顺序
✗ 同时推进多个无明确隔离的 Current Work Item
```

下一步：[`03-repository-setup.md`](03-repository-setup.md)。
