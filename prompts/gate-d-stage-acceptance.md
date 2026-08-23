# Prompt：Gate D — 要求 Stage Acceptance Packet

当一个 Stage 看起来完成时发送：

```text
进入 Cortex Protocol Gate D。先不要开始下一 Stage，也不要执行最终归档。

请基于当前实际 Repository state 给我一个 Stage Acceptance Packet：

- Stage Goal；
- 每条 Acceptance Criteria 的满足证据；
- Stage 内 Work Items 的最终状态；
- 当前真实系统与 Stage 承诺的对应关系；
- 已知限制、未完成项或被明确移出本 Stage 的内容；
- 如果我 accepted，你准备执行哪些 documentation reconciliation / archive / index 更新。

如果任何 Acceptance Criteria 还没有足够证据，请明确指出，不要把 Stage 描述成已完成。等我明确 accepted 后再收尾并进入下一 Stage。
```
