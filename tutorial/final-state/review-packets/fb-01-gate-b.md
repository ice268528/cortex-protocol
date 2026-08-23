# FB-01 — Gate B Design Review Packet

## Business Flow

已登录员工填写 title + description，提交后创建一条归属当前用户的 Feedback。

## Data Flow

```text
authenticated user
→ POST feedback input
→ validate auth + fields
→ persist Feedback
→ return created representation
```

## State

新建 Feedback：

- `status = new`
- `category = null`
- `author_user_id = current user`

## User-visible Failures

- 未登录：要求登录，不创建记录；
- 非法输入：显示字段错误，不创建记录；
- persistence failure：显示可重试错误，不显示成功。

## Persistence Boundary

只有服务端完成 validation 后才持久化；UI 不自行推断创建成功。

## Human Decision

请判断：上述系统行为是否符合 FB-01 和已批准的 project design？
