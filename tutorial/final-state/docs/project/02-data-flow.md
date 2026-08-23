# Feedback Inbox — Data Flow

## Submit Feedback

```text
Authenticated Employee
→ Submit title + description
→ Server validates identity and input
→ Persist Feedback(author, status=new, category=null)
→ Return created Feedback
→ UI shows success
```

## Failure Behavior

- 未认证：拒绝创建并要求登录；
- title / description 不合法：返回可理解的 validation error；
- persistence 失败：不宣称创建成功，UI 显示可重试错误。

## Triage Flow

```text
Support opens Inbox
→ selects Feedback
→ chooses category
→ status new → triaged
```
