# Feedback Inbox — Domain & State Model

## Feedback

核心字段：

- `id`
- `author_user_id`
- `title`
- `description`
- `category` — 可为空，triage 后设置
- `status` — `new | triaged | resolved`
- `created_at`
- `updated_at`

## State Transitions

```text
new → triaged → resolved
```

V1 不支持 reopen。

## Ownership

- 员工创建 Feedback；
- Support 拥有 category 和 status 的处理权限；
- 普通员工不能修改 triage 状态。
