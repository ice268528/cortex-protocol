# FB-01 — Gate C Feature Acceptance Packet

## Work Item

`FB-01 Submit Feedback`

## Completed Capability

已登录员工可提交 title + description；成功后 Feedback 被保存为 `status=new`、`category=null` 并绑定当前用户。

## Automated Verification

示例（真实项目必须只列实际执行过的验证）：

- unit: passed
- integration: passed
- code review: clean
- relevant E2E: passed

## Manual Scenario 1 — Successful Submit

前置：以普通员工身份登录。

操作：填写合法 title + description，点击 Submit。

预期：

- 页面显示成功；
- 新 Feedback 出现在对应数据源；
- status 为 `new`；
- category 为空；
- author 为当前员工。

## Manual Scenario 2 — Validation

操作：title 为空提交。

预期：

- 页面显示 validation error；
- 不创建 Feedback。

## Human Decision

请判断：这个真实功能是不是你要交付的 FB-01？
