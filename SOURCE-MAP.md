# Source Map

Cortex Protocol 来自本项目整理时提供的三类原始材料：

1. 网页版 ChatGPT 与 Coding Agent 协作开发的心智模型；
2. Human-side workflow；
3. Claude Code workflow starter template。

## 原始思想 → 当前结构

| 原始主题 | Cortex Protocol 中的位置 |
|---|---|
| 0→1 逐文件设计 | `WHY.md`, `docs/02-web-chatgpt-design.md`, `prompts/web-design-session.md` |
| Repository 作为长期状态 | `WHY.md`, `docs/03-repository-as-memory.md`, `PROTOCOL.md` |
| 第一次 handoff / 后续 resume | `docs/04-handoff-and-cold-start.md`, `prompts/` |
| Superpowers 职责去重 | `docs/05-superpowers-work-item-loop.md`, `PROTOCOL.md` |
| Gate A/B/C/D | `docs/06-human-gates.md`, `checklists/`, `prompts/gate-*.md` |
| PR / E2E / Stage closeout | `docs/07-pr-e2e-and-closeout.md` |
| coding-guides 按需读取 | `docs/08-coding-guides-and-context.md` |
| Human 只保留高价值判断 | `WHY.md`, `docs/01-mental-model.md`, `PROTOCOL.md` |
| Claude Code standing policy | `starter-template/CLAUDE.template.md` + `starter-template/docs/coding-agent-instructions/` |

## V2 Onboarding Layer

V2 新增的 `WHY.md`、`GLOSSARY.md` 和 `tutorial/` 是**教学与 onboarding 层**：它们不改变 Protocol 内核，而是把原始思想按“问题 → 推导 → 心智模型 → 跟做一次 → 自己采用”的顺序重新组织，让第一次接触的人更容易理解并执行。

`PROTOCOL.md` 仍是精确定义层；`starter-template/` 仍是项目落地层。
