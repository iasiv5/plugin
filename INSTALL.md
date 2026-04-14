# 安装与启用

## 前提

- VS Code 版本支持 GitHub Copilot Agent Plugins（预览功能）。
- 已开启设置 `chat.plugins.enabled`。

## 方式一：从 GitHub 源安装

1. 在 VS Code 命令面板执行 `Chat: Install Plugin From Source`。
2. 输入仓库地址 `https://github.com/iasiv5/plugin`。
3. 完成安装后重新打开一个 Copilot Chat 会话。

## 方式二：作为 Marketplace 仓库使用

1. 在支持 marketplace 的入口添加仓库 `iasiv5/plugin`。
2. 从该 marketplace 中选择并安装插件 `iasi-plugin`。

如果提示“这似乎不是有效的插件市场”：

1. 先确认远程仓库已包含 `.github/plugin/marketplace.json`。
2. 刷新/重试安装入口，避免命中旧缓存。
3. 确认你选择的是插件项 `iasi-plugin`，而不是只添加 marketplace 源后即结束。

## 验证

- 打开 Chat 的插件列表，确认插件已启用。
- 输入 `/`，确认能看到 `code-review`。
- 发送一条代码审查请求，检查 skill 是否被调用。
- 执行一次会话后，确认 hook 已在仓库 `logs/copilot/` 下写入日志（如启用了日志）。