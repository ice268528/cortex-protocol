# Cortex Protocol Glossary

这不是完整术语词典，只解释第一次使用 Cortex Protocol 最容易混淆的词。

| 术语 | Plain-language 解释 |
|---|---|
| **Project-level design** | 系统长期应该是什么样：产品边界、Domain、Data Flow、Architecture 等。 |
| **Stage** | 一段有明确目标和验收标准的开发阶段；比 Work Item 大，比整个项目小。 |
| **Work Item** | 一个可以相对独立完成并验证的项目级能力变化。不是“修改某个文件”。 |
| **Current Work Item** | Coding Agent 当前唯一应该主要推进的项目级 change。 |
| **Spec** | 这次 Work Item 在当前系统里应该“怎么工作”，属于 change-level design。 |
| **Plan** | Coding Agent / Superpowers 准备“怎么实现”：文件、测试、步骤等。默认不需要 Human review。 |
| **Gate** | Agent 必须暂停，把某类判断权交回 Human 的节点。 |
| **Gate A** | 真实工程证据可能推翻重要已批准设计时的决策 Gate。 |
| **Gate B** | Spec 收敛后，Human 审“系统行为是不是我要的”。 |
| **Gate C** | 实现与验证完成后，Human 验“真实功能是不是我要的”。 |
| **Gate D** | Stage 看起来完成时，Human 验“阶段承诺是否完整交付”。 |
| **Current truth** | 当前仍然有效、应该指导后续工作的长期事实；不是历史聊天记录。 |
| **Repository state** | 让新 session 能恢复项目当前位置的持久状态：docs、TODO、代码、tests、git 等。 |
| **Reconcile** | 设计或实现变化后，把受影响文档、TODO、spec/plan 与当前实际系统重新对齐。 |
| **Housekeeping** | TODO 更新、文档同步、review 调度、服务清理、归档等可由规则驱动的流程维护工作。 |
| **Cold start** | 新 Claude Code session 从 Repository 恢复当前状态并验证工程现实的启动过程。 |
| **Standing policy** | 持续有效的项目级 Agent 规则，通常放在 `CLAUDE.md` 或按需 instruction 文件中。 |
