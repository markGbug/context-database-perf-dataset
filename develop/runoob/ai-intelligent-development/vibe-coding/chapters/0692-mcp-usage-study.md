# Vibe Coding：MCP 入门教程

- 来源：[MCP 入门教程](https://www.runoob.com/vibe-coding/mcp-usage.html)
- 分类：AI / 智能开发
- 技术：Vibe Coding
- 笔记类型：学习笔记
- 章节序号：0692

## 本章内容

MCP 英文全称 Model Context Protocol（模型上下文协议），是一个开放标准协议，用于标准化 AI 应用与外部工具、数据源之间的连接方式。

MCP 就像 USB-C 一样，可以让不同设备能够通过相同的接口连接在一起。

在 MCP 出现之前，每接入一个新工具（如 GitHub、Slack、数据库），每个 AI 应用都要单独写一套集成代码，形成 N × M 集成难题（N 个 AI 应用 × M 个工具 = N×M 套代码）。

有了 MCP 之后，工具方只需按标准做一个 MCP Server，任何支持 MCP 的 AI 应用都能直接使用，变成 1 套 Server + 兼容所有 Host。

下图直观展示了传统 N×M 集成与 MCP 标准化集成的区别：

MCP 已于 2025 年 12 月由 Anthropic 捐赠给 Linux Foundation 下的 Agentic AI Foundation（AAIF），成为行业共有的开放标准。OpenAI、Block 等厂商共同参与治理。


### 发展时间线


## 核心架构：Host / Client / Server

MCP 借鉴了 LSP（Language Server Protocol，编辑器统一支持编程语言的协议）的设计思路，定义了三种角色：

三层架构关系如下图所示：

底层通信统一使用 JSON-RPC 2.0 消息格式，保证了不同角色之间交互的标准化。


## MCP 通信流程详解

以"用户让 AI 查天气"为例，一次完整的工具调用过程如下：

流程分为七个步骤：

- 用户提问：用户在 Host（如 Claude Code）中输入"帮我查一下北京天气"。
- 模型判断：Host 内置的大模型分析问题，判断需要调用天气查询工具，将调用意图发送给 Client。
- 协议翻译：Client 将工具调用请求转换为 JSON-RPC 2.0 格式消息，发送给对应的 Server。
- Server 执行：Server 收到请求后执行实际操作（如调用天气 API、查询数据库）。
- 返回结果：Server 将结果以 JSON-RPC 格式返回给 Client。
- 交回模型：Client 将结果传回 Host，供模型整合到回答中。
- 回答用户：模型将工具返回的数据与自然语言整合，输出最终回答。

在整个流程中，Server 完全不知道大模型的存在——它只处理 JSON-RPC 消息，这是 MCP 实现模型无关的关键设计。


## 三大核心原语

一个 MCP Server 可以对外暴露三类能力，称为"原语"（Primitive）：

此外还有两个进阶机制：

- Sampling（采样）：Server 反过来可以请求 Host 的模型帮它生成内容，实现角色互换。
- Elicitation（信息征询）：Server 执行中途发现信息不足，可以主动向用户追问，例如"要按哪个日期筛选？"

刚开始可以先重点关注 Tools 和 Resources 即可，Prompts、Sampling、Elicitation 在后期使用时再了解也不迟。


## 传输方式

MCP 支持两种传输方式，适用于不同场景：

个人学习和本地开发使用 stdio 即可。

企业级、需要多人共享的场景则使用 Streamable HTTP。

本教程的演示案例均采用 stdio 方式。


## 安全须知

MCP 赋予了 AI 执行代码、访问真实系统的能力，因此安全规范尤为重要：

- 工具描述本身不可信：除非来自可信 Server，功能说明可能被恶意篡改（提示词注入风险），Host 应对工具描述保持警惕。
- 必须显式获得用户同意：不能静默执行敏感操作，每次工具调用都应经过用户确认。
- 生产环境加强防护：Server 应作为 OAuth 资源服务器部署，配合 TLS 加密、访问控制、日志审计。
- 第三方 Server 需审核：使用前确认来源可信，必要时做沙箱隔离。


## 实战演示：用 Claude Code 接入 MCP Server

下面通过两个完整案例，展示如何编写 MCP Server 并接入 Claude Code 使用。

第一个案例使用 Python 编写天气查询服务，第二个案例使用 Node.js/TypeScript 编写待办事项管理。


### 案例一：Python 天气查询 Server

目标：编写一个提供天气查询工具的 MCP Server，通过 Claude Code 调用。

```text
pip install mcp httpx
```

需要安装两个 Python 包：mcp 是 MCP 官方 Python SDK，httpx 用于发起 HTTP 请求调用天气 API。

创建文件 weather_server.py：


## 实例

代码说明：

- @mcp.tool()：将函数注册为 Tool，模型的 docstring 会自动作为工具说明提供给大模型，帮助模型判断何时该调用。
- @mcp.resource()：将函数注册为 Resource，供模型按需读取，不涉及"执行"，只是"查阅"。
- mcp.run(transport="stdio")：通过标准输入输出与 Host 通信，是本地工具最常用的方式。

在接入 Claude Code 之前，先用 MCP 官方 Inspector 工具调试 Server，确认它正常工作：

```text
npx @modelcontextprotocol/inspector python weather_server.py
```

运行后会自动打开一个网页调试界面，可以看到 Server 暴露了哪些 Tool 和 Resource，并手动调用测试。

建议每次都先走一遍 Inspector 调试流程，在接入真实的 AI 助手之前排查代码问题，能节省大量排查时间。

方式一：直接让 AI 添加

我们可以直接启动 Claude：

```text
claude
```

输入以下信息，让 Claude 自己帮我配置添加：

```text
添加 @weather_server.py 这个 MCP 服务
```

这种最简单，输入提示信息，配置依赖都能自动完成。

可以看到在当前目录的 .mcp.json 文件中自动生成了配置信息：

配置完成后，在 Claude Code 中直接提问：

```text
帮我查一下北京现在的天气
```

如果喜欢自己折腾，也可以使用命令式添加和文件配置。

方式二：命令行添加

注意命令与文件的路径，要自己修改：

```text
claude mcp add weather python /Users/runoob/runoob-test/weather_server.py
```

这条命令的含义：

- claude mcp add：Claude Code 的 MCP 管理子命令。
- weather：给这个 MCP Server 起一个名字，后续用 claude mcp list 可以看到。
- python：启动 Server 的命令。
- /Users/.../weather_server.py：Server 脚本的绝对路径。

添加成功后，可以用以下命令查看已连接的 MCP Server：

```text
claude mcp list
```


### 案例二：Node.js/TypeScript 待办事项 Server

如果你更熟悉 JavaScript/TypeScript 生态，以下是 Node.js 版本的 MCP Server 示例。

```text
npm install @modelcontextprotocol/sdk zod
```

创建文件 todo_server.ts：


## 实例

接入 Claude Code 的方式与 Python 版本完全一致。

我们可以直接启动 Claude：

```text
claude
```

输入以下信息，让 Claude 自己帮我配置添加：

```text
添加 @todo_server.ts 这个 MCP 服务
```

然后在对话中说 "帮我添加一条待办：购买 runoob 教程"，Claude Code 就会调用 add_todo 工具。


## 现有生态：不必什么都自己写

MCP 发布以来，社区已发布超过 500 个公开 Server，覆盖了绝大多数常见场景：

官方 SDK 覆盖以下编程语言：TypeScript、Python、C#、Java、Swift。

实际开发中，大部分场景直接找现成 Server 使用即可。只有在连接公司内部系统或私有数据库时，才需要自己编写 MCP Server。


## 常见问题


## 参考资料

- 官方文档：https://modelcontextprotocol.io
- 官方规范：https://modelcontextprotocol.io/specification
- 官方 GitHub（含各语言 SDK 与参考实现）：https://github.com/modelcontextprotocol
- MCP 协议：https://www.runoob.com/np/mcp-protocol.html
- 调试工具 Inspector：npx @modelcontextprotocol/inspector


## 复习重点

- 能说明 `MCP 入门教程` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
