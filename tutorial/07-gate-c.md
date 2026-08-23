# 07 — Gate C：验真实功能，不是验“代码看起来完成了”

假设 FB-01 已完成实现、测试、review 和适用的 E2E。

Agent 应提交 Feature Acceptance Packet。

示例：[`final-state/review-packets/fb-01-gate-c.md`](final-state/review-packets/fb-01-gate-c.md)。

## YOUR JOB RIGHT NOW

按 Agent 给出的真实入口操作：

```text
Scenario 1
已登录员工填写标题和描述
→ 点击 Submit
→ 看到成功状态
→ 新 Feedback 被保存为 status=new

Scenario 2
标题为空
→ 提交
→ 用户看到 validation error
→ 不创建记录
```

然后回答：

> **“这个真实功能是不是我要的？”**

通过就明确：

```text
Accepted.
```

## 为什么测试全绿仍然需要 Gate C

自动验证回答：

> “实现是否满足机器可验证的断言？”

Gate C 回答：

> “这个真实产品能力是不是 Human 想交付的？”

二者不是同一个问题。

## Accepted 之后谁做 housekeeping

Agent 应自己：

```text
FB-01 → Done
→ reconcile 长期有效的新事实
→ 判断 Stage 是否完成
→ 若未完成，推进 Next Work Item
```

Human 不需要提醒“记得把 TODO 打勾”。

## DON'T DO THIS

```text
✗ 看到 CI green 就直接 accepted
✗ Gate C 时重新做一次完整 code review
✗ accepted 后逐份点名要求更新文档
```

下一步：[`08-resume.md`](08-resume.md)。
