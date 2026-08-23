# Prompt：Gate A 时要求 Agent 给出完整决策材料

当 Agent 说设计与工程现实冲突，但说明不够清楚时，可以发送：

```text
先不要继续实现。请按 Gate A 给我一个 Design Divergence Review：

- 原来的设计是什么；
- 实际工程证据是什么；
- 为什么冲突；
- 你建议怎么改以及理由；
- 有哪些可行 alternatives；
- 会影响哪些 project docs、stages、TODO；
- 当前 Superpowers spec/plan 是否仍有效。

只陈述你已经验证过的工程事实；把推断明确标出来。等我决定后再继续。
```
