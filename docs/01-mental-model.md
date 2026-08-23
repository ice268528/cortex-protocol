# 01. 心智模型：三层设计 + 四个 Human Gate

## 0. 先用一句话抓住 Cortex

> **Project-level 的重要判断由 Human 保留，change-level 的工程执行尽量交给 Agent，长期状态进入 Repository，而不是留在人脑和聊天历史里。**

如果你还没理解为什么要这样分工，先读 [`../WHY.md`](../WHY.md)。

## 1. 三种不同层级不要混在一起

### 项目级长期设计

由你和网页版 ChatGPT 在 0→1 阶段完成，主要落在：

```text
docs/project/
docs/stages/
TODO.md
```

它回答的是：产品是什么、系统长期应该是什么样、阶段目标是什么、当前要交付哪个项目级 change。

### Change-level 工程设计

由 Claude Code 在当前 Work Item 上结合真实代码和 Superpowers 形成 spec。它回答的是：**这一次 change 在当前代码库里具体应该如何工作。**

### Implementation-level 执行

由 Superpowers 的 plan / execution 流程继续拆解并执行。它回答的是：改哪些文件、写哪些测试、按什么顺序实现、如何 review 和 verification。

这三层如果混在一起，常见后果是：`TODO.md` 充满函数级任务、`CLAUDE.md` 重复 Superpowers、项目设计被某个临时实现细节污染。

## 2. Human 的职责应该越来越少

人不应该长期扮演“流程调度器”。理想状态下，人只做四类高价值判断：

```text
理解 → 选择 → 批准 → 验收
```

而不是记住：

```text
现在是不是该更新 TODO？
是不是该同步 domain 文档？
是不是该再做一次 review？
这个服务是不是该关？
```

这些属于可编码进仓库规则的 housekeeping。

## 3. 四个 Gate 的真正区别

### Gate A：Design Divergence

触发条件不是“实现遇到困难”，而是**真实工程证据与已批准的重要设计发生冲突**。

局部实现差异通常由 Agent 自己处理；产品行为、业务规则、Domain semantics、核心状态机、Architecture、Security boundary、Stage Goal/AC 等实质变化才需要停下来。

### Gate B：Spec Review

人审的是“系统设计是不是我要的”，不是“函数怎么写”。Review Packet 应帮助人看懂业务流程、数据流、状态变化、关键计算、持久化边界、外部服务交互；如果有 AI Agent，还要解释 context、tools、tool result、state 和最终 decision ownership。

### Gate C：Feature Acceptance

工程验证完成后，人亲自确认真实功能。Agent 应给出已完成验证、手动场景、操作方式、预期结果和无法自动验证的部分。

### Gate D：Stage Acceptance

不是“最后一个 Work Item Done”就自动算 Stage 完成。还要回到 Stage Goal、Acceptance Criteria、Work Items 和实际系统做整体判断。

## 4. 一个重要原则：不要重复 Superpowers

如果 Superpowers 已经负责 brainstorming、spec、plan、隔离工作区、TDD、task review、whole-change review、verification 等流程，就不要在 `CLAUDE.md` 重新发明一套相同机制。

`CLAUDE.md` 更应该写 Superpowers 不知道的项目级约束：Repository 状态源、Gate A/B/C/D、文档生命周期、PR standing policy、E2E 沉淀、coding-guides 的按需读取等。
