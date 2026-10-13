# 02. Web ChatGPT：从长期讨论沉淀成项目文件

Web ChatGPT 有两个主要角色：

1. 全新项目的 Project Bootstrap；
2. 已有项目的新 capability / direction Exploration。

共同原则：

> **先讨论，后沉淀；文件保存收敛后的 durable conclusions，不保存聊天流水账。**

---

## 1. File Output Contract

给 Web ChatGPT 的 Prompt 应提前说明最终文件契约：

- Path
- Description
- Required Headings
- `Last Updated`
- 什么情况下生成
- 多文件时 README 怎么写

推荐统一头部：

```md
# <Title>

> **Description:** 用 1–2 句话说明这个文件回答什么问题。
> **Last Updated:** YYYY-MM-DD
```

规则：

- Description 描述稳定职责，不描述聊天过程；
- 实质内容改变时更新 Last Updated；
- 只有职责改变才改 Description；
- 纯格式化不刷新日期。

---

## 2. 新项目

Human 可以和 ChatGPT 聊很多轮：

```text
Target User / Problem
Core Experience
Product Principles
M1 User Capability
M1 Definition of Done / AC
Constraints / Non-Goals
Explicitly Not Now
```

只有 Human 明确说：

> “整理成文件”

才生成。

默认核心文件：

```text
docs/project/product.md
docs/project/roadmap.md
docs/project/project-state.md
```

Architecture 只按需创建。

不要为了模板完整把 database、queue、cache、API、deployment 一次性全部决定。

---

## 3. 已有项目的新功能 / 新方向

讨论收敛后形成 Proposal。

简单：

```text
docs/proposals/<name>.md
```

复杂：

```text
docs/proposals/<name>/
├── README.md
├── product-behavior.md
├── architecture-options.md
└── ...
```

多文件时：

1. 先决定真实需要哪些文件；
2. 先写 supporting files；
3. README 最后生成；
4. README 只做 overview / navigation / cross-cutting open questions；
5. 不复制 supporting files 的完整正文。

Proposal 不是 Requirement，也不是 Approved Design。

下一步必须由 Coding Agent 对真实 repo 做 Review，然后进入 Gate R。

---

## 4. 为什么不让 Web ChatGPT 直接决定是否做

Web ChatGPT 通常不知道：

- 真实 repo 已经实现什么；
- 当前 Milestone 实际 commitment；
- 真实依赖版本；
- architecture constraints；
- 现有 Work Item 是否已覆盖。

因此：

```text
ChatGPT
= 扩大、整理 design space

Coding Agent
= 用真实 repo evidence 收敛

Human
= 在 Gate R 确认最终 disposition
```
