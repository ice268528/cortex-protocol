# 05. Superpowers 在一个 Work Item 里负责什么

## 边界

Cortex Protocol 把 Superpowers 当作 **change-level engineering workflow**。它不负责定义整个项目的产品方向，也不应该替代 `docs/project/`、`docs/stages/` 和 `TODO.md`。

## 推荐衔接

```text
Current Work Item
+ 当前 Stage
+ 相关 project docs
+ 真实代码/依赖
        ↓
Superpowers brainstorming
        ↓
change-level spec
        ↓
Gate B: Human Spec Review
        ↓ approved
Superpowers writing-plans
        ↓
隔离工作区 / implementation / TDD / review / verification
        ↓
PR / CI / E2E（按项目规则）
        ↓
Gate C: Feature Acceptance
```

## Gate B 为什么在 spec 后，而 plan 不需要人工 review

人真正需要判断的是“这个系统行为是不是我要的”。一旦 spec 已批准，implementation task decomposition、文件修改顺序、测试步骤等属于工程执行层，默认交给 Superpowers 和 Coding Agent。

因此这个工作流的策略是：

- **Spec 要人工审**；
- **Plan 默认不人工审**；
- 如果 plan 或 implementation 暴露重大上游设计错误，再跳出正常 loop 进入 Gate A。

## 不要在 `CLAUDE.md` 重复的内容

如果你的 Superpowers 版本已经负责这些能力，就不要再写第二套强制流程：

- brainstorming；
- spec 自审/用户 review gate；
- writing plans；
- worktree/isolation；
- subagent-driven development；
- TDD；
- task-level review；
- whole-change review；
- verification / fix / re-review；
- branch finishing 的内部工程步骤。

`CLAUDE.md` 只需要补充项目级约束和与这些能力的衔接点。
