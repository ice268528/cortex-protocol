# 09. 如何教 Cortex Protocol：90 分钟 Workshop

## 目标

学员结束后应该能：

1. 解释网页版 ChatGPT、Repository、Claude Code、Superpowers、Human 各自负责什么；
2. 用逐文件方式完成 0→1 设计；
3. 建立 `docs/project/`、`docs/stages/`、`TODO.md`；
4. 完成第一次 Claude Code handoff；
5. 区分 Gate A/B/C/D；
6. 不再把 Superpowers 已有流程重复塞进 `CLAUDE.md`。

## 课程安排

建议开场先用 [`../WHY.md`](../WHY.md) 的失败模式建立共同问题意识，再用 `PROTOCOL.md` 作为精确定义参考。不要让学员第一步就背规范。

### 0–15 分钟：先讲失败模式

让学员回忆：长会话上下文丢失、TODO 靠人脑记、Agent 静默改设计、文档与代码不一致、重复 review、一次性 E2E。

### 15–30 分钟：讲三层设计

用 [`01-mental-model.md`](01-mental-model.md) 解释 project-level / change-level / implementation-level 的边界。

### 30–50 分钟：演示网页版逐文件设计

使用 [`../prompts/web-design-session.md`](../prompts/web-design-session.md)，让 ChatGPT 只处理一个设计文件。重点演示“问题没清零前不生成最终文档”和“发现上游冲突就回退”。

### 50–65 分钟：把设计变成 Repository state

展示：

- `docs/project/`
- `docs/stages/`
- `TODO.md`
- `CLAUDE.md`

然后打开 [`../tutorial/`](../tutorial/) 看一个最小示例。

### 65–80 分钟：Claude Code + Superpowers 接管

使用第一次 handoff prompt，沿着 Current Work Item 讲解：现实验证 → Gate A（条件）→ spec → Gate B → plan/execution → PR/E2E → Gate C。

### 80–90 分钟：Stage 收尾与复盘

讲 Gate D、documentation reconciliation、archive，以及为什么新会话最终只需要“继续当前 Work Item”。

## 练习题

1. “数据库字段名与设计文档不同，但业务语义没变”应该进 Gate A 吗？为什么？
2. “为了兼容真实 API，核心状态机需要增加一个状态”应该谁决定？
3. Plan 写完后是否默认需要人工 review？
4. Gate C 通过前能不能把 Work Item 标记为 Done？
5. 为什么 `docs/coding-guides/` 不应该默认全量加载？

答案都能在本仓库教程中找到。
