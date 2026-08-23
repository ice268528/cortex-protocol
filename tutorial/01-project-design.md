# 01 — 用 Web ChatGPT 逐文件完成 Project Design

## Step 1：先使用固定设计协议

打开网页版 ChatGPT，复制 [`../prompts/web-design-session.md`](../prompts/web-design-session.md)。

然后告诉它：

```text
我们先设计第一个文件：产品定位与边界。
当前产品想法：做一个内部 Feedback Inbox，让用户提交反馈，团队可以查看、分类并处理。
```

ChatGPT 不应该马上生成完整项目文档，而应该暴露需要你理解/选择的问题，例如：

- 谁能提交反馈？
- 谁能查看全部反馈？
- “分类”是人工还是自动？
- 处理状态有哪些？
- 是否需要匿名？
- 是否需要通知？

## YOUR JOB RIGHT NOW

```text
✓ 对产品行为做选择
✓ 对不理解的问题继续追问
✓ 要求重要假设明确化
✓ 问题清零后才接受当前文件
```

## 示例 accepted 结论

本 Tutorial 假设最终确认：

- 公司内部已登录用户可提交反馈；
- Support 团队可查看全部反馈；
- v1 分类由 Support 人工选择；
- 反馈状态为 `new / triaged / resolved`；
- v1 不支持匿名提交；
- v1 不做邮件通知。

示例产物：[`final-state/docs/project/00-product.md`](final-state/docs/project/00-product.md)。

## Step 2：继续 Domain / State

让前一个 accepted 文件成为 baseline，再讨论 Domain：

```text
现在进入下一个文件：Domain 与 State Model。
把已经 accepted 的产品设计作为上游 baseline。
```

这里重点确认：

- Feedback 是什么实体；
- category 是否允许为空；
- 状态如何迁移；
- 谁拥有 triage / resolve 权限。

示例产物：[`final-state/docs/project/01-domain-and-state.md`](final-state/docs/project/01-domain-and-state.md)。

## Step 3：Data Flow

再讨论提交和处理流程的数据流。

示例产物：[`final-state/docs/project/02-data-flow.md`](final-state/docs/project/02-data-flow.md)。

## 如果下游发现上游错了

比如讨论 Data Flow 时发现：`resolved` 之后实际上需要支持 reopen。

不要在 Data Flow 里偷偷补一个 `reopened`。

正确做法：

```text
暂停 Data Flow
→ 回到 Domain / State Model
→ Human 讨论并批准状态变化
→ 更新 accepted baseline
→ 再继续 Data Flow
```

这就是 project-design 阶段的 design divergence 思维。

## DON'T DO THIS

```text
✗ 一次性让 AI 输出 product + domain + data flow + architecture + stages
✗ 把被否决方案继续留在 current design 里
✗ 为了文档“看起来完整”而编造未知内容
```

下一步：[`02-stage-and-work-item.md`](02-stage-and-work-item.md)。
