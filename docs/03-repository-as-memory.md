# 03. Repository as Memory

Repository 必须能让新 session 恢复：

```text
我们在造什么？
当前 Milestone 是什么？
当前 Work Item 是什么？
现在卡在哪个 Gate / blocker？
长期系统边界是什么？
真实代码/测试/config/Git 是什么？
```

## Canonical sources

```text
CLAUDE.md
→ standing policy

docs/project/product.md
→ product intent

docs/project/roadmap.md
→ Milestone / capability commitment

docs/project/project-state.md
→ Human-readable latest trusted checkpoint；同时给 Agent 恢复坐标

docs/project/architecture/
→ long-lived architecture truth / baseline

docs/proposals/
→ candidate changes + review/disposition history

TODO.md
→ Work Item queue only

spec / plan
→ Work Item design / implementation

code/tests/schema/config/git
→ engineering reality
```

## Cold Start

```text
CLAUDE
→ project-state（最近一次 checkpoint）
→ TODO（live Work Item/Gate state）
→ current Milestone in roadmap
→ relevant architecture
→ current Spec/Plan if active
→ code/tests/config/Git（验证 snapshot 之后的真实变化）
```

不默认读取整个 docs tree。

Proposal Inbox 也不默认打断 active Work Item。

## Direct Change

Direct Change 正常结束时，通常：

```text
code + tests + Git
```

就足够形成 durable evidence。

如果一个所谓 Direct Change 越来越需要 TODO / Spec / Plan 或新的 project-state checkpoint 才能跨 session 协调，说明它应该升级为 Work Item。
