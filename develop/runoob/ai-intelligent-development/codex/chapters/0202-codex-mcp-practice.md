# Codex：Codex MCP 服务器配置

- 来源：[Codex MCP](https://www.runoob.com/codex/codex-mcp.html)
- 分类：AI / 智能开发
- 技术：Codex
- 笔记类型：练习笔记
- 章节序号：0202

## 本章内容

MCP（Model Context Protocol，模型上下文协议）允许 Codex 与外部工具和服务集成。

本节详细介绍如何配置和使用 MCP 服务器。


## 什么是 MCP？

MCP 是一个开放协议，允许 AI 模型与外部工具和服务进行标准化交互。通过 MCP 服务器，你可以扩展 Codex 的能力：

- 连接文件系统
- 访问数据库
- 集成项目管理工具
- 调用外部 API


## MCP 基础配置


### Codex 配置菜单

通过设置菜单可以管理或添加 MCP 服务：

连接至自定义 MCP:


### 配置文件位置

MCP 服务器在 ~/.codex/config.toml 的 mcp_servers 部分配置。


### stdio 类型服务器


## 配置 stdio MCP 服务器


### HTTP 类型服务器


## 配置 HTTP MCP 服务器


## MCP 工具配置


### 限制可用工具

你可以限制 MCP 服务器暴露的工具：


## 工具白名单/黑名单


### 超时配置


## 配置超时


## MCP 认证配置


### OAuth 配置


## 配置 OAuth


### HTTP 头配置


## 配置 HTTP 头


### OAuth 回调配置


## 配置 OAuth 回调


## MCP 工具权限

你可以为每个 MCP 服务器的工具单独设置权限：


## 配置工具权限


## 常用 MCP 服务器


### 文件系统服务器


## 后续章节

- 文件系统 MCP
- GitHub 服务器
- GitHub MCP
- PostgreSQL 服务器
- PostgreSQL MCP
- 常用 MCP 服务器
- 故障排除
- 服务器启动失败
- 工具调用超时
- 认证问题
- 常见问题
- Q: MCP 服务器无法启动？
- Q: 工具权限在哪里配置？
- Q: 如何禁用某个 MCP 服务器？
- Q: 支持多少个 MCP 服务器？

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Codex MCP` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
