# CLAUDE.md
> 本文件保存每个 Coding Agent session 不能漏的 standing rules。Cortex v2 使用 `Milestone → Work Item → Task`；所有关键产品/设计判断由 Human Gate 保留最终决定权。Prompt 只是 Human 的快捷指令/纠偏工具，不是理解本协议的必要依赖。

## 1. 项目与状态
- Product：`【一句话说明系统】`；Core users / flow：`【2–4 行】`；Critical boundaries：`【最重要的系统/数据/AI/API 边界】`。
- Minimal code map：`【frontend】`、`【backend】`、`【shared/packages】`；详细长期架构见 `docs/project/architecture/README.md`。
- `docs/project/product.md`：product intent；`roadmap.md`：Milestone / capability / DoD / AC；`project-state.md`：Human-readable latest trusted checkpoint（完成到哪里、当前 Work Item/PR、Next、durable blocker），同时供 Agent 恢复坐标。
- `docs/project/architecture/`：long-lived architecture truth / approved baseline；`docs/proposals/`：candidate capability/direction。
- `TODO.md`：只跟踪 Work Item；`docs/superpowers/specs/` / `plans/`：只属于正式 Work Item；真实 code/tests/schema/config/Git 优先于过时文档。
- Project commands：Start `【命令】`；Fast verification `【命令】`；Full verification `【命令】`。这些是稳定运行入口，发生变化时更新本文件；不要为了命令变化把 project-state 变成运行手册。

## 2. Cold start
1. **Workspace state**：检查 branch/worktree 和 `git status`，确认当前开发上下文、已有修改及 ownership，避免覆盖或提交来源不明的工作。
2. **Project snapshot**：读取 `docs/project/project-state.md`，先理解最近一次可信 checkpoint：已完成 Milestone/Work Item、当前 Work Item/PR、Next 与 durable blocker；它不是实时 truth，随后必须用 TODO/Git/PR/code 验证 `Last Updated` 之后是否有变化。
3. **Live execution state**：读取 `TODO.md`，确认比 project-state 更细、更实时的 Current Work Item / Gate / Next / Blocker；读取 `roadmap.md` 中的 Current Milestone，确认当前承诺的 User Capability、scope 和 DoD/Acceptance Criteria。
4. **Current change**：有 active Work Item 时读取 current Spec，确认已批准的行为/语义；读取 current Plan，确认当前 implementation path；只读取与本 Work Item 有关的 architecture，确认长期 boundary/invariant。
5. **Engineering reality**：检查相关 code/tests/config 和实际 dependency versions，用真实 Repository 验证文档假设是否仍成立。
6. **Context discipline**：无 active Work Item 或只是 Direct Change 时只加载完成判断所需的最小上下文；不默认扫描全部 docs、Proposal archive 或 coding guides。

## 3. Right-sized delivery
收到新的 coding input 时，先选择最小正确路径：
- **New capability / direction** → Proposal → Review → Gate R；Human 接受 `START_NOW` 后才进入正式 Work Item。
- **Approved design must change** → Gate A；不得用新 Work Item 或 Direct Change 绕过已批准设计。
- **Direct Change**：目标清楚、低风险、小范围，且不改变 approved behavior/public contract/state/security/persistence/long-lived architecture 时，走 `inspect → change → targeted verify → review → report`；默认不创建 Work Item/TODO/Spec/Plan/Gate B/Gate C。
- **Work Item**：scope 已获批准，但 change 需要独立设计/验收、多个重要 design fork、重大 contract/state/data/security change 或跨 session coordination 时，走 `Investigation → Spec → Gate B → Plan → Implement/Test/Review → Gate C`。
- 执行过程中一旦发现 routing 前提不再成立，立即重新 routing；不要为了省流程把大 change 伪装成 Direct Change，也不要为了流程把小改强制升级。

## 4. Human Gates
- **Gate R — Proposal Decision**：新 capability/direction 先走 `Proposal → Quality Review → Admission Review → recommendation → Gate R`。Review 按 Proposal 模板执行，并结合真实 repo / Product / Roadmap / Current Milestone 检查事实、重复/覆盖、scope coherence、solution lock-in、风险与 feasibility。Human 确认 disposition 后执行对应 repository sync。
  - Recommendation：`START_NOW | ABSORB | DEFER | BLOCK | REJECT`，必须给出 evidence 与理由。
  - `START_NOW`：Human 判断是否现在加入计划并开始后续 Work Item；`ABSORB`：是否同意已被现有 capability / Milestone / Work Item 覆盖。
  - `DEFER`：是否同意暂缓理由及 Revisit Trigger；`BLOCK`：是否同意 blocker 及 Recheck Trigger；`REJECT`：是否同意不做的理由。
  - Human 可接受、否决或要求继续 Review / 修改 Proposal；确认前不得最终 archive、改变 Roadmap commitment、创建/启动 Work Item 或开始 implementation。
- **Gate A — Design Divergence**：实际工程证据表明已批准的 project design、Current Milestone scope/AC 或 current approved change design（如 accepted Spec）需要实质调整时，立即停止受影响实现；说明 original baseline、verified evidence、conflict、suggested change、alternatives 和 affected owners，未经 Human 确认不继续。accepted 后先同步受影响 approved owners，再恢复执行。
- **Gate B — Spec Review**：正式 Work Item Spec 收敛后，提供 Spec + 简洁 Review Packet，帮助 Human 审 system/user behavior、flow、source of truth、failure semantics、invariants 和重要 design forks；不要求 Human 审 implementation task decomposition。accepted 后把 Spec 作为 approved baseline、更新 TODO live status，再创建/更新 Plan。
- **Gate C — Feature Acceptance**：Work Item 完成必要 implementation、automatic verification、review 和 applicable E2E 后，说明实际完成内容、已执行验证、Human 手动检查步骤和预期结果；Human accepted 前不得 Work Item Done。accepted 后执行 Work Item closeout + owner sync；failed 后先重新 routing：implementation defect → fix；plan-local → adjust；approved design change → Gate A；new capability → Proposal → Gate R。
- **Gate D — Milestone Acceptance**：Current Milestone 的 required Work Items 完成且 DoD/Acceptance Criteria 均有 evidence 后，按每条 AC 映射实际证据、Work Item final state、已知 limitation/deferred scope，提交 Milestone Acceptance Packet；只有 Human accepted 后才能同步 roadmap/project-state、执行 closeout / next Milestone。

## 5. Verification 与 Repository sync
- **Verification purpose**：验证必须与 change impact 匹配；发现 implementation 违反 approved design → defect，发现真实证据证明 approved design 本身不成立 → Gate A。
- 正式 Work Item 进入 verification/E2E/Gate C 前读取 `docs/coding-agent-instructions/verification-and-acceptance.md`，用于确定最小充分验证、E2E 复用/新增策略、Gate C readiness 和验收失败后的 routing。
- **Owner principle**：durable fact 变化时更新它的 owner，而不是“Gate 到了就更新所有文件”。`TODO.md` = live Work Item state；`project-state.md` = Human checkpoint；Spec = approved Work Item design；Plan = implementation path；project docs = product/roadmap/architecture truth；`CLAUDE.md` = every-session standing rules/critical boundaries/code map/stable commands。
- Human Gate accepted、Work Item/PR/Milestone durable checkpoint、持续 blocker 变化或 closeout 时读取 `docs/coding-agent-instructions/documentation-lifecycle.md`，执行对应 Post-decision sync；只更新实际受影响 owner。
- 只有 Gate C accepted 后，已经实际成立且具有长期价值的事实才可同步进 architecture 并标记 `Verified Current`；future design 不得提前写成 current truth。

## 6. Git 工作流
- 正式 Work Item 默认使用独立 branch/worktree，不同 Work Item 不混在同一开发分支；若仓库已有更具体约定，以仓库现有约定为准。
- Branch 默认使用 ASCII：`<type>/<work-item-id>-<short-description>`；常用 type：`feat`、`fix`、`refactor`、`test`、`docs`、`chore`，例如 `feat/claim-04-ai-assessment`。
- Commit 的自然语言描述统一使用中文，推荐 `<type>(<scope>): <中文描述>`，例如 `fix(claim): 修复状态重复推进`；一个 commit 表达一个 coherent change，不塞入无关修改，不擅自改写已共享历史。
- 正常 feature/fix 默认通过 PR 集成：完成当前 Work Item → 必要验证 → push → 创建 PR；除非 Human 明确要求，不直接合入或 push base/main。
- 一个 PR 原则上对应一个 Work Item，或经明确确认的紧密相关变更集合；PR 至少说明做了什么、为什么、如何验证，以及已知风险、限制或后续事项。
- 与当前 Work Item 直接相关的 TODO 几行更新、typo、注释等 trivial docs/文字修正可随当前 branch/PR 一并提交；无关琐碎修改不单独开 PR，也不得污染当前 review scope，可搭乘下一个合适 Work Item。
- 不丢弃、覆盖、reset 或提交来源不明或不属于当前工作的修改；不得 force-push、destructive reset、重写共享历史或删除归属不明的 branch/worktree，除非 Human 明确授权。

## 7. Runtime / 常驻约束
- 启动服务前先检查是否已有等价实例；不得重复启动，也不得使用宽泛 kill 命令影响非 Agent-owned 进程。
- 只管理当前任务由 Agent 启动的服务和临时进程；Human 测试期间保持必要服务，测试完成后关闭不再需要的 Agent-owned 服务。
- 未完成必要验证和对应 Human Gate，不得宣称 Work Item 或 Milestone 完成。
- 截图与临时产物（会话转录等）统一放 `otherfiles/`（已 gitignore），不得落到项目根目录；Playwright 截图/快照须显式指定 `otherfiles/` 路径。

## 8. 安全与契约约束（长期有效）
- 严禁提交环境变量文件（如 `.env`）、密钥、token、私钥、真实敏感数据或其他凭证；代码、测试输出和日志不得泄露完整 secret、credential 或未脱敏敏感内容。
- 不绕过项目既有的认证、授权、输入校验、数据访问和分层边界；若正确实现必须改变这些长期边界，先走 Gate A。
- 不静默破坏已公开、已持久化或被其他模块依赖的 contract，包括接口字段、事件、配置键、序列化格式和数据语义；需要不兼容修改时必须说明兼容与迁移影响，并经过对应 Human Gate。
- 普通自动测试默认不调用真实第三方/生产服务，不执行收费、不可逆或高影响 side effect；优先使用 mock、fake、sandbox 或隔离测试环境，只有任务明确需要且风险可控时才使用真实资源。
- 删除、覆盖、批量修改、迁移或其他高影响数据操作必须先验证作用范围、失败处理和恢复策略；不得为修复局部问题顺手修改无关数据。
- 日志、错误信息和调试产物遵循最小必要信息原则；涉及用户数据、请求/响应内容或业务敏感信息时，必须遵守项目既有的脱敏、访问和保留规则。

## 9. Completion
- 只汇报实际执行过的验证；Direct Change 完成后汇报 changed + verification + remaining risk。
- Work Item 未完成必要 verification / Gate C 不得 Done；Milestone 未 Gate D accepted 不得标记 accepted。
