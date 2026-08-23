# 07. PR、Review、Playwright 与收尾

## 1. 正常 feature 默认走 PR

推荐 standing policy：

```text
独立 branch/worktree
→ 完成当前 Work Item
→ 必要验证
→ push
→ create PR
→ CI
```

除非人明确要求，不默认直接 merge base branch。

## 2. 不要因为“创建了 PR”就机械重复 review

如果 PR HEAD 就是刚刚完成干净 whole-change review 的 HEAD，可以复用该 review 结论。只有 HEAD、实现或 review 前提变化时，再做新的 review。

## 3. Playwright 是 regression asset，不是一次性验收脚本

用户可见流程需要 E2E 时：

```text
先查已有 Playwright
→ 已覆盖：复用
→ 行为变化：修改已有 test
→ 新行为且有长期回归价值：新增 test
→ 提交到 repo
```

不要为了“流程完整”强行创建没有长期价值的 E2E。

## 4. Gate C 失败后的 loop

```text
人工验收失败
→ 修复
→ 重跑受影响验证
→ 必要时更新 E2E
→ 必要时 re-review
→ 再次 Gate C
```

## 5. Stage accepted 后

Agent 主动：

1. reconcile 当前有效文档与实际实现；
2. 识别过时的 Stage-scoped 文档；
3. 用 `git mv` 归档到 `_archive/stage_XX/`；
4. 更新 README/index；
5. 进入 next stage。

长期仍代表 current truth 的 `docs/project/` 不应机械归档。
