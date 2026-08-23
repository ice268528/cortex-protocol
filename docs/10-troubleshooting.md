# 10. 常见跑偏方式与修正

## 症状 1：网页版 ChatGPT 一次生成六七个设计文件

**问题**：人没有真正参与设计，后续冲突难以回溯。

**修正**：回到逐文件工作协议；当前文件没收敛前不进入下一文件。

## 症状 2：`TODO.md` 出现“修改 foo.ts 第 37 行”

**问题**：项目级 Work Item 和 Superpowers implementation tasks 混在一起。

**修正**：TODO 只保留可独立验证的项目级 change；文件/函数/测试步骤留在 plan。

## 症状 3：`CLAUDE.md` 写了大量 TDD/subagent/review 细节

**问题**：与 Superpowers 重复，两个流程可能互相打架。

**修正**：删掉重复机制，只保留项目级 standing policies 和衔接规则。

## 症状 4：Agent 发现设计不成立，但“先做出来再说”

**问题**：重大设计偏差被静默吞掉。

**修正**：触发 Gate A，提交证据、冲突、建议、影响范围，等人决定。

## 症状 5：每次新会话都粘贴一大段项目背景

**问题**：Repository state 不完整或不可信。

**修正**：补齐 CLAUDE/TODO/Stage/project docs，让冷启动能从仓库恢复。

## 症状 6：人一直提醒“更新 TODO、同步文档、关服务”

**问题**：housekeeping 仍在人的脑内。

**修正**：把这些职责写进 coding-agent instructions，并要求 Gate 通过后主动 reconcile。

## 症状 7：每次创建 PR 都再做一次完整 review

**问题**：机械重复。

**修正**：判断 PR HEAD 是否就是刚刚 clean review 的 HEAD；没有变化就复用，变化后再 review。

## 症状 8：Playwright 只在验收时临时写，之后删除

**问题**：没有形成 regression asset。

**修正**：有长期回归价值的测试提交进 repo，未来复用或随行为更新。
