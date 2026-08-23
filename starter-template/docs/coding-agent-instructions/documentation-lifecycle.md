# Documentation Lifecycle

本文件定义工程事实如何回写长期文档，以及 Stage accepted 后如何归档。

## 1. 回写原则
实现结果形成长期有效的新事实时，只更新确实受到影响的当前文档：
- 长期项目设计变化 → `docs/project/`
- Stage、Work Item 或 Acceptance Criteria 变化 → `docs/stages/`
- 项目级 Work Item 状态/拆分变化 → `TODO.md`
- 当前 change 设计变化 → 当前 Superpowers spec/plan

重大变化先经过 Human Gate A。
不要为了“保持一致”无关地重写未受影响文档。

## 2. 当前状态与历史记录
`docs/project/` 应反映当前长期设计。
Superpowers spec/plan 是具体 change 的设计与实施记录，不应要求后续 Agent 阅读全部历史 spec 才能理解当前系统。

Work Item 完成后，不把整个 spec/plan 机械复制进项目文档；只沉淀仍然有效的长期事实。

## 3. Work Item 完成
Human Gate C 通过后：
- 更新 `TODO.md`；
- 检查是否有需要长期保留的项目设计变化；
- 只同步确实受影响的文档。

## 4. Stage Acceptance 与 Archive
Stage 满足条件后进入 Human Gate D。
用户明确 `accepted` 后：
1. reconcile 当前有效文档与实际实现；
2. 判断哪些 Stage-scoped 文档已经过时；
3. 使用 `git mv` 移动到对应 `_archive/stage_XX/`；
4. 更新相关 `README.md` / index；
5. archived 文档作为历史记录，不再作为当前设计编辑。

不要机械归档仍然代表当前真相的长期项目文档。
