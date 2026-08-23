# START HERE — 把 Cortex Protocol 装进你的项目

> 如果你第一次接触 Cortex Protocol，建议先读 [`WHY.md`](WHY.md) 并完成 [`tutorial/README.md`](tutorial/README.md)。
>
> 本文件假设你已经理解核心思想，现在只想把它落到一个真实 Repository。

## Step 0：先确认职责边界

```text
Human 决策
Web ChatGPT 收敛 project-level design
Repository 保存真相和状态
Claude Code 推进 Current Work Item
Superpowers 做好单个 change
Human 只在 A / B / C / D Gate 回来
```

精确定义看 [`PROTOCOL.md`](PROTOCOL.md)，术语不熟看 [`GLOSSARY.md`](GLOSSARY.md)。

## Step 1：建立 Repository state

在真实项目建立：

```text
docs/project/
docs/stages/
TODO.md
```

- `docs/project/`：长期有效的产品、Domain、Data Flow、Architecture 等 current design；
- `docs/stages/`：阶段目标、范围、Work Items、Acceptance Criteria；
- `TODO.md`：项目级 Work Item queue，不放 implementation tasks。

## Step 2：网页版 ChatGPT 一次只设计一个文件

使用 [`prompts/web-design-session.md`](prompts/web-design-session.md)。

```text
当前设计文件
→ 暴露需要 Human 理解/选择的问题
→ 逐项讨论
→ 决策问题清零
→ “当前设计已收敛”
→ 输出最终文件
→ Human accepted
→ 下一个文件
```

常见顺序可以是：产品定位/边界 → 技术约束 → Domain/State → Data Flow → Architecture → Stage decomposition，但不是固定模板。

如果后面的设计暴露上游错误，回到上游修正，再继续；不要在下游静默绕过。

## Step 3：拆 Stage 和 Work Item

每个 Stage 至少表达：

- Goal
- Scope / Non-goals
- Work Items
- Acceptance Criteria

每个 Work Item 应是一个相对独立、可验证的项目级 change。

然后在 `TODO.md` 建立 `Current / Next / Blocked / Done`。

用 [`checklists/work-item-readiness.md`](checklists/work-item-readiness.md) 检查粒度。

## Step 4：安装项目侧规则

把 [`starter-template/`](starter-template/) 合并进真实 repo：

- `CLAUDE.template.md` → 填写后作为根 `CLAUDE.md`；
- `TODO.template.md` → 按真实 Work Item 填写；
- `docs/coding-agent-instructions/` → 填入项目真实命令、目录、测试、服务和 Git 约束；
- `templates/` → 可选的 project/stage 文档骨架。

不要保留 `【占位符】` 就开始开发。

## Step 5：确认 Current Work Item ready

至少确认：

- 有稳定 ID 和标题；
- 归属某个 Stage；
- 相关上游设计已 accepted；
- 有可验证的完成边界；
- 不是“改某文件第几行”这种 implementation task。

## Step 6：第一次交接给 Claude Code

发送 [`prompts/first-handoff-to-claude-code.md`](prompts/first-handoff-to-claude-code.md)。

第一次交接不是重新解释整个项目，而是要求 Claude Code：

1. 按 `CLAUDE.md` 冷启动；
2. 从 Current Work Item 恢复状态；
3. 先验证设计假设与工程现实；
4. 有重大偏差就进入 Gate A；
5. 没有偏差就进入 Superpowers change-level workflow。

## Step 7：之后只在四个 Gate 做高价值判断

- **A — Design Divergence**：重要设计真的需要改吗？
- **B — Spec Review**：这个系统设计是不是我要的？
- **C — Feature Acceptance**：真实功能是不是我要的？
- **D — Stage Acceptance**：这一阶段承诺是否完整交付？

速查见 [`checklists/human-gates-cheatsheet.md`](checklists/human-gates-cheatsheet.md)。

## Step 8：让新会话从 Repository 恢复

项目跑起来后，新 Claude Code session 使用：

> 继续当前 Work Item，按 `CLAUDE.md` 冷启动并恢复当前状态。

Repository state 足够可靠时，可以缩短成：

> 继续当前 Work Item。

这就是 Cortex Protocol 想达到的状态：**你不再用 Prompt 搬运项目记忆。**
