# 07 — Milestone Gate D

假设 M1 有：

```text
FB-01 Submit Feedback
FB-02 Support Inbox
FB-03 Manual Triage
```

三个 Work Item 都 Gate C accepted 后，还不能直接说 M1 accepted。

Agent 回到 `roadmap.md`：

```text
M1 User Capability
Definition of Done / Acceptance Criteria
```

逐条找 evidence。

例如：

```text
[✓] Employee can submit
[✓] Feedback durably exists
[✓] Support can view new feedback
[✓] Support can manually triage
```

然后：

```text
→ Gate D
```

Human 判断：

> **这一整层能力真的完整了吗？**

accepted 后才：

```text
roadmap → M1 accepted
project-state → Latest Accepted Milestone / Next / checkpoint
final reconciliation / archive
CLAUDE → only if every-session standing context changed
```

然后进入下一 Milestone。

