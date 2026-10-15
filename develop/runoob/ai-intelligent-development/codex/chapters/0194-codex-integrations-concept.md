# Codex：Codex 集成与连接

- 来源：[Codex 集成与连接](https://www.runoob.com/codex/codex-integrations.html)
- 分类：AI / 智能开发
- 技术：Codex
- 笔记类型：概念卡
- 章节序号：0194

## 本章内容

Codex 支持与多种开发工具和平台集成，扩展其能力和应用场景。


## GitHub 集成

Codex 与 GitHub 深度集成，可以在 PR 中直接进行代码审查。


### 功能概览


### 设置 GitHub 集成

- 配置 Codex Cloud
- 前往设置页面开启 Code Review
- 授权访问你的 GitHub 仓库
- 选择要启用的仓库


### 请求审查


## PR 中使用


### Codex 响应

Codex 会：

- 对 PR 反应 👀
- 分析代码变更
- 发布审查意见
- 标记发现的问题（默认 P0 和 P1）


### 审查指南定制

在仓库的 AGENTS.md 中定义审查规则：


## 审查指南

Codex 默认只标记 P0 和 P1 问题，可在 AGENTS.md 中调整。


## Slack 集成

通过 Slack 集成，团队成员可以在频道中直接使用 Codex。


### 设置 Slack 集成

- 前往 Codex 设置页面
- 找到 Integrations 部分
- 添加 Slack 应用
- 授权访问 Slack 工作区


### 使用方式


## Slack 中使用


### 适用场景

- 团队协作讨论时快速获取 AI 辅助
- 远程团队成员委派任务
- 异步工作场景


## Linear 集成

Linear 是项目管理工具，Codex 可以与之联动处理 Issue。


### 设置 Linear 集成

- 前往 Codex 设置页面
- 添加 Linear 集成
- 授权访问 Linear 工作区
- 配置 Issue 处理规则


### 使用场景


## MCP（Model Context Protocol）

MCP 是连接 Codex 与外部工具的协议。


### MCP 概述

- STDIO 服务器：本地进程，通过标准输入输出通信
- HTTP 服务器：远程服务器，通过 HTTP API 通信


### 配置 MCP 服务器


## MCP 配置


### 常用 MCP 服务器


### MCP 工具权限


## 工具权限配置


## OAuth 认证配置

某些 MCP 服务器需要 OAuth 认证：


## 后续章节

- OAuth 配置
- 常见问题
- Q: GitHub 集成需要什么计划？
- Q: 可以限制 Codex 访问的仓库吗？
- Q: MCP 服务器如何安装？
- Q: 支持其他集成吗？

## 记忆卡片

- 一句话定义：`Codex 集成与连接` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
