# Prompt：Web ChatGPT — Existing Project Exploration → Proposal

```text
这是已有项目中的探索性讨论，不是 Requirement，也不是 Approved Design。

我们可以先讨论很多轮。
只有我明确说“整理成文件”时，才执行 File Output Contract。

讨论中区分：
- 已知事实
- 我的明确偏好/决定
- 你的建议
- 未验证假设

不要假装你已经验证真实 repo。
不要提前创建 Work Item / Spec / Plan。

# File Output Contract

简单主题：
docs/proposals/<name>.md

复杂主题：
docs/proposals/<name>/
  README.md
  <supporting-topic>.md
  ...

一个文件只回答一个主要问题。

统一头部：

# <Title>

> **Description:** 这个文件回答什么问题。
> **Last Updated:** YYYY-MM-DD

写正文前先给：
Path
Description
Why Needed
Required Headings

## Single-file Proposal

# Proposal — <Title>

> **Description:** 这个候选变化解决什么问题，以及本文覆盖什么范围。
> **Last Updated:** YYYY-MM-DD

## Problem / Opportunity
## Desired User Capability
## Motivation / Evidence
## Proposed Behavior
## Candidate Design
## Alternatives Considered
## Assumptions
## Risks / Dependencies
## Open Questions
## Explicit Non-Goals
## Must Validate Against Real Repository
## What Should NOT Be Decided Yet

## Proposal Package README

README 最后生成。

至少包含：
## Overview
## Desired User Capability
## File Index
## Cross-Cutting Assumptions
## Risks / Dependencies
## Open Questions
## Explicit Non-Goals
## Must Validate Against Real Repository

README 只做 overview / navigation，不复制 supporting files 全文。

最终这些文件只是 Proposal input。
Coding Agent 仍需 Review，之后由 Human 在 Gate R 确认 disposition。
```
