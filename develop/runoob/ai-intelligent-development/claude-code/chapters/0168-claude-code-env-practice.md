# Claude Code：Claude Code 环境变量

- 来源：[Claude Code 环境变量](https://www.runoob.com/claude-code/claude-code-env.html)
- 分类：AI / 智能开发
- 技术：Claude Code
- 笔记类型：练习笔记
- 章节序号：0168

## 本章内容

环境变量是控制 Claude Code 行为的重要方式，无需编辑配置文件即可灵活调整各项设置。本章详细介绍 Claude Code 支持的所有环境变量、它们的用途、配置方式以及常见使用场景。


## 环境变量概述

Claude Code 使用环境变量来控制行为，这些变量可以通过以下方式设置：

- 直接在 shell 中 export
- 在 ~/.claude/settings.json 的 env 字段中配置
- 在项目级 .claude/settings.json 中配置
- 通过 IDE 插件的设置界面配置

环境变量优先级从高到低：命令行 > 项目级 settings.json > 用户级 settings.json > shell 环境变量。在 settings.json 中配置的变量会自动传递给 Claude 进程。


## 认证相关变量


### 配置示例


## 实例


## 实例


## 模型配置变量


### 使用场景

子代理默认继承主对话的模型。通过 CLAUDE_CODE_SUBAGENT_MODEL 可以统一设置，将简单任务交给 Haiku，将复杂分析交给 Sonnet，从而优化成本：


## 实例


## 工具与命令变量


## 权限与安全变量


### 权限模式详解

- default：正常权限提示，每次操作前询问
- acceptEdits：自动接受文件编辑，无需确认
- dontAsk：自动拒绝未授权操作，不中断执行
- bypassPermissions：跳过所有权限检查（仅限完全可信环境）
- plan：只读规划模式，不执行写操作


## 实例


## 日志与调试变量


## 会话与历史变量


## MCP 相关变量

当 Claude Code 执行 MCP 工具时，会设置以下环境变量：


## 工作流相关变量


## GitHub Actions 专用变量


## settings.json 配置方式

所有环境变量都可以在 settings.json 中配置，这种方式更加声明式和可移植：


## 实例


### VS Code 插件配置

在 VS Code 中使用 Claude Code 插件时，可以通过 environmentVariables 设置：


## 实例


## 常见使用场景


### 场景一：使用代理或自定义 API 端点


## 实例


## 后续章节

- 场景二：优化成本配置
- 实例
- 场景三：CI/CD 环境安全配置
- 实例
- 场景四：Windows PowerShell 环境
- 实例
- 优先级与覆盖
- 查看当前配置
- 最佳实践
- 1、敏感信息处理
- 2、按环境配置
- 3、集中管理
- 常见问题

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Claude Code 环境变量` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
