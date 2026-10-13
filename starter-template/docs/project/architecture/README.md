# Architecture

> **Description:** 保存跨多个 Work Item 仍有价值的长期 architecture knowledge；不是完整技术 reference。
> **Last Updated:** YYYY-MM-DD

## Status convention

```text
Verified Current
Approved Baseline
UNDECIDED
```

- Verified Current：真实实现已经如此。
- Approved Baseline：Human 明确批准的长期 foundation。
- UNDECIDED：当前不需要决定；附 Decision Trigger。

## Optional topics

| Future file | Answers | Starter template |
|---|---|---|
| `system-overview.md` | major components / responsibilities / boundaries | [`system-overview.template.md`](../../../templates/system-overview.template.md) |
| `project-structure.md` | repo/module ownership / dependency direction | [`project-structure.template.md`](../../../templates/project-structure.template.md) |
| `domain-and-state.md` | core domain/state/invariants | [`domain-and-state.template.md`](../../../templates/domain-and-state.template.md) |
| `data-flow.md` | critical flow/source-of-truth/side-effects | [`data-flow.template.md`](../../../templates/data-flow.template.md) |
| `interfaces-and-contracts.md` | long-lived API/event/schema contracts | [`interfaces-and-contracts.template.md`](../../../templates/interfaces-and-contracts.template.md) |
| `persistence-and-data.md` | data ownership/consistency/migration/retention | [`persistence-and-data.template.md`](../../../templates/persistence-and-data.template.md) |
| `runtime-and-deployment.md` | runtime/process/deployment topology | [`runtime-and-deployment.template.md`](../../../templates/runtime-and-deployment.template.md) |

全部可选。需要一个未归入上述主题的 architecture 文档时，可从通用 [`architecture-document.template.md`](../../../templates/architecture-document.template.md) 开始。

不要放：
- full OpenAPI endpoint reference
- full DB DDL
- every feature implementation note
- Proposal
- current Work Item Plan
- coding-agent instruction
