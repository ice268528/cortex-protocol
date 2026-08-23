# 02. 网页版 ChatGPT：如何做 0→1 项目设计

## 目标

网页版阶段不是“让 AI 一次生成一套漂亮文档”，而是让人真正参与并理解设计，再把已经确认的结论写进 Repository。

## 工作方式：逐文件收敛

```text
选择当前文件
→ ChatGPT 读取目标 + 已 accepted 的上游文档
→ 主动暴露需要人理解/选择/确认的问题
→ 逐项讨论
→ 决策问题清零
→ ChatGPT 明确“当前设计已收敛”
→ 生成最终文档
→ 人确认 accepted
→ 进入下一个文件
```

后续文件把前面 accepted 的文档当作 baseline。

## 为什么不要一次生成全部设计

一次性生成 product + technology + domain + data flow + architecture + stages，看起来效率高，但人容易变成“批量审结果”，没有真正建立自己的系统模型。后面发现冲突时，也很难知道应该回到哪一层修正。

逐文件设计的价值在于：

- 每层决策都能被理解和确认；
- 上下游关系清楚；
- 设计冲突能回溯到真正的源头；
- Repository 最终保存的是 accepted baseline，而不是聊天过程。

## 发现上游设计错误怎么办

例如正在讨论 Data Flow，却发现 Domain Model 的状态定义不成立：

```text
暂停当前 Data Flow
→ 明确指出与已 accepted Domain Model 的冲突
→ 回到 Domain Model
→ 讨论并修正
→ 更新 accepted baseline
→ 再继续 Data Flow
```

不要在下游文件里静默“兼容”错误上游设计。

## 输出文档时的原则

- 只保留已确认的当前结论；
- 被否决方案不作为当前设计继续存在；
- 未确定内容标为假设；
- 不为了“看起来完整”而编造；
- 一个文件没收敛前不提前设计后续文件。

直接使用：[`../prompts/web-design-session.md`](../prompts/web-design-session.md)。
