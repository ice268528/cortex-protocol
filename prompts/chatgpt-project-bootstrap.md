# Prompt：Web ChatGPT — New Project Bootstrap

```text
这是一个全新项目。

第一阶段不要急于生成文件。先和我把产品需求讨论清楚，可以持续很多轮。

优先讨论：
1. Target User / Problem
2. Core Experience
3. Product Principles
4. Initial Product Wedge
5. M1 User Capability
6. M1 Definition of Done / Acceptance Criteria
7. Constraints / Non-Goals
8. Explicitly Not Now
9. 真正必须提前确定的 stable technical boundaries

不要为了“完整”提前决定 database / queue / cache / provider / framework。

只有当我明确说：
“整理成文件”
“生成项目需求文档”
“按 File Output Contract 输出”
时，才开始写最终文件。

# File Output Contract

## 默认核心文件

### docs/project/product.md

# Product

> **Description:** 说明产品为谁解决什么问题、最终体验和长期产品原则；它是 authoritative product intent。
> **Last Updated:** YYYY-MM-DD

## North Star
## Target User / Problem
## Core Experience
## Product Principles
## Initial Product Wedge
## Non-Goals

### docs/project/roadmap.md

# Capability Roadmap

> **Description:** 按用户能力定义 Milestone 顺序、当前 Milestone 的 DoD / Acceptance Criteria 和状态。
> **Last Updated:** YYYY-MM-DD

## M1 — <Name>
### User Capability
### Why Now
### Definition of Done / Acceptance Criteria
### Scope
### Non-Goals
### Candidate Work Items
### Status

## Later Milestones

Milestone 是 capability atomic unit。
不要把 implementation Task 写进 Roadmap。

### docs/project/project-state.md

# Project State

> **Description:** 让 Human 快速了解项目最近一次可信 checkpoint：已经完成到哪个 Milestone / Work Item、当前正在做什么、相关 PR、下一步与持续 blocker；同时为新的 Coding Agent session 提供恢复坐标。
> **Last Updated:** YYYY-MM-DD

> 这是 checkpoint snapshot，不是实时 event log。

## Current Snapshot
- Current Milestone:
- Current Work Item:
- Status:
- Active PR:

## Completed Through
- Latest Accepted Milestone:
- Latest Accepted Work Item:
- Latest Integrated PR:

## In Progress
- Work Item:
- Goal:
- PR:
- Current State:
- Since:

## Next
1.

## Blockers / Decisions Needed
- none

## Recent Checkpoints
- YYYY-MM-DD — ...

## Explicitly Not Now

## Navigation
- Product:
- Roadmap:
- TODO:
- Current Spec:
- Current Plan:

初始 Current Work Item / Active PR 可以是 none。
新项目刚生成时 `Latest Accepted Milestone / Work Item / Integrated PR` 也可以是 none。
Coding Agent Bootstrap Review 后负责在真正形成 Work Item/PR/Milestone checkpoint 时维护本文件；不要把每个 Gate/commit/task 都写进来。

# Architecture：按需创建

可选 topic：

system-overview.md
project-structure.md
domain-and-state.md
data-flow.md
interfaces-and-contracts.md
persistence-and-data.md
runtime-and-deployment.md

创建前问：
“如果现在不写，新 Coding Agent 会不会反复误解一个已经明确的长期边界？”

如果 No，不创建。

Architecture file 使用：

# <Title>

> **Description:** ...
> **Last Updated:** YYYY-MM-DD
> **Status:** Approved Baseline | UNDECIDED

全新空项目不要声称 Verified Current，除非已有真实实现。

Optional infrastructure：
Status: UNDECIDED
Decision Trigger: <何时真正需要决定>

# README

如果 docs/project 已有多个文档，最后生成 README。
README 只做 File Index / Reading Order / Navigation，不复制正文。

# 输出顺序

正式写文件前先给 File Plan：

Path
Description
Why Needed
Required Headings
Status

不要为了模板完整创建空文件。
```
