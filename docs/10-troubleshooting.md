# 10. Troubleshooting

## 1. Proposal Review 后 Agent 自动归档 DEFER / REJECT

**错误。**

v2 中 Recommendation 不等于 decision。

必须 Gate R，让 Human 确认这个判断。

---

## 2. 只有 START_NOW 才 Gate R

**错误。**

ABSORB / DEFER / BLOCK / REJECT 同样需要 Gate R。

因为 Human 不只是决定“做不做”，还需要确认 Agent 对产品优先级、重复关系、blocker 的判断。

---

## 3. Gate A 在主流程里像消失了

Gate A 本来就不是 happy-path stage。

它应该画成：

```text
任何受影响阶段
-. approved design must change .-> A
```

---

## 4. 每个 bug 都建 Work Item

如果正确行为已明确、低风险、小范围，优先 Direct Change。

---

## 5. 为了省流程，把复杂 change 也叫 Direct Change

如果需要：

- 新 capability；
- approved semantics 改动；
- contract/state/security/persistence 变化；
- 多 design fork；
- independent acceptance；

就必须升级。

---

## 6. `roadmap.md` 又变成 task backlog

Roadmap 表达 Milestone / capability / DoD。

Implementation Task 只在 Plan。

---

## 7. Architecture 变成完整 API / DB reference

只保留长期 architecture 层：

```text
ownership
boundary
invariant
compatibility
consistency
lifecycle
```

Exact schema 留给机器可读 source。

---

## 8. Web ChatGPT 一次生成所有未来设计

新项目默认只需要：

```text
product
roadmap
project-state
+ necessary stable architecture baseline
```

Optional infrastructure 保持 UNDECIDED。

---

## 9. Gate C 测试绿了就自动 accepted

错误。

Gate C 是 Human 真实功能验收。

---

## 10. 最后一个 Work Item Done 就自动 Milestone Done

错误。

必须回到 Milestone User Capability + AC / DoD，经 Gate D。
