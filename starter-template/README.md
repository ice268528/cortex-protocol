# Cortex Protocol v2 — Starter Template

这个目录是放进真实 Repository 的文本脚手架。这里只保留项目运行需要的模板、入口 README 和两个真正按需加载的 Coding Agent instruction。

## 安装

1. [`CLAUDE.template.md`](CLAUDE.template.md) → Repository 根 `CLAUDE.md`
2. [`TODO.template.md`](TODO.template.md) → Repository 根 `TODO.md`
3. 新项目用 Web ChatGPT 生成：
   - `docs/project/product.md`
   - `docs/project/roadmap.md`
   - `docs/project/project-state.md`
4. `docs/project/architecture/` 只按需创建 topic
5. 保留 Proposal Inbox、Superpowers artifacts 和两个按需 Coding Agent instruction

推荐结构：

```text
CLAUDE.md
TODO.md

docs/
├── project/
│   ├── README.md
│   └── architecture/
│       └── README.md
├── proposals/
│   ├── README.md
│   ├── _TEMPLATE.md
│   ├── _PACKAGE_TEMPLATE/
│   └── _archive/
├── superpowers/
│   ├── specs/
│   └── plans/
├── coding-agent-instructions/
│   ├── verification-and-acceptance.md
│   └── documentation-lifecycle.md
└── coding-guides/
```

正式 taxonomy：

```text
Milestone → Work Item → Task
```

没有 `docs/stages/`。

---

## 资产导航

### Repository 根模板

| 文件 | 用途 |
|---|---|
| [`CLAUDE.template.md`](CLAUDE.template.md) | 每个 Coding Agent session 都不能漏的 standing operating rules |
| [`TODO.template.md`](TODO.template.md) | 正式 Work Item 的 live queue/state；Direct Change 与 Plan Task 不进入 |

### Project docs

- [`docs/project/README.md`](docs/project/README.md) — Product / Roadmap / Project State / Architecture 的职责入口
- [`templates/product.template.md`](templates/product.template.md) — `product.md` 结构
- [`templates/roadmap.template.md`](templates/roadmap.template.md) — `roadmap.md` 结构
- [`templates/project-state.template.md`](templates/project-state.template.md) — Human-readable checkpoint snapshot 结构
- [`docs/project/architecture/README.md`](docs/project/architecture/README.md) — Architecture topic 选择与对应模板

### Proposal Inbox

- [`docs/proposals/README.md`](docs/proposals/README.md) — Proposal lifecycle、single-file/package/archive 入口

### Work Item artifacts

- [`docs/superpowers/specs/README.md`](docs/superpowers/specs/README.md) — 正式 Work Item Spec 的存放边界
- [`docs/superpowers/plans/README.md`](docs/superpowers/plans/README.md) — 正式 Work Item Plan / Task decomposition 的存放边界

### Coding Agent on-demand instructions

- [`docs/coding-agent-instructions/verification-and-acceptance.md`](docs/coding-agent-instructions/verification-and-acceptance.md) — impact-based verification、Playwright/E2E 复用与沉淀、Gate C readiness/failure routing
- [`docs/coding-agent-instructions/documentation-lifecycle.md`](docs/coding-agent-instructions/documentation-lifecycle.md) — durable fact → owner matrix、Gate R/A/B/C/D Post-decision sync、project-state checkpoint policy

### Coding guides

- [`docs/coding-guides/README.md`](docs/coding-guides/README.md) — 项目以后如何放置“已验证但只应按需加载”的技术 guide

---

## CLAUDE 与按需 instruction 的边界

`CLAUDE.md` 是 Coding Agent 的 standing operating constitution，必须让不同模型只读它也能一致理解：
- cold start / canonical state；
- Direct Change vs Work Item；
- Gate R / A / B / C / D；
- Git branch / commit / PR / history safety；
- runtime/service safety；
- security / contract constraints；
- completion boundary。

`docs/coding-agent-instructions/` 只保留“进入特定阶段后才需要、且无法用少量 standing rule 表达”的详细操作手册。

不要为了“conditional”就继续拆 instruction。只有当不读某个文件会让 Agent 在特定类型工作中系统性做错，而且详细规则不适合常驻 CLAUDE 时，才新增 instruction。

## Right-sized delivery

```text
Direct Change
= small + clear + low risk
= no forced Work Item / Spec / Plan / Gate B / Gate C

Work Item
= needs design + durable coordination + independent acceptance
= Spec + Gate B + Plan + Gate C
```

## Proposal

Proposal Review schema 保存在 Proposal template；Gate R standing behavior 保存在 `CLAUDE.md`。Coding Agent recommendation 必须经过 Human Gate R confirmation。

## 旧项目

不要直接覆盖现有 `CLAUDE.md`。先把 repo-local high-value constraints 分类迁移：

```text
every-session critical → CLAUDE.md
rare + detailed conditional behavior → coding-agent-instructions/
long-lived architecture truth → docs/project/architecture/
machine-readable facts → code/schema/config/tests/CI
```
