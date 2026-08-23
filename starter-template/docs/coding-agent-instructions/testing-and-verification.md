# Testing and Verification

本文件只维护本仓库特有的测试地图、命令和验证要求，不解释通用测试概念。

## 1. 测试地图
- Backend unit：`【路径】`
  - 命令：`【命令】`
- Backend integration：`【路径】`
  - 命令：`【命令】`
- Frontend/component：`【路径】`
  - 命令：`【命令】`
- Playwright E2E：`【路径】`
  - 命令：`【命令】`
- Full verification：
  - 命令：`【命令】`

删除项目中不存在的测试类型。

## 2. 项目特定验证要求
【只填写这个仓库特有的规则，例如：】
- 修改数据库 migration 后额外运行：`【命令】`
- 修改 Agent tools 后额外运行：`【命令】`
- 修改 API schema 后额外运行：`【命令】`
- 修改前端关键流程后额外运行：`【命令】`

没有特定规则时删除对应条目。

## 3. 验证原则
- 优先复用已有测试。
- 验证范围与当前 change 的实际影响匹配。
- 只汇报实际执行过的验证；未执行的测试不要推测结果。
- 测试失败若暴露重大设计偏差，进入 Human Gate A。
- user-visible flow 需要 E2E 时，继续读取 `e2e-and-human-acceptance.md`。
