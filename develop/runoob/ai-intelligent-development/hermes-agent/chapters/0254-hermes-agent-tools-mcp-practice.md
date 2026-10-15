# Hermes Agent：Hermes Agent 工具生态与 MCP 集成

- 来源：[Hermes Agent 工具](https://www.runoob.com/hermes-agent/hermes-agent-tools-mcp.html)
- 分类：AI / 智能开发
- 技术：Hermes Agent
- 笔记类型：练习笔记
- 章节序号：0254

## 本章内容

Hermes 的所有能力都通过工具（Tools）暴露给 Agent。

工具组织成工具集（Toolsets），工具集再组合成平台配置。这三层结构决定了 Agent 在不同场景下能做什么：

```text
工具（Tool）
  └── 工具集（Toolset）         # 相关工具的逻辑分组
        └── 平台配置            # 哪个平台加载哪些工具集
              └── 自定义工具集   # 你自己定义的组合
```


### 工具集管理命令

```text
# 打开 curses TUI，按平台开/关工具集
hermes tools

# 命令行列出所有工具和状态
hermes tools list

# 按名称启用或禁用工具集
hermes tools enable NAME
hermes tools disable NAME
```

桌面版，在左侧的技能与工具菜单：

关闭一个工具集，其中的工具从系统提示词中完全消失，不只是禁用——这直接节省 Token，并防止 Agent 误用不该用的工具。


## 内置工具集一览

Hermes 提供 70+ 内置工具，分为 28 个工具集。

以下按功能分类介绍最常用的工具集。


### 文件与系统


### 网络与内容


### Agent 能力


### 媒体创作

以下工具集需 Nous Portal 或对应 API Key：


### 自定义工具集

你可以在配置文件中将现有工具集组合成项目专属的工具集：


## 实例

然后在启动时指定：


## 实例


## 六种终端执行后端

终端工具集支持六种执行后端，决定了 Agent 的 Shell 命令在哪里运行，对应不同的隔离级别和「爆炸半径」。


### 切换后端


## 实例

Docker 后端完整配置示例：


## 实例

安全原则：local 后端让 Agent 拥有和你相同的文件系统权限——适合个人机器，不适合生产服务。docker 后端是最简单有效的隔离方式。


### 危险命令审批

默认情况下，Hermes 会在执行可能有破坏性的命令前请求确认：


## 实例

在会话中临时绕过审批（谨慎使用）：


## 实例


## MCP：连接外部工具生态

MCP（Model Context Protocol）让 Hermes 无需修改核心代码就能接入外部工具服务器——GitHub、数据库、文件系统、浏览器堆栈、内部 API 等。

标准安装已包含 MCP 支持，无需额外步骤。


### 两种 MCP 服务器类型

本地 stdio 服务器：以子进程形式在本地运行，通过标准输入/输出通信：


## 实例

适用场景：工具已本地安装，需要低延迟访问本地资源。

远程 HTTP 服务器：直接连接到远程 MCP 端点：


## 实例

适用场景：工具在远端托管，或组织内部有 MCP 接口。


### Nous 精选 MCP 目录

Hermes 内置了一个经 Nous 审核的 MCP 目录，一键安装：


## 实例

选择器会显示每个条目的当前状态：

```text
n8n          available              管理和检查 n8n 工作流
linear       enabled                Linear 问题/项目管理（远程 OAuth）
github       installed (disabled)   GitHub 仓库 + PR 工具
```

安装时会自动完成三个步骤：

- 提示配置 API Key 或引导 OAuth 登录
- 探测服务器暴露的工具列表
- 显示工具选择清单，让你决定开启哪些工具


### 工具过滤：只暴露你需要的

每个 MCP 服务器都支持精细的工具过滤，减少 Agent 可用的攻击面：


## 实例

过滤规则使用 MCP 原始工具名称（含连字符/点），不是 Hermes 注册后的下划线版本。


## 后续章节

- 每个 MCP 服务器生成独立工具集
- 实例
- 重新加载 MCP 配置
- 实例
- 编辑器集成（ACP）
- 实例
- 实例
- 语音模式
- 安装与启用
- 实例
- 实例
- TTS 提供商
- Tool Gateway（Nous Portal 订阅）
- 实例
- 工具安全：MCP 环境变量隔离
- 实例

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Hermes Agent 工具` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
