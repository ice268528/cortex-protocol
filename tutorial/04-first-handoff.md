# 04 — 第一次把 Repository 交给 Claude Code

现在才进入 Coding Agent 实施阶段。

## 发送什么

使用 [`../prompts/first-handoff-to-claude-code.md`](../prompts/first-handoff-to-claude-code.md)。

注意：这个 Prompt **没有重新解释 Feedback Inbox 的产品背景**。

因为背景已经在 Repository。

## Claude Code 此时应该先做什么

```text
1. git / worktree reality check
2. 读取 TODO → FB-01
3. 读取所属 Stage
4. 读取与 FB-01 相关的 project docs
5. 查看真实代码 / tests / config / dependency versions
6. 判断设计假设与工程现实是否冲突
```

然后只有两条路：

```text
重大上游设计冲突
→ Gate A

没有重大冲突
→ Superpowers brainstorming → spec
```

## 一个不是 Gate A 的例子

Agent 发现项目实际使用的 ORM 字段命名约定与文档示例不同，但反馈实体、状态和行为都不变。

这通常是局部工程差异，Agent 自己处理。

## 一个应该 Gate A 的例子

Agent 实际验证后发现现有认证体系无法可靠识别提交者，而产品设计明确要求每条 Feedback 必须关联已登录员工身份。

如果解决方案会改变身份/安全边界或产品行为，Agent 应停下来提交 Gate A packet。

## YOUR JOB RIGHT NOW

如果没有 Gate A：

```text
什么都不用做。
让 Agent 形成 change-level spec。
```

## DON'T DO THIS

```text
✗ Agent 刚开始就告诉它应该改哪些文件
✗ 重新把项目背景复制一遍
✗ 为了“保险”让它先扫描整个 docs/
```

下一步：[`05-gate-b.md`](05-gate-b.md)。
