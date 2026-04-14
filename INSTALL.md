# 安装与启用

## 前提

- VS Code 版本支持 GitHub Copilot Agent Plugins（预览功能）。
- 已开启设置 `chat.plugins.enabled`。

## 方式一：从 GitHub 源安装

1. 将当前 `plugin/` 目录单独上传为一个 GitHub 仓库。
2. 在 VS Code 命令面板执行 `Chat: Install Plugin From Source`。
3. 输入该 GitHub 仓库 URL，完成安装。

## 方式二：本地路径启用（调试）

在 `settings.json` 增加：

```json
{
  "chat.pluginLocations": {
    "d:/git-repo/ai-workspace-assets/plugin": true
  }
}
```

## 验证

- 打开 Chat 的插件列表，确认插件已启用。
- 输入 `/`，确认能看到 `code-review`。
- 发送一条代码审查请求，检查 skill 是否被调用。
- 执行一次会话后，确认 hook 已在仓库 `logs/copilot/` 下写入日志（如启用了日志）。