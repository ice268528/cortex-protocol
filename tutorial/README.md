# Guided Tutorial — 用 Feedback Inbox 跑完第一次 Cortex Protocol

这个 Tutorial 的目标不是让你背规则，而是让你**亲手经历一次正确的人机分工**。

我们用一个虚构但足够真实的小项目：**Feedback Inbox**。

产品想法只有一句：

> 做一个内部 Feedback Inbox，让用户提交反馈，团队可以查看、分类并处理。

你会从这句话开始，一直跑到第一个 Work Item 通过 Gate C，再演示新 Claude Code session 如何恢复状态。

## 你将完成什么

```text
一句产品想法
→ Web ChatGPT 逐文件设计
→ accepted project docs
→ Stage / Work Item
→ Repository state
→ 第一次 Claude Code handoff
→ Superpowers spec
→ Gate B
→ Agent execution
→ Gate C
→ Work Item Done
→ 新 session resume
```

## 使用方式

按顺序读：

1. [`00-start.md`](00-start.md) — 先知道整个练习在做什么
2. [`01-project-design.md`](01-project-design.md) — 逐文件设计，不让 AI 一次性替你决定所有东西
3. [`02-stage-and-work-item.md`](02-stage-and-work-item.md) — 从长期设计拆出 Stage 和 Work Item
4. [`03-repository-setup.md`](03-repository-setup.md) — 把设计变成可恢复 Repository state
5. [`04-first-handoff.md`](04-first-handoff.md) — 第一次交给 Claude Code
6. [`05-gate-b.md`](05-gate-b.md) — Human 第一次真正回来：审 Spec，不审 Plan
7. [`06-execution.md`](06-execution.md) — Human 不插手的阶段
8. [`07-gate-c.md`](07-gate-c.md) — 验真实功能，不是验代码细节
9. [`08-resume.md`](08-resume.md) — 新 session 只靠 Repository 恢复

示例最终状态在 [`final-state/`](final-state/)。

## Tutorial 中反复出现的两个框

### YOUR JOB RIGHT NOW

告诉你此刻 Human 真正应该判断什么。

### DON'T DO THIS

告诉你此刻**不要重新接管 Agent 的工作**。

Cortex Protocol 很大一部分价值，不是教 Human 多做什么，而是教 Human **哪些事情以后不用再做**。
