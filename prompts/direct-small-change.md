# Prompt：明确的小改（可选快捷版）

```text
这是一个我认为边界明确的小改：

<描述>

请先验证它是否满足 Direct Change：

- 不新增 capability；
- 不改变 approved semantics / public contract / state / security / persistence / long-lived architecture；
- blast radius 小；
- 无重大 design fork。

满足则：
inspect → change → targeted verification → review → report。

不要创建 Work Item / TODO / Spec / Plan / Gate B / Gate C。

如果不满足，不要为了省流程硬做；进入 Gate A / Work Item / Proposal + Gate R 中最小正确路径。
```
