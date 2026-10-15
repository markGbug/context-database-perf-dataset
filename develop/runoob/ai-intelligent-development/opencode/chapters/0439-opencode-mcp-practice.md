# OpenCode：OpenCode MCP 服务器配置

- 来源：[OpenCode MCP 服务器配置](https://www.runoob.com/opencode/opencode-mcp.html)
- 分类：AI / 智能开发
- 技术：OpenCode
- 笔记类型：练习笔记
- 章节序号：0439

## 本章内容

MCP（Model Context Protocol，模型上下文协议）是一种开放协议，允许你为 OpenCode 接入外部工具和数据源。添加 MCP 服务器后，其提供的工具会自动与 OpenCode 的内置工具并列，LLM 可以在对话中直接调用它们。

OpenCode 同时支持两种 MCP 服务器：

- 本地（local）：在你的机器上通过命令行启动的 MCP 进程，适合本地工具和脚本
- 远程（remote）：通过 HTTPS 连接的远端 MCP 服务，适合云端服务和第三方平台

上下文消耗提醒：每个 MCP 服务器都会占用对话的上下文空间。启用的工具越多，每次对话消耗的 Token 越多，越容易触达模型的上下文上限。建议只启用当前任务实际需要的 MCP 服务器，用完即关。某些服务器（如 GitHub MCP）工具数量众多，Token 消耗尤其显著，使用时请格外注意。


## 基础配置结构

所有 MCP 服务器配置写在 opencode.json 的 mcp 字段下。每个服务器需要一个唯一的名称作为键名，该名称也可以在提示词中用来指定调用哪个 MCP：

```text
{
  "$schema": "https://opencode.ai/config.json",
  "mcp": {
    "my-mcp-server": {         // 服务器名称（自定义，全局唯一）
      "type": "local",         // 连接类型：local 或 remote
      // ...其他配置项
      "enabled": true          // 是否启用，默认为 true
    },
    "another-mcp-server": {    // 可同时配置多个 MCP 服务器
      "type": "remote",
      // ...
    }
  }
}
```

将 enabled 设置为 false 可以临时禁用某个服务器，而无需将其从配置文件中删除，方便按需开关：


## 实例


## 本地 MCP 服务器

本地 MCP 服务器通过在你的机器上运行一个命令进程来提供工具。将 type 设置为 "local"，并通过 command 指定启动命令：


## 实例


### 本地服务器配置项


### 示例：添加测试用 MCP 服务器

以下是添加官方测试用 MCP 服务器 @modelcontextprotocol/server-everything 的示例，可用于验证 MCP 功能是否正常工作：


## 实例

配置完成后，在提示词中加入服务器名称，即可让 LLM 调用该 MCP 的工具：

```text
use the mcp_everything tool to add the number 3 and 4
```


## 远程 MCP 服务器

远程 MCP 服务器通过 HTTPS 连接到云端服务。将 type 设置为 "remote"，并通过 url 指定服务器地址：


## 实例


### 远程服务器配置项


### 引用环境变量

在配置文件中，不应将 API 密钥等敏感信息直接写成明文。OpenCode 支持通过 {env:变量名} 语法在运行时读取系统环境变量：


## 实例


## OAuth 身份验证

OpenCode 内置了对远程 MCP 服务器的 OAuth 身份验证支持，整个流程几乎全自动，无需手动处理 Token。


### 自动认证流程

当服务器需要 OAuth 认证时，OpenCode 会自动完成以下步骤：

- 检测到服务器返回 401（未授权）响应
- 自动启动 OAuth 授权流程，打开浏览器引导你完成登录
- 在服务器支持的情况下，使用动态客户端注册（RFC 7591）自动注册应用
- 将获取到的 Token 安全存储在 ~/.local/share/opencode/mcp-auth.json 中
- 后续请求自动携带 Token，无需重复登录


### 1、自动 OAuth（无需额外配置）

对于大多数支持 OAuth 的 MCP 服务器，只需配置 url 即可，OpenCode 会在首次使用时自动引导你完成认证：


## 实例

也可以手动触发认证流程（例如 Token 过期后重新登录）：

```text
opencode mcp auth my-oauth-server
```


### 2、预注册客户端凭据

如果你已经从服务提供商处拿到了固定的客户端 ID 和密钥，可以直接在配置中指定，跳过动态注册步骤：


## 实例


### 3、禁用 OAuth（使用 API 密钥认证）

如果服务器使用 API 密钥而非 OAuth 认证，可以将 oauth 设为 false 禁用自动 OAuth 检测，改用 headers 传递密钥：


## 实例


### OAuth 配置项


### 认证管理命令

OpenCode 提供了一组命令行工具用于管理 MCP 的认证状态：

```text
# 对指定 MCP 服务器进行身份验证（会打开浏览器完成 OAuth 授权）
opencode mcp auth my-oauth-server

# 列出所有已配置的 MCP 服务器及其当前认证状态
opencode mcp list

# 删除指定服务器已存储的凭据（下次使用时需要重新登录）
opencode mcp logout my-oauth-server

# 调试指定服务器的连接和 OAuth 流程（显示认证状态、测试连接、执行 OAuth 发现流程）
opencode mcp debug my-oauth-server

# 查看所有支持 OAuth 的服务器的认证状态
opencode mcp auth list
```


## 覆盖远程默认配置

组织可以通过 .well-known/opencode 端点为成员提供预置的 MCP 服务器配置，这些服务器可能默认处于禁用状态。如果你需要启用其中某个服务器，在本地配置中添加同名条目并设置 enabled: true 即可，本地配置会覆盖远程默认值：


## 实例


## 后续章节

- 工具管理
- 1、全局禁用指定 MCP 的工具
- 实例
- 2、使用 Glob 模式批量禁用
- 实例
- 3、按代理启用特定 MCP 工具
- 实例
- Glob 模式规则
- 配置示例
- Sentry
- 实例
- Context7
- 实例
- 实例
- Grep by Vercel
- 实例

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `OpenCode MCP 服务器配置` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
