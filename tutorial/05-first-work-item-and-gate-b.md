# 05 — 第一个正式 Work Item 和 Gate B

Work Item：

```text
FB-01 Submit Feedback
```

目标：

> 登录员工提交 title + description 后，系统可靠保存一条 Feedback，并得到明确成功/失败结果。

Agent：

```text
Repo Investigation
→ Spec
→ Gate B Packet
```

## Gate B Human 看什么

```text
用户提交行为
validation
Feedback initial state
source of truth
failure behavior
permission
persistence boundary
invariants
non-goals
```

不看：

```text
migration task 排第几
文件怎么拆
函数叫什么
test 放哪个目录
```

如果设计正确：

```text
Gate B accepted.
```

然后 Agent 自动执行 Gate B Post-decision sync：

```text
Spec → accepted / approved baseline
TODO → planning/execution
Plan → create/update from approved Spec
project-state → usually unchanged
```

再自主进入 Plan/Implementation。
