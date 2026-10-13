# 01 — 从文本脚手架开始

把 `starter-template/` 复制进你的 Repository。

一开始可以只有：

```text
CLAUDE.md
TODO.md

docs/
├── project/
│   └── architecture/
│       └── README.md
├── proposals/
├── superpowers/
├── coding-agent-instructions/
└── coding-guides/
```

此时：

```text
product.md       还没生成
roadmap.md       还没生成
project-state.md 还没生成
architecture topic 不需要先建
```

## Human 现在做什么

只填能确定的 `CLAUDE.md` 内容：

```text
项目一句话
critical boundary
repo minimal code map
Git / service / secret 等已有硬约束
```

## 不要做

```text
✗ 先创建一堆空 architecture 文件
✗ 先列 30 个 Work Item
✗ 先写 Spec
✗ 让 Coding Agent 猜产品需求
```

下一步：和 Web ChatGPT 讨论产品。
