# 11. Adoption Guide：把现有项目迁移到 Cortex Protocol

不需要为了采用 Cortex Protocol 重做整个项目。最稳妥的方法是先把“项目记忆”和“人类 Gate”从聊天历史里迁回 Repository。

## Phase 1：建立最小状态源

先补齐四个入口：

```text
CLAUDE.md
docs/project/
docs/stages/
TODO.md
```

不要一开始追求文档完美。先确保它们能分别回答：Agent 怎么工作、系统长期是什么、当前 Stage 为什么做、现在做到哪里。

## Phase 2：清理 TODO 粒度

把 `TODO.md` 里的文件级、函数级、测试步骤移出项目级队列。这些应该进入当前 change 的 plan。

保留能独立描述能力变化、能独立验证、能归属某个 Stage 的 Work Item。

## Phase 3：把隐含设计变成 current truth

从现有代码和已确认产品行为中，提炼仍然有效的长期设计到 `docs/project/`。

不要把旧聊天全文、历史争论或已废弃方案搬进去。需要历史时用 Git history / archive；`docs/project/` 的职责是 current truth。

## Phase 4：定义四个 Human Gate

把 Gate A/B/C/D 写入根 `CLAUDE.md`，并明确：

- 什么情况必须停；
- Agent 要给 Human 什么材料；
- Human 决定后谁负责 reconcile；
- 哪些工程细节不构成人工 Gate。

## Phase 5：去掉与 Superpowers 重复的流程

检查 `CLAUDE.md` 是否重新规定了 Superpowers 已经负责的 brainstorming、TDD、subagent、task review、whole-change review、verification 等流程。

重复规则越多，越容易出现两个 workflow 互相打架。保留项目级 standing policies 和衔接点即可。

## Phase 6：从一个 Work Item 试运行

不要一次迁移所有历史工作。选择一个边界清楚的 Current Work Item：

```text
cold start
→ reality check
→ Gate A if needed
→ spec
→ Gate B
→ execution
→ Gate C
```

跑通后再调整模板和项目规则。

## Phase 7：观察 Human 是否仍在 babysitting

如果 Human 仍频繁提醒：

- 更新 TODO；
- 同步某个文档；
- 运行 review；
- 关闭服务；
- 创建 PR；
- 归档 Stage；

说明这些职责还没有真正进入 Repository rules。把重复出现的 housekeeping 写进相应 coding-agent instruction，而不是继续依赖人记忆。

## 成功标准

迁移完成后，一个新的 Claude Code session 应该能够在不听完整项目背景的情况下：

1. 找到 Current Work Item；
2. 理解它属于哪个 Stage；
3. 找到相关长期设计；
4. 验证工程现实；
5. 知道什么时候自主推进、什么时候必须停下来找 Human。

如果这五件事做不到，优先修 Repository state，而不是继续加长启动 Prompt。
