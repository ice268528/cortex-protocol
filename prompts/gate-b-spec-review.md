# Prompt：Gate B — 要求 Design Review Packet

当 spec 已形成，但你希望 Claude Code 用“系统行为”而不是实现细节帮助你审查时发送：

```text
先进入 Cortex Protocol Gate B，不要开始 implementation plan。

请基于当前已形成的 spec 给我一个 Design Review Packet。目标是让我判断“这个系统设计是不是我要的”，而不是审函数和文件级实现。

只覆盖当前 change 实际相关的内容：
- 业务流程；
- 数据流；
- 状态变化；
- 关键计算逻辑；
- persistence 边界；
- external service interaction；
- 关键失败路径和用户可观察行为。

如果当前功能包含 AI Agent，再说明：
- Agent 收到哪些输入；
- context 如何组装、哪些内容进入 model context；
- 有哪些 tools、如何选择和执行；
- tool result 如何回到 context；
- agent state 如何变化；
- 最终 output 是什么；
- 最终业务 decision ownership 在哪里。

不适用的部分省略，不要为了完整而推测。最后明确列出仍需要我决定的问题。等我明确批准 spec 后再进入 plan。
```
