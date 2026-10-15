# Hermes Agent：Hermes Agent MCP 集成

- 来源：[Hermes Agent MCP](https://www.runoob.com/hermes-agent/hermes-agent-mcp.html)
- 分类：AI / 智能开发
- 技术：Hermes Agent
- 笔记类型：概念卡
- 章节序号：0265

## 本章内容

MCP（Model Context Protocol）是 Anthropic 提出的开放协议，用于标准化 LLM 与外部工具的交互。

Hermes 原生支持 MCP，无需修改核心代码就能接入 GitHub、数据库、文件系统、浏览器堆栈、内部 API 等任何 MCP 兼容服务。

本章将深入 MCP 的两种接入方式、工具过滤策略、安全隔离机制以及常见问题排查。


## 什么是 MCP

MCP 解决了一个实际问题：每接入一个新服务，传统做法需要写适配代码、定义工具 Schema、处理认证——每个服务都是一次性工作。

MCP 把这些标准化了。任何实现 MCP 协议的服务，Hermes 都能直接接入，无需额外开发。

MCP 的核心角色：

```text
Hermes Agent（MCP 客户端）
    │
    ├── stdio ──→ MCP 服务器 A（本地子进程）
    │                  └── 暴露工具：git_commit, git_push...
    │
    ├── HTTP ───→ MCP 服务器 B（远程服务）
    │                  └── 暴露工具：list_issues, create_issue...
    │
    └── HTTP ───→ MCP 服务器 C（远程 OAuth）
                       └── 暴露工具：search_docs, create_page...
```

标准安装已包含 MCP 支持，无需额外步骤。所有 MCP 服务器在 ~/.hermes/config.yaml 中统一配置。

MCP 不是 Hermes 的专有协议——它是开放的。为其他支持 MCP 的工具编写的服务器（如 Claude Code 的 MCP 服务器）可以直接在 Hermes 中使用，反之亦然。


## 两种 MCP 服务器类型


### 本地 stdio 服务器

以子进程形式在本地运行，通过标准输入/输出（stdin/stdout）与 Hermes 通信。

通信使用 JSON-RPC 协议，每条消息以换行符分隔。

适用场景：工具已本地安装，需要低延迟访问本地资源（文件系统、Git 仓库、本地数据库）。


## 实例

stdio 服务器的生命周期由 Hermes 管理：

- 会话启动或 /reload-mcp 时，Hermes 启动子进程
- 会话结束或禁用服务器时，Hermes 终止子进程
- 子进程崩溃会自动重启（最多重试 3 次）


### 远程 HTTP 服务器

通过 HTTP 请求直接连接远程 MCP 端点，支持多种认证方式。

适用场景：工具在远端托管，或组织内部已有 MCP 接口。


## 实例


### 两种类型对比


## Nous 精选 MCP 目录

Hermes 内置了一个经 Nous Research 审核的 MCP 目录，提供一键安装体验。


### 浏览与安装

打开交互式选择器（TUI），浏览所有目录条目:

```text
hermes mcp
```

其他命令：

```text
# 纯文本列表（适合脚本化）
hermes mcp catalog

# 按名称一键安装
hermes mcp install n8n
hermes mcp install github
hermes mcp install linear
```

交互式选择器显示每个条目的当前状态：

```text
n8n          available              管理和检查 n8n 工作流
linear       enabled                Linear 问题/项目管理（远程 OAuth）
github       installed (disabled)   GitHub 仓库 + PR 工具
filesystem   installed (enabled)    安全的文件系统操作
postgres     available               PostgreSQL 数据库查询
slack        available               Slack 消息和频道管理
```

状态说明：

桌面版在设置菜单中查看配置：

仪表盘在左侧 MCP 菜单查看配置：


### 安装过程发生了什么

一键安装自动完成三步：

- 配置引导：提示填写 API Key 或引导 OAuth 浏览器授权流程
- 工具探测：连接服务器，获取其暴露的完整工具列表
- 工具选择：展示工具清单让你勾选要启用的工具（默认全选）

第三步（工具选择）是重要的安全环节——不是每个工具你都需要。比如 GitHub 服务器暴露了 delete_repo，如果你不需要，可以取消勾选。


## 工具过滤：只暴露你需要的

每个 MCP 服务器都支持精细的工具过滤。这是减少 Agent 攻击面的关键安全机制。


### include 模式（白名单）

只注册列表中的工具，其余全部排除：


## 实例


### exclude 模式（黑名单）

排除列表中的工具，其余全部注册：


## 实例


### 过滤规则优先级


### 关闭资源和提示词

MCP 服务器除了工具，还可能暴露资源和提示词（Prompts）。如果不需要，可以关闭：


## 实例


## MCP 环境变量隔离

这是 Hermes 的 MCP 安全机制中最容易被忽略但最重要的设计。

MCP stdio 子进程接收一个经过过滤的环境，默认只传递以下变量：

```text
PATH, HOME, USER, LANG, LC_ALL, TERM, SHELL, TMPDIR
以及所有 XDG_* 变量
```

其他所有环境变量（API Key、Token、密码）都被屏蔽。

只有在 MCP 服务器配置的 env: 块中显式声明的变量才会传入子进程：


## 实例

为什么这样设计？假设你在 .env 中存了 10 个 API Key（OpenAI、Anthropic、SerpAPI、Telegram Bot Token...）。如果 MCP 服务器能读取所有环境变量，一个恶意的 MCP 服务器工具就可以窃取所有凭据。环境变量隔离确保它只能看到显式声明的那个。


### 错误信息自动脱敏

MCP 工具的错误信息在返回给 LLM 前会自动脱敏——敏感信息（API Key、Token、密码）替换为 [REDACTED]。

这防止了 Agent 在分析错误时意外看到明文凭据。


## 手动添加 MCP 服务器

除了从 Nous 目录一键安装，你也可以手动添加任何 MCP 兼容服务器。


## 实例

hermes mcp configure 会打开交互式工具选择界面，让你重新勾选要启用的工具。


## 重新加载 MCP 配置

修改了 config.yaml 中的 MCP 配置后，无需重启整个 Agent：


## 后续章节

- 实例
- 常见问题排查

## 记忆卡片

- 一句话定义：`Hermes Agent MCP` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
