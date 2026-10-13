# START HERE — 从 v2 文本脚手架开始

## Step 1 — 复制 [`starter-template/`](starter-template/README.md)

得到：

```text
CLAUDE.md
TODO.md

docs/
├── project/
├── proposals/
├── superpowers/
├── coding-agent-instructions/
└── coding-guides/
```

处理：

```text
CLAUDE.template.md → CLAUDE.md
TODO.template.md   → TODO.md
```

旧项目不要直接覆盖已有 `CLAUDE.md`，先迁移仍有效的 repo-local 约束。

复制前可先看 [`starter-template/README.md`](starter-template/README.md)，了解每个模板、按需 instruction 和 Proposal/Architecture 子目录分别负责什么。

---

## Step 2 — 新项目先和 Web ChatGPT 讨论

复制：

[`prompts/chatgpt-project-bootstrap.md`](prompts/chatgpt-project-bootstrap.md)

可以聊很多轮，不要第一轮就要求生成全部文件。

收敛：

```text
Target User / Problem
Core Experience
Product Principles
M1 User Capability
M1 Definition of Done / Acceptance Criteria
Constraints / Non-Goals
Explicitly Not Now
```

---

## Step 3 — 明确要求 ChatGPT 整理成项目文档

说：

> **“现在按 File Output Contract 整理成项目需求文档。”**

默认生成：

```text
docs/project/product.md
docs/project/roadmap.md
docs/project/project-state.md
```

Architecture 只按需生成。

不要为了模板完整创建全部 architecture files。

---

## Step 4 — 把文件放回 Repository

填好根 `CLAUDE.md`：

- project identity；
- critical boundaries；
- minimal code map；
- run/verify commands；
- Git/runtime/artifact rules；
- project-specific non-negotiables。

---

## Step 5 — 第一次交给 Coding Agent

使用：

[`prompts/first-handoff-to-claude-code.md`](prompts/first-handoff-to-claude-code.md)

Coding Agent：

```text
Cold Start
→ Bootstrap Review
→ real repo check
→ 识别第一个真正需要正式设计的 Work Item
→ Investigation
→ Spec
→ Gate B
```

小 starter/config/docs 修正若符合 Direct Change，可直接修。

---

## Step 6 — Gate B 后

```text
Plan
→ Implementation
→ Tests
→ Review
→ Gate C
```

中途任何位置如果发现 approved design / Milestone / accepted Spec 必须改变：

```text
→ Gate A
```

---

## Step 7 — 项目日常的三种其他情况

### Existing Project + New Feature

Web ChatGPT → Proposal → Coding Agent Review → **Gate R**。

无论 Agent 建议现在做、以后做、已覆盖、阻塞还是不做，都必须让 Human 确认判断。

### Mid-flight Idea

直接告诉 Coding Agent。

它判断：

```text
plan-local
Direct Change
new Work Item
Gate A
Proposal → Gate R
```

### Bug / UI Small Change / Real-use Feedback

直接描述：

```text
Actual:
Expected / Desired:
Context:
```

Coding Agent 优先判断 Direct Change。

---

完整教程：

[`tutorial/README.md`](tutorial/README.md)
