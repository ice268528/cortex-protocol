# Work Item and Stage Lifecycle

本文件只定义项目级 Work Item / Stage 生命周期，不重复 Superpowers 的内部工程流程。

## 1. Work Item
- `TODO.md` 是项目级 Work Item 状态源。
- 一个 Work Item 对应一个相对独立、可验证的 change。
- Superpowers plan 内部任务不回写 `TODO.md`。
- 当前 Work Item 未完成前，不主动推进无关 Work Item。

## 2. 设计偏差
调研、spec、planning 或 implementation 中发现已批准设计需要实质性调整时：
1. 停止受影响部分。
2. 进入 Human Gate A。
3. 用户确认后，只修改确实受影响的 `docs/project/`、`docs/stages/`、`TODO.md` 和当前 spec/plan。
4. 判断当前 spec/plan 是否仍有效；需要时回到对应设计阶段重新收敛。

不要为了遵守旧文档而实现已知错误设计，也不要静默修改重大设计后继续开发。

## 3. Work Item 完成
Human Gate C 通过后：
- 将 Current Work Item 标记为 Done；
- 同步必要的长期文档变化；
- 若 Stage 未完成，选择下一 Work Item；
- 若 Stage 看起来已满足全部 Acceptance Criteria，进入 Human Gate D。

## 4. Stage 完成
用户明确 accepted 后：
- 执行必要的文档 reconciliation；
- 按 `documentation-lifecycle.md` 归档过时 Stage 文档；
- 更新相关 README/index；
- 再进入下一 Stage。
