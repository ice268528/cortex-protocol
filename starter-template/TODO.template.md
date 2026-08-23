# TODO

> 本文件只跟踪项目级 Work Item，不记录 Superpowers implementation plan 内部任务。
> 默认一次只推进一个 Current Work Item；如确需并行，必须明确区分不同 branch/worktree。

## Current Work Item
- [ ] `【WORK-ITEM-ID】` 【标题】
  - Stage：`docs/stages/【stage 文件】`
  - 目标：【一句话描述该 Work Item 完成后新增/改变的能力】
  - Branch：`【branch】`
  - Spec：`【如已生成，填写 docs/superpowers/specs/...；否则留空】`
  - PR：`【如已创建，填写 PR；否则留空】`
  - 状态：`ready | in_progress | awaiting_spec_review | awaiting_human_acceptance | blocked`

## Next
- [ ] `【WORK-ITEM-ID】` 【标题】
- [ ] `【WORK-ITEM-ID】` 【标题】

## Blocked
- [ ] `【WORK-ITEM-ID】` 【标题】
  - 原因：【阻塞原因】
  - 等待：【需要谁/什么解除阻塞】

## Done
- [x] `【WORK-ITEM-ID】` 【标题】 — 【完成日期或 PR，可选】

## 维护规则
- Work Item 粒度应足以独立形成一次 change，并可独立验证。
- 文件级、函数级、测试步骤等 implementation tasks 不写入这里。
- Human Gate C 通过前，不把 Current Work Item 标记为 Done。
- Stage 是否 accepted 以对应 Stage 文档和 Human Gate D 为准，不在这里替代 Stage 验收。
- Work Item 拆分、合并、重排或跨 Stage 调整时，同步更新对应 `docs/stages/`。
