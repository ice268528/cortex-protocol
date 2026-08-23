# Prompt：Gate C — 要求 Feature Acceptance Packet

当 Agent 说实现完成，但你需要一份可执行的人工验收说明时发送：

```text
进入 Cortex Protocol Gate C。先不要把 Current Work Item 标记为 Done。

请给我一个 Feature Acceptance Packet，只汇报你实际完成和实际验证过的内容：

1. 当前 Work Item 和 PR/branch；
2. 本次实际完成的用户/系统能力；
3. 已实际执行并通过的 unit / integration / CI / review / E2E；
4. 需要我手动验收的场景；
5. 每个场景的前置条件、操作步骤、预期结果；
6. 当前仍无法自动验证或需要我特别观察的内容；
7. 为人工验收需要保持运行的服务和访问入口。

不要把没有运行过的验证写成已通过。等我明确 accepted 后，再执行 Work Item Done 和后续 reconciliation。
```
