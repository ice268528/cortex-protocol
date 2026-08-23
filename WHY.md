# Why Cortex Protocol

> 这不是“先规定一套流程，再要求大家遵守”。
>
> Cortex Protocol 是从 AI Coding 项目逐渐变复杂之后反复出现的问题，一步步推导出来的。

## 1. 小项目时，Prompt 看起来已经够了

最简单的 AI Coding 模式：

```text
Human
  ↓
“帮我做这个功能”
  ↓
Coding Agent
  ↓
Code
```

对于一次性脚本、小改动、短生命周期项目，这往往已经足够。

问题出现在项目开始具备：长期设计、多 Stage、多 Work Item、多 session、真实用户流程、外部依赖、PR/CI/E2E、多人或多 Agent 协作之后。

## 2. 第一个问题：聊天不是可靠的项目记忆

常见现象：

- 新 session 不知道上次为什么这么设计；
- Human 重新讲项目背景；
- Prompt 越来越长；
- 同一个事实在聊天、TODO、README、代码里出现多个版本；
- Agent 根据最近上下文行动，而不是根据项目当前真实状态行动。

### 推导

```text
项目必须跨 session 恢复
        ↓
状态不能只存在聊天里
        ↓
Repository 成为 durable state carrier
```

所以 Cortex Protocol 把不同状态放回 Repository：

```text
CLAUDE.md      → Agent 怎么工作

docs/project/ → 系统长期应该是什么样

docs/stages/  → 当前 Stage 承诺什么

TODO.md        → 现在做到哪个项目级 Work Item

code/tests/git → 工程现实
```

结论：**Repository truth > chat memory。**

## 3. 第二个问题：Human 开始变成流程调度器

项目变大后，Human 经常开始提醒：

```text
“记得更新 TODO。”
“这个改动是不是要同步 Domain 文档？”
“跑一下测试。”
“做完再 review。”
“记得开 PR。”
“Stage 结束后归档一下。”
```

这些动作本身可能重要，但大部分不是高价值 Human judgment。

### 推导

```text
可重复的 housekeeping
        ↓
应该写入 Repository rules
        ↓
由 Coding Agent 主动执行
```

Human 应逐渐从：

```text
Workflow Scheduler
```

退回到：

```text
理解 → 选择 → 批准 → 验收
```

## 4. 第三个问题：Agent 又不能完全自主

如果把所有权都交给 Agent，另一类问题会出现：

- 为了让代码跑通，Agent 静默改变产品行为；
- 为了适配依赖，Agent 改掉 Domain semantics；
- 为了实现方便，Agent改变核心状态机或安全边界；
- Human 最后看到“功能完成”，但系统已经不是原来批准的系统。

### 推导

不能在每一步都人工审批，因为那会重新变成 babysitting。

但重大判断也不能让 Agent 静默决定。

所以需要：

```text
Agent 默认自主推进
        +
少数明确的 Human Gates
```

Cortex Protocol 只保留四类高价值 Gate：

- **A — Design Divergence**：重大上游设计真的要改吗？
- **B — Spec Review**：这个 change 的系统行为是不是我要的？
- **C — Feature Acceptance**：真实功能是不是我要的？
- **D — Stage Acceptance**：阶段承诺是否完整交付？

## 5. 第四个问题：所有“设计”不是同一个粒度

如果把所有层级都放进一个 `CLAUDE.md` 或 TODO，会出现：

- TODO 充满“修改 foo.ts / 写 test X”这种实现任务；
- 临时实现限制污染长期架构文档；
- Human 被要求 review 文件级 implementation plan；
- Agent 不知道哪些设计是长期 baseline，哪些只是当前 change 的工程方案。

### 推导

需要分三层：

```text
Project-level design
→ 产品、Domain、Data Flow、Architecture、Stage、Work Item

Change-level design
→ 当前 Work Item 的具体系统行为 / spec

Implementation-level execution
→ 文件、函数、测试、顺序、review、verification
```

对应职责：

```text
Human + Web ChatGPT
        ↓ project-level
Repository baseline
        ↓
Claude Code + Superpowers
        ↓ change-level spec
Superpowers
        ↓ implementation-level execution
Code + tests + PR
```

## 6. 第五个问题：不要重新发明 Superpowers

如果 Superpowers 已经负责当前 change 内的：

- brainstorming；
- spec；
- writing plans；
- isolated worktree；
- TDD；
- subagent-driven development；
- task / whole-change review；
- verification / fix / re-review；

那么再在 `CLAUDE.md` 写一套同类 workflow，会产生两个互相竞争的流程。

### 推导

Cortex Protocol 只定义 **Superpowers 之外** 的项目级问题：

- project/stage/TODO 是什么；
- Claude Code 如何恢复状态；
- 什么是重大设计偏差；
- Human Gate 何时发生；
- Gate 时 Human 要看到什么；
- Gate 后谁负责 reconcile；
- PR/E2E/文档生命周期如何与项目长期状态衔接。

## 7. 最终得到 Cortex Protocol

```text
Human intent / judgment
          ↓
Web ChatGPT design convergence
          ↓
Repository durable truth + state
          ↓
Claude Code project-aware execution
          ↓
Superpowers disciplined change workflow
          ↓
Human returns only at meaningful Gates
```

最终目标不是让 Agent 做得越多越好，而是：

> **Human 和 Agent 各自在正确的层级工作。**

## 8. 什么时候不值得用 Cortex Protocol

它不是所有任务都需要的重型流程。

对于一次性脚本、几分钟能完成的小修改、没有长期状态的实验，直接 Prompt + Agent 可能更合适。

当项目开始出现以下任意几项时，Cortex Protocol 才开始显著有价值：

- 多 session；
- 多个项目级 Work Item；
- 需要长期设计一致性；
- Human 不希望持续 babysit Agent；
- Agent 可能碰到重要业务/架构边界；
- 需要 PR、CI、E2E、Stage 验收；
- 需要从聊天迁移到可恢复的 Repository state。

下一步：读 [`docs/01-mental-model.md`](docs/01-mental-model.md)，然后直接进入 [`tutorial/README.md`](tutorial/README.md)。
