# Claude Code：Claude Code MCP

- 来源：[Claude Code MCP](https://www.runoob.com/claude-code/claude-code-mcp.html)
- 分类：AI / 智能开发
- 技术：Claude Code
- 笔记类型：概念卡
- 章节序号：0151

## 本章内容

如果说 Claude Code 是一个优秀的打字员（代码生成）和测试员（代码校验），那么加上 MCP（Model Context Protocol，模型上下文协议） 则是让 Claude 真正拥有了外部感官和手脚——它不再局限于当前项目的代码文件，而是能主动连接外部世界的资源与工具，成为你的全链路开发协作伙伴。


### 什么是 MCP (Model Context Protocol)？

MCP 是 Anthropic 推出的一套开放的标准化协议，专为解决AI 与外部工具协作的核心痛点而生。

MCP 的核心逻辑颠覆了传统思路：不要让 AI 去逐一学习所有工具的使用规则，而是让所有工具都提供一个统一的接口给 AI。

这个逻辑就像现实中的通用插座——不用让电器适配不同的插座，只要插座统一标准，所有电器都能直接使用。

连接 MCP 服务器后，你可以让 Claude Code：

- 从 JIRA/工单系统获取需求并开发功能、创建 GitHub PR
- 分析 Sentry 监控数据、定位生产环境错误
- 查询 PostgreSQL/MySQL 等数据库数据
- 基于 Figma 设计更新代码、自动化生成邮件草稿等


### 为什么 Claude Code 需要 MCP？

在没有 MCP 之前，Claude Code 的能力被严格限制在你当前打开的项目文件夹内，就像一个坐井观天的助手，只能看到眼前的代码，无法感知项目之外的任何信息。而 MCP 的出现，彻底打破了这个信息孤岛，让 Claude 能深度参与全流程开发：

举几个直观的场景对比，你就能快速理解 MCP 的价值：

简单来说，MCP 让 Claude Code 从被动接收信息的助手，变成了主动获取信息、执行操作的协作伙伴。


## Claude Code 中 MCP 的基本使用方式

Claude Code 内置了完整的 MCP 管理能力，核心命令只有一个：

```text
claude mcp
```

常用子命令:


## 安装 MCP 服务器

MCP 服务器支持 HTTP/SSE/stdio 三种接入方式，推荐优先使用 HTTP（SSE已弃用）。


### 1. 远程 HTTP 服务器（推荐）

适用于云服务类工具，是最通用的方式：

```text
# 基础语法
claude mcp add --transport http <服务器名称> <服务器URL>

# 示例1：连接Notion
claude mcp add --transport http notion https://mcp.notion.com/mcp

# 示例2：带身份验证的HTTP服务器
claude mcp add --transport http secure-api https://api.example.com/mcp \
  --header "Authorization: Bearer 你的令牌"
```


### 2. 远程 SSE 服务器（已弃用）

仅兼容旧版工具，优先用 HTTP 替代：

```text
# 基础语法（仅兼容用）
claude mcp add --transport sse <服务器名称> <服务器URL>
# 示例：连接Asana
claude mcp add --transport sse asana https://mcp.asana.com/sse
```


### 3. 本地 stdio 服务器

适用于需要本地系统访问的工具（如本地数据库、自定义脚本）：

```text
# 基础语法（注意：--前是Claude参数，--后是服务器命令）
claude mcp add --transport stdio [--env 环境变量] <服务器名称> -- <启动命令>

# 示例：连接Airtable（需替换自己的API密钥）
claude mcp add --transport stdio --env AIRTABLE_API_KEY=你的密钥 airtable \
  -- npx -y airtable-mcp-server
```

关键注意：--transport/--env 等参数必须放在服务器名称前面，-- 用于分隔Claude参数和服务器命令，避免参数冲突。


## 管理 MCP 服务器

配置完成后，你可以通过以下命令管理服务器：

```text
# 列出所有已配置的服务器
claude mcp list

# 查看指定服务器详情（如github）
claude mcp get github

# 删除指定服务器
claude mcp remove github

# 在Claude Code中检查服务器状态
/mcp
```


## 配置范围（控制服务器可见性）

你可以指定 MCP 服务器的生效范围，适配个人/团队使用场景：

优先级：local > project > user（同名服务器，本地配置覆盖共享配置）


## 实用示例


### 示例 1：GitHub 代码审查

```text
claude mcp add --transport http github https://api.githubcopilot.com/mcp/
```

在 Claude Code 中：

```text
> Review PR #456 and suggest improvements
> Show me all open PRs assigned to me
```


### 示例 2：Sentry 生产环境排错

```text
claude mcp add --transport http sentry https://mcp.sentry.dev/mcp
```

```text
> /mcp   # 完成 OAuth 登录
> What are the most common errors in the last 24 hours?
```


### 示例 3：直接查 PostgreSQL

```text
claude mcp add --transport stdio db \
  -- npx -y @bytebase/dbhub \
  --dsn "postgresql://readonly:pass@prod.db.com:5432/analytics"
```

```text
> Show me the schema for the orders table
> Which users haven't purchased in 90 days?
```


## 在对话中使用 MCP 的高级方式


### 1、使用 @ 引用 MCP 资源

```text
> Analyze @github:issue://123 and suggest a fix
```

支持多个资源对比：

```text
> Compare @postgres:schema://users with @docs:file://user-model
```


### 2、MCP Prompt 作为斜杠命令

MCP 可以暴露命令：

```text
/mcp__github__list_prs
/mcp__jira__create_issue "Login bug" high
```

Claude 会像执行内置命令一样执行它们。


## 关键注意事项

- 身份验证：远程MCP服务器（如GitHub/Sentry）需在Claude Code中执行 /mcp 完成OAuth 2.0授权；
- Windows兼容：本地stdio服务器若用npx，需加cmd /c包装（如-- cmd /c npx -y 包名），否则会报"Connection closed"错误；
- 第三方风险：使用非官方MCP服务器时，需确认来源可信，避免提示注入/安全风险；
- 参数顺序：stdio服务器配置时，-- 前后的参数不可颠倒，否则会执行失败。


## 记忆卡片

- 一句话定义：`Claude Code MCP` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
