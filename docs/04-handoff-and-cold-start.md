# 04. 从网页版交给 Claude Code

## 1. 第一次交接只做一件事：让 Agent 正式接管 Repository

前置条件：

```text
CLAUDE.md
+ docs/project/
+ docs/stages/
+ TODO.md
```

都已经存在，而且至少有一个 Current Work Item。

第一次交接时，不要把项目背景重新复制进 Prompt。真正的上下文应该已经在仓库里。

使用：[`../prompts/first-handoff-to-claude-code.md`](../prompts/first-handoff-to-claude-code.md)。

## 2. 冷启动应该先验证现实，再 coding

Agent 应先：

1. 检查 branch/worktree 和 `git status`；
2. 读取 Current Work Item；
3. 读取所属 Stage；
4. 读取相关 project docs；
5. 查看真实代码、测试、配置、依赖版本；
6. 如已有 spec/plan，读取当前 change 的对应文件。

然后判断：设计与工程现实是否冲突。

## 3. 两类“设计和现实不一致”要分开

### 局部工程差异

例如内部 API 调法、字段实现细节、error handling、test structure。通常由 Agent 在 change-level 设计里自己解决。

### 重大上游设计偏差

例如产品行为、业务规则、Domain semantics、核心状态机、Architecture、Security boundary、Stage Goal/AC 需要变化。此时必须进入 Gate A。

## 4. 后续会话

Repository 状态维护好以后，新会话使用：[`../prompts/resume-current-work-item.md`](../prompts/resume-current-work-item.md)。

目标是最终缩短到一句：

> 继续当前 Work Item。
