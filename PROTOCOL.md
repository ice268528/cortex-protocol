# Cortex Protocol — Core Protocol

本文是 Cortex Protocol 的核心规范。教程解释“为什么”，本文件定义“各方必须如何协作”。

文中的 **MUST / 必须** 表示协议不变量；**SHOULD / 应该** 表示默认策略；**MAY / 可以** 表示项目可按实际情况调整。

## 1. Participants

### Human

Human **MUST** 保留以下决策权：

- 重大上游设计变化；
- change-level spec 的业务/系统行为批准；
- Work Item 的真实功能验收；
- Stage 的最终验收。

Human **SHOULD NOT** 长期承担 TODO 更新、文档同步提醒、review 调度、服务清理等可编码的 housekeeping。

### Web ChatGPT

Web ChatGPT 用于 0→1 的 project-level design convergence。

它 **MUST NOT** 在 Human 尚未理解和确认当前设计层时，替 Human 一次性决定后续全部设计。

### Repository

Repository 是跨会话、跨 Agent 的 durable state carrier。

Repository **MUST** 能回答至少四个问题：

1. 系统长期应该是什么样？
2. 当前 Stage 承诺什么？
3. 当前 Work Item 是什么？
4. 真实代码、测试、配置和 Git 状态是什么？

### Claude Code

Claude Code 负责从 Repository 恢复当前状态，并推进 Current Work Item。

它 **MUST** 在 coding 前验证相关设计假设与工程现实，而不是把文档当作不可质疑的事实。

### Superpowers

Superpowers 负责 change-level engineering workflow。Cortex Protocol **MUST NOT** 重复实现其已有的 brainstorming、spec、plan、隔离执行、TDD、review、verification 等机制。

## 2. Canonical State

### `docs/project/`

保存 current long-term design。它是“系统现在应该是什么样”，不是聊天日志。

### `docs/stages/`

保存 Stage 的 Goal、Scope / Non-goals、Work Items、Acceptance Criteria。

### `TODO.md`

保存项目级 Work Item queue 和状态。它 **MUST NOT** 复制 implementation plan 的文件级/函数级任务。

### `CLAUDE.md`

保存 Agent standing policy、cold start、Human Gates、按需加载规则和项目特定工程入口。

### `docs/superpowers/`

保存当前 change 的 spec / plan（若实际 Superpowers 版本使用不同路径，以实际路径为准）。这些文档是 change-level artifacts，不替代长期 project design。

## 3. Context Loading Rule

每个 Work Item 开始时，Agent **SHOULD** 只加载完成当前判断所需的最小上下文：

- Current Work Item；
- 所属 Stage；
- 相关 project docs；
- 真实代码、测试、配置、依赖版本；
- 当前 change 已存在的 spec / plan。

Agent **MUST NOT** 为了“全面了解项目”默认扫描全部 `docs/`。

`docs/coding-guides/` **MUST NOT** 默认加载；只有 Human 明确指定某个 guide 或实现点时才读取。

## 4. Work Item Lifecycle

```text
Current Work Item
→ cold start + reality check
→ [Gate A if needed]
→ Superpowers brainstorming
→ change-level spec
→ Gate B
→ plan / implementation / tests / review / verification
→ PR / CI / applicable E2E
→ Gate C
→ Work Item Done
→ next Work Item OR Gate D
```

### Before implementation

Agent **MUST** 先检查 Repository state 和工程现实。

如果差异只是局部工程实现问题，Agent **SHOULD** 在 change-level design 内解决。

如果差异会实质修改产品行为、业务规则、Domain semantics、核心状态机、Architecture、Security boundary、Stage Goal/AC 或大范围 Stage scope，Agent **MUST** 进入 Gate A。

## 5. Human Gates

### Gate A — Design Divergence

**Trigger:** 已验证工程证据与重要上游设计发生实质冲突。

Agent **MUST** 提交：原设计、工程证据、冲突原因、建议修改、alternatives、受影响 project/stage/TODO/spec/plan。

在 Human 决定前，Agent **MUST NOT** 继续受影响实现，也 **MUST NOT** 静默修改重大设计。

### Gate B — Spec Review

**Trigger:** 当前 Work Item 的 change-level spec 已收敛并准备进入 plan。

Agent **MUST** 提供 spec，并 **SHOULD** 提供 Design Review Packet，帮助 Human 理解与当前 change 相关的业务流程、数据流、状态变化、关键计算、持久化和外部服务边界。

AI Agent 功能还 **SHOULD** 解释 input、context assembly、model context、tools、tool execution、tool result 回流、agent state、output 和最终业务 decision ownership。

Human 审的是系统行为，不是 implementation task decomposition。

### Gate C — Feature Acceptance

**Trigger:** 实现、必要自动验证、review 和适用 E2E 完成。

Agent **MUST** 提供实际完成内容、实际执行过的验证、手动验收场景、操作、预期结果和无法自动验证的部分。

Human accepted 前，Work Item **MUST NOT** 标记为 Done。

### Gate D — Stage Acceptance

**Trigger:** Stage 的 Work Items 和 Acceptance Criteria 看起来均已满足。

Agent **MUST** 基于 Stage Goal、AC、Work Items 和当前实际系统说明为什么 Stage 已完成。

Human accepted 后，Agent 才 **MAY** 执行 final reconciliation、archive 和 next stage transition。

## 6. Documentation Reconciliation

Gate 通过后，Agent **MUST** 主动判断哪些文档真正受影响，无需等待 Human 点名文件。

- Gate A 后：同步受影响的 project/stage/TODO/spec/plan；
- Gate C 后：更新 TODO，并沉淀仍长期有效的新事实；
- Gate D 后：final reconciliation，归档过时 Stage-scoped 文档，更新必要 index/README。

Agent **MUST NOT** 为了形式一致而无关地重写未受影响文档。

## 7. PR, Review and E2E

正常 feature/fix **SHOULD** 使用独立 branch/worktree 并通过 PR 集成，除非项目另有明确 standing policy。

PR 创建本身 **MUST NOT** 成为机械重复 review 的理由。如果当前 PR HEAD 就是已经完成等价 clean review 的 HEAD，可以复用结论；HEAD 或 review 前提变化时再 review。

有长期回归价值的 Playwright E2E **SHOULD** 成为 Repository regression asset：已有覆盖则复用，行为变化则修改，新行为才新增。

## 8. Stage Closeout

Stage accepted 后，Agent **SHOULD**：

1. reconcile current docs 与实际系统；
2. 识别过时 Stage-scoped artifacts；
3. 使用可追踪的 Git move/archive 方式归档；
4. 更新相关 README/index；
5. 切换到 next Stage / Work Item。

仍代表 current truth 的长期 `docs/project/` **MUST NOT** 被机械归档。

## 9. Protocol Invariants

以下规则是 Cortex Protocol 最重要的不变量：

1. **重大设计变化不能静默发生。**
2. **Spec approval 与 Feature acceptance 是两种不同判断。**
3. **Plan 默认属于 Agent 工程执行层，不制造额外 Human Gate。**
4. **TODO 记录项目级 Work Item，不复制 implementation tasks。**
5. **Repository state 优先于聊天记忆。**
6. **Agent 维护 housekeeping，Human 保留高价值判断。**
7. **Cortex Protocol 不重复 Superpowers 已经提供的 change-level workflow。**
8. **只加载当前任务需要的最小上下文。**

只要这八条仍成立，项目可以自由调整目录名、工具、技术栈和具体命令，而不破坏 Cortex Protocol 的核心。
