# 14. CLAUDE.md 应保留什么？

根 CLAUDE.md 保存每个 session 不能漏的高价值规则。

## 应该常驻

- project identity / critical boundaries；
- minimal code map；
- cold start；
- right-sized delivery；
- Gate R / A / B / C / D 的短版；
- quick run / verify；
- Git/service/artifact safety；
- secrets / frozen contract / forbidden layer bypass。

## 不应该常驻全文

- 完整 architecture 说明；
- 全量 test path；
- repository path encyclopedia；
- Superpowers 内部步骤；
- 完整 Proposal Review checklist。

## 分流

```text
every-session critical
→ CLAUDE.md

conditional Agent behavior
→ coding-agent-instructions/

long-lived architecture truth
→ docs/project/architecture/

machine-readable details
→ source/schema/config/tests/CI
```


## 什么时候更新 CLAUDE.md

`CLAUDE.md` 由 Coding Agent 维护，但只在 **every-session standing fact** 真正改变时更新，而不是跟随每个 Work Item/Gate 机械变化。

典型 owner facts：

- project identity / critical boundary；
- minimal code map；
- stable Start / Fast verification / Full verification command；
- repository-wide Git/runtime/safety/contract rule。

Gate A accepted 如果改变上述 standing boundary，应同步 CLAUDE；Gate C/D closeout 如果真实实现最终改变 code map / stable commands，也应同步。

不要把以下内容塞进 CLAUDE：

- 仍未实现的 Work Item future design；
- 当前 Plan Task；
- 临时 blocker；
- 只属于单个 feature 的 implementation detail。

## v2 必须常驻的两个新规则

### Gate R

Proposal Review recommendation 不能自动成为 disposition。

### Right-sized Delivery

```text
small + clear + low risk
→ Direct Change

needs design / acceptance
→ Work Item
```
