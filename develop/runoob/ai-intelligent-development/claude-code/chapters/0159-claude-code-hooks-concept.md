# Claude Code：Claude Code 钩子

- 来源：[Claude Code 钩子](https://www.runoob.com/claude-code/claude-code-hooks.html)
- 分类：AI / 智能开发
- 技术：Claude Code
- 笔记类型：概念卡
- 章节序号：0159

## 本章内容

Claude Code 钩子是用户自定义的 Shell 命令，会在 Claude Code 生命周期的特定节点自动执行。

借助钩子，你可以对 Claude Code 的行为实现精准控制，确保某些操作（如代码格式化、日志记录）必定触发，而非依赖大模型自主选择是否执行。


### 钩子的典型应用场景

钩子能帮你实现很多实用功能，常见场景包括：

- 消息通知：当 Claude Code 等待输入或需要权限时，自动发送桌面/邮件提醒
- 自动格式化：编辑 .ts 文件后自动运行 prettier，修改 .go 文件后执行 gofmt
- 操作日志：记录 Claude 执行的所有命令，用于合规审计或调试排障
- 代码规范校验：若 Claude 生成的代码不符合项目规范（如命名规则），自动给出反馈
- 文件权限管控：阻止 Claude 修改生产环境配置文件或敏感目录（如 .env、.git）

相比于通过提示词约束 Claude 的行为，钩子是应用级的硬规则，只要触发对应事件就会强制执行，稳定性和可靠性更高。


### 重要安全提醒

钩子运行时会直接使用当前系统环境的凭证（如环境变量、用户权限），存在一定安全风险：

- 恶意钩子代码可能泄露你的敏感数据（如 API 密钥、项目源码）
- 错误的钩子命令可能导致文件误删、系统异常

必做安全操作：

- 注册钩子前，务必逐行审查命令的逻辑和权限
- 避免在钩子中执行来源不明的脚本
- 详细安全最佳实践，可参考官方文档的 安全注意事项


## 钩子事件类型说明

Claude Code 内置了多个生命周期事件，你可以为不同事件绑定钩子命令。每个事件会传递不同的上下文数据，且对 Claude 行为的影响方式不同。


## 快速入门：实现命令日志记录

下面以 记录 Claude 执行的所有 Bash 命令 为例，带你一步步完成钩子的配置和使用。


### 前置准备

安装 jq 工具（用于命令行解析 JSON 数据）：

- macOS：brew install jq
- Linux：sudo apt install jq / sudo yum install jq
- Windows：下载 jq 官方安装包，或通过 WSL 安装


### 步骤 1：打开钩子配置界面

在 Claude Code 的交互界面中，输入斜杠命令 /hooks，回车后选择要绑定的事件 —— 这里我们选 PreToolUse（工具调用前触发，适合记录命令）。


### 步骤 2：添加事件匹配器

匹配器的作用是 限定钩子的触发条件，只在指定工具被调用时执行钩子命令。

- 选择 + Add new matcher…
- 输入匹配关键词 Bash，表示仅当 Claude 调用 Bash 工具时触发钩子 小技巧：输入 * 可以匹配所有工具，实现全局钩子


### 步骤 3：添加钩子命令

选择 + Add new hook…，输入以下命令（功能：提取命令内容和描述，写入日志文件）：

```text
jq -r '"\(.tool_input.command) - \(.tool_input.description // "无描述信息")"' >> ~/.claude/bash-command-log.txt
```

命令说明：

- jq -r ...：提取 JSON 中的命令（command）和描述（description），无描述时显示"无描述信息"
- >> ~/.claude/...：将内容追加写入用户主目录下的日志文件


### 步骤 4：选择配置存储位置

配置保存位置决定钩子的生效范围：

- User settings：保存到用户级配置（~/.claude/settings.json），所有项目生效
- Project settings：保存到当前项目配置（.claude/settings.local.json），仅当前项目生效

这里我们选 User settings，实现全局命令日志记录。选择后按 Esc 键退出配置界面，钩子即注册完成。


### 步骤 5：验证钩子配置

- 再次输入 /hooks 命令，可查看已配置的钩子列表
- 或直接打开配置文件 ~/.claude/settings.json，会看到如下配置内容： { "hooks": { "PreToolUse": [ { "matcher": "Bash", "hooks": [ { "type": "command", "command": "jq -r '\"\\(.tool_input.command) - \\(.tool_input.description // \"无描述信息\")\"' >> ~/.claude/bash-command-log.txt" } ] } ] } }


### 步骤 6：测试钩子效果

- 在 Claude Code 中输入指令：帮我执行 ls 命令
- 执行完成后，在终端中查看日志文件： cat ~/.claude/bash-command-log.txt
- 若日志中出现如下内容，说明钩子配置成功： ls - Lists files and directories


## 实用钩子示例

下面提供几个常用的钩子配置，你可以直接复制使用或按需修改。

📌 完整示例代码可参考官方仓库：bash 命令验证器示例


### 示例 1：自动格式化 TypeScript 文件

功能：编辑/写入 .ts 文件后，自动用 prettier 格式化代码

```text
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Edit|Write", // 匹配“编辑”和“写入”工具
        "hooks": [
          {
            "type": "command",
            "command": "jq -r '.tool_input.file_path' | { read file_path; if echo \"$file_path\" | grep -q '\\.ts$'; then npx prettier --write \"$file_path\"; fi; }"
          }
        ]
      }
    ]
  }
}
```


### 示例 2：自动修复 Markdown 文件格式

功能：为无语言标签的代码块自动补全标签、清理多余空行

```text
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Edit|Write",
        "hooks": [
          {
            "type": "command",
            "command": "\"$CLAUDE_PROJECT_DIR\"/.claude/hooks/markdown_formatter.py"
          }
        ]
      }
    ]
  }
}
```

在项目目录下新建文件 .claude/hooks/markdown_formatter.py，粘贴以下代码：


## 实例

```text
chmod +x .claude/hooks/markdown_formatter.py
```


### 示例 3：Claude 等待输入时发送桌面通知

功能：当 Claude 需要用户输入时，自动弹出桌面提醒（适用于 Linux/macOS）

```text
{
  "hooks": {
    "Notification": [
      {
        "matcher": "", // 匹配所有通知事件
        "hooks": [
          {
            "type": "command",
            "command": "notify-send 'Claude Code 提示' '请你输入指令或确认权限'"
          }
        ]
      }
    ]
  }
}
```


### 示例 4：禁止修改敏感文件

功能：阻止 Claude 编辑 .env、package-lock.json 等敏感文件

```text
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Edit|Write",
        "hooks": [
          {
            "type": "command",
            "command": "python3 -c \"import json, sys; data=json.load(sys.stdin); path=data.get('tool_input',{}).get('file_path',''); sys.exit(2 if any(p in path for p in ['.env', 'package-lock.json', '.git/']) else 0)\""
          }
        ]
      }
    ]
  }
}
```

说明：脚本返回状态码 2 时，Claude Code 会拦截此次工具调用，从而阻止文件修改。


## Claude Code 钩子参考手册


### 配置文件路径


### 核心配置结构

Hooks 按事件+匹配器组织，支持 command（执行 Shell 命令）和 prompt（调用 LLM 决策）两种类型。

```text
{
  "hooks": {
    "【钩子事件名】": [
      {
        "matcher": "【工具匹配规则】", // 部分事件可省略
        "hooks": [
          {
            "type": "command/prompt",
            "command": "【Shell 命令】", // type=command 时必填
            "prompt": "【LLM 提示词】",  // type=prompt 时必填
            "timeout": 30 // 可选，超时时间（秒）
          }
        ]
      }
    ]
  }
}
```


### 匹配器规则（仅适用于工具类事件）


### 特殊配置技巧


### 扩展配置（Skill/Agent/斜杠命令）

扩展配置允许直接在 Skill、Agent 或自定义斜杠命令的定义中内嵌 Hooks 配置，这类 Hooks 仅在对应组件被激活并运行时生效，组件执行完成后会自动清理，不会影响全局会话。

仅支持 PreToolUse、PostToolUse、Stop 三类事件，与全局 Hooks 功能一致，但作用域仅限当前 Skill/斜杠命令的生命周期。

- once: true（可选）：设置为 true 时，该 Hooks 在整个会话中仅运行一次，首次成功执行后会自动移除，避免重复触发。

```text
---
# Skill/斜杠命令的基础信息
name: secure-operations
description: 执行Shell命令前先做安全校验的工具
# Hooks 配置段
hooks:
  PreToolUse:
    # 匹配器：仅拦截Bash工具调用
    - matcher: "Bash"
      hooks:
        - type: "command"
          # 要执行的安全校验脚本
          command: "./scripts/security-check.sh"
          # 会话内仅执行一次
          once: true
          # 超时时间（秒），避免脚本卡死
          timeout: 15
---
```


### Agent 中的 Hooks 配置

同样仅支持 PreToolUse、PostToolUse、Stop 三类事件，作用域仅限该子 Agent 的任务执行周期。

无额外专属配置项，不支持 once: true（Agent 每次执行任务时，Hooks 都会触发）。

```text
---
# Agent 的基础信息
name: code-reviewer
description: 自动审查代码修改并运行代码检查的子代理
# Hooks 配置段
hooks:
  PostToolUse:
    # 匹配器：拦截Edit（编辑）或Write（写入）工具
    - matcher: "Edit|Write"
      hooks:
        - type: "command"
          # 代码检查脚本，执行lint校验
          command: "./scripts/run-linter.sh"
          # 超时时间（秒）
          timeout: 30
---
```

注意事项：

- 组件内 Hooks 的匹配器规则与全局 Hooks 完全一致：支持精确匹配（如 "Write"）、多工具匹配（如 "Edit|Write"）、通配匹配（"*"），且区分大小写；
- 组件内 Hooks 与全局 Hooks 会并行执行：若全局和组件内同时配置了针对同一事件的 Hooks，触发时两类 Hooks 会一起运行，互不冲突；
- 配置格式要求：组件内 Hooks 需写在 frontmatter（--- 包裹的区域）中，遵循 YAML 语法，缩进错误会导致配置失效；
- 脚本路径建议：优先使用相对路径（如 ./scripts/xxx.sh），或借助 $CLAUDE_PROJECT_DIR 环境变量指定绝对路径，确保组件在任意目录下都能找到脚本。


## 后续章节

- 钩子事件--工具类事件（支持匹配器）
- 钩子事件--会话/任务类事件（无匹配器）
- 钩子类型对比
- 输入与输出 -- 钩子输入（stdin 传入 JSON）
- 钩子输出（两种方式）
- MCP 工具的 Hooks 配置
- MCP 工具命名规则
- 匹配示例
- 安全与调试
- 安全最佳实践
- 调试技巧

## 记忆卡片

- 一句话定义：`Claude Code 钩子` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
