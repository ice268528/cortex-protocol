# Repository and Code Organization

本文件仅在跨模块理解代码组织时读取。简单项目如果根 `CLAUDE.md` 已足够说明代码结构，可以删除本文件。

## 1. 系统组成
【填写主要运行组件及关系】
- Web frontend：
- API/backend：
- AI Agent：
- Worker / scheduler：
- Database：
- External services：

## 2. 目录职责
【只记录帮助 Coding Agent 定位代码职责的稳定目录】

- `【目录】`：【职责】
- `【目录】`：【职责】
- `【目录】`：【职责】

## 3. 依赖与边界
【只填写本项目真实且长期有效的模块约束】

- `【模块 A】` → 可以/不可以依赖 `【模块 B】`
- `【边界】`：
- `【边界】`：

## 4. AI Agent 代码组织（如适用）
- context assembly：`【路径】`
- orchestration：`【路径】`
- tools：`【路径】`
- deterministic business logic：`【路径】`
- state persistence：`【路径】`
- prompt/template：`【路径】`

## 5. 常见修改定位
- 新增 API：`【路径】`
- 修改 Domain model：`【路径】`
- 修改 Agent context：`【路径】`
- 新增 Agent tool：`【路径】`
- 修改数据库 schema：`【路径】`
- 新增前端页面：`【路径】`
- 新增 integration test：`【路径】`
- 新增 Playwright E2E：`【路径】`

目录或模块职责长期变化时更新本文件；当前做到哪里始终以 `TODO.md` 为准。
