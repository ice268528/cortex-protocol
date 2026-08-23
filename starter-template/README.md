# Cortex Protocol — Starter Template

把本目录内容复制/合并到你的真实项目仓库，用它建立 Cortex Protocol 的 Repository state 和 Claude Code standing policy。

## 安装

1. `CLAUDE.template.md` 填完后重命名为根 `CLAUDE.md`。
2. `TODO.template.md` 填完后重命名为根 `TODO.md`。
3. 保留 `docs/coding-agent-instructions/`，把项目真实命令、目录、服务和验证要求填进去。
4. 在 `docs/project/` 放网页版 ChatGPT 阶段已经 accepted 的长期设计。
5. 在 `docs/stages/` 放 Stage 定义。
6. `docs/coding-guides/` 只放需要 Human 明确指定读取的已验证技术事实。
7. `docs/superpowers/` 由项目实际使用的 Superpowers workflow 产生/维护 change-level spec 与 plan；不要把这里当长期项目设计。

## 模板内容

```text
starter-template/
├── CLAUDE.template.md
├── TODO.template.md
├── docs/
│   ├── coding-agent-instructions/   # 按需加载的 standing rules
│   ├── coding-guides/               # Human 明确指定时才读
│   ├── project/                     # current long-term design
│   └── stages/                      # Stage commitments
└── templates/
    ├── project-document.template.md
    └── stage.template.md
```

## 使用前必须替换

搜索 `【`，把所有占位符改成真实项目内容，尤其是：

- 启动/测试/完整验证命令；
- 代码目录；
- 服务和端口；
- 测试路径；
- 项目特有边界。

不要让 Agent 在占位符仍存在时把模板当作真实项目事实。
