# iasi plugin

这是一个最小可用的 GitHub Copilot plugin 仓库。

当前版本包含以下可复用资产：

- `code-review` skill
- `session-logger` hook
- `create-git-commit-message-IEC` command prompt
- `python-cli-scripts` path-specific instruction

`code-review` 提供结构化代码审查流程。
`session-logger` 负责记录会话与提示词事件，便于审计和分析。

## 当前结构

```text
.
├── .plugin/
│   └── plugin.json
├── commands/
│   └── create-git-commit-message-IEC.prompt.md
├── hooks/
│   ├── hooks.json
│   └── session-logger/
├── instructions/
│   └── python-cli-scripts.instructions.md
├── .github/
│   └── copilot-instructions.md
└── skills/
    └── code-review/
        ├── SKILL.md
        └── resources/
```

## 为什么先做成这个形态

- 目录采用插件常见分层：`.plugin/`、`commands/`、`hooks/`、`skills/`。
- 本仓库按“单插件仓库”使用，不包含 marketplace 索引文件。
- 这样可以保证通过远程插件源安装时，能力文件路径稳定且便于后续扩展。

## 安装方式

### 从 Git 仓库安装

1. 在 VS Code 中启用 `chat.plugins.enabled`。
2. 执行命令 `Chat: Install Plugin From Source`。
3. 输入仓库地址：`https://github.com/iasiv5/plugin`。

## 使用方式

- 在聊天中直接输入 `/code-review` 手动调用。
- 或在你发起代码审查请求时，让 Copilot 根据 skill 描述自动加载。
- 会话期间，hook 会按 `hooks/hooks.json` 配置自动记录日志事件。

## 当前边界

- 已包含：1 个 skill、1 组 hook（session-logger）、1 个 command prompt、1 条 path-specific instruction。
- 未包含：自定义 agent、MCP server、marketplace 配置。
- 未包含：任何依赖本地绝对路径的安装逻辑。

## 后续建议

如果你后续想把现有 `prompts/` 里的工作流继续迁入 plugin，建议优先按以下顺序演进：

1. 把路由型 prompt 继续沉淀到 `commands/` 或改造成 `agents/` 下的自定义 agent。
2. 把与环境初始化强绑定的 prompt 拆成更通用的 skill 或 agent。
3. 只有在确实需要外部命令或系统集成时，再增加新的 hooks 或 MCP。