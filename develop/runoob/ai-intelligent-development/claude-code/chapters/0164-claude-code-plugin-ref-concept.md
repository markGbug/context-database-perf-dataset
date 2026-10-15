# Claude Code：Claude Code 插件参考手册

- 来源：[Claude Code 插件参考手册](https://www.runoob.com/claude-code/claude-code-plugin-ref.html)
- 分类：AI / 智能开发
- 技术：Claude Code
- 笔记类型：概念卡
- 章节序号：0164

## 本章内容

插件是 Claude Code 的功能扩展核心，能帮你添加自定义斜杠命令、子代理、自动化钩子等能力。本教程从核心组件、配置规范、CLI 管理三个维度，带你快速掌握插件的使用与开发要点。


## 插件核心组件：5类扩展能力

插件通过 5 类组件实现功能扩展，每个组件都有固定的存储位置和格式要求。


### 关键组件示例

1、钩子配置示例：文件编辑后自动格式化

```text
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Write|Edit",
        "hooks": [
          {
            "type": "command",
            "command": "${CLAUDE_PLUGIN_ROOT}/scripts/format-code.sh"
          }
        ]
      }
    ]
  }
```

：支持 Go 语言智能提示

```text
{
  "go": {
    "command": "gopls",
    "args": ["serve"],
    "extensionToLanguage": {
      ".go": "go"
    }
  }
}
```


## 插件基础规范：安装范围与清单


### 1. 安装范围：决定插件的可用范围

安装插件时需选择范围，不同范围对应不同的配置文件和使用场景：


### 2. 插件清单：plugin.json 必知要点

plugin.json 是插件的核心配置文件，存放于 .claude-plugin/ 目录下，用于定义插件元数据和组件路径。

```text
{
  "version": "1.0.0", // 语义化版本
  "description": "提供 Go 语言代码智能和调试能力",
  "author": {
    "name": "Dev Team",
    "email": "dev@example.com"
  },
  "license": "MIT"
}
```

用于指定自定义组件的位置，路径需相对插件根目录且以 ./ 开头：

```text
{
  "commands": ["./custom-commands/deploy.md"],
  "agents": "./custom-agents/",
  "hooks": "./hooks.json"
}
```

${CLAUDE_PLUGIN_ROOT}：插件根目录的绝对路径，用于脚本和配置中引用插件内文件，避免路径错误。


### 3. 标准插件目录结构

```text
my-plugin/
├── .claude-plugin/           # 元数据目录
│   └── plugin.json          # 插件清单（必需）
├── commands/                 # 自定义斜杠命令
├── agents/                   # 子代理定义
├── skills/                   # 自动技能
├── hooks/                    # 事件钩子配置
├── .mcp.json                # MCP 服务器配置
├── .lsp.json                # LSP 服务器配置
└── scripts/                 # 钩子执行脚本
```

注意：commands/ agents/ 等组件目录必须在插件根目录，不能放在 .claude-plugin/ 内。


## 插件管理：CLI 命令速查

通过 Claude Code CLI 可快速完成插件的安装、卸载、启用/禁用等操作，适合脚本和自动化场景。


## 调试与排错：常见问题解决


### 1. 调试命令

运行以下命令查看插件加载详情，定位配置和加载问题：

```text
claude --debug
```

可查看：插件加载状态、清单语法错误、组件注册情况、MCP/LSP 服务器初始化日志。


### 2. 高频问题与解决方案


## 版本管理与分发

- 版本规范：遵循语义化版本 MAJOR.MINOR.PATCH，比如 1.2.3
- 分发渠道：通过插件市场分发，或直接分享插件目录（需包含完整结构）
- 更新日志：建议在插件根目录添加 CHANGELOG.md，记录版本更新内容


## 记忆卡片

- 一句话定义：`Claude Code 插件参考手册` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
