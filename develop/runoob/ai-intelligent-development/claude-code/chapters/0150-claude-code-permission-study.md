# Claude Code：Claude Code 权限配置

- 来源：[Claude Code 权限配置](https://www.runoob.com/claude-code/claude-code-permission.html)
- 分类：AI / 智能开发
- 技术：Claude Code
- 笔记类型：学习笔记
- 章节序号：0150

## 本章内容

Claude Code 使用分层权限系统来平衡功能和安全性，支持细粒度权限规则、权限模式和沙箱策略来控制 Claude 可以访问和执行的操作。合理配置权限，既能让 AI 高效完成任务，又能防止误操作破坏代码或泄露敏感文件。

从 Claude Code v1.1.1 开始，推荐使用新的权限配置方式。旧的 tools 布尔配置仍被支持，但建议迁移到新的权限规则语法。


## 权限系统概述

Claude Code 的权限系统将操作分为三类，不同类型的操作有不同的默认权限策略：


## 三种权限动作

每条权限规则最终会解析为以下三种动作之一：

规则优先级：deny → ask → allow。 第一个匹配的规则获胜，因此 deny 规则始终优先于 allow 和 ask。


## 权限模式

权限模式控制 Claude 是否在执行操作前询问用户。不同的任务需要不同级别的自主权。


### 1、六种可用模式

受保护目录说明：无论模式如何，对 .git、.vscode、.idea、.husky 和 .claude 的写入永远不会自动批准，除了 .claude/commands、.claude/agents 和 .claude/skills。


### 2、切换权限模式

会话期间切换：按 Shift+Tab 循环切换 default → acceptEdits → plan → auto

启动时指定模式：

```text
claude --permission-mode plan
claude --permission-mode bypassPermissions
```

设置为默认模式（settings.json）：


## 实例


## 权限规则语法


### 1、基本格式

权限规则遵循格式 Tool 或 Tool(specifier)：


## 实例


### 2、匹配所有工具使用

不带说明符的规则匹配该工具的所有使用：

Bash(*) 等同于 Bash，两者效果相同。


### 3、使用说明符进行细粒度控制


## 实例


### 4、通配符模式

Bash 规则支持带有 * 的 glob 模式，通配符可以出现在命令中的任何位置：


## 实例

注意通配符前的空格：Bash(ls *) 匹配 ls -la 但不匹配 lsof；Bash(ls*) 匹配两者。


## 工具特定的权限规则


### 1、Bash 命令

重要限制：尝试约束命令参数的 Bash 权限模式可能很脆弱。URL 前的选项、不同的协议、重定向、变量、额外空格都可能导致不匹配。建议使用 WebFetch 工具配合 domain: 权限进行 URL 过滤。


### 2、Read 和 Edit（文件操作）

文件路径支持多种路径前缀模式：


## 实例

注意：Read 和 Edit deny 规则不适用于 Bash 子进程中的 cat .env。要获得 OS 级别强制执行，需启用沙箱。


### 3、WebFetch（网络请求）


## 实例


### 4、MCP（模型上下文协议）


## 实例


### 5、Agent（子代理）


## 实例


## 后续章节

- 工作目录配置
- 1、扩展访问方式
- 实例
- 2、例外情况
- 自动模式（Auto Mode）
- 1、可用条件
- 2、工作原理
- 3、分类器默认行为
- 4、自动模式配置
- 实例
- 5、回退机制
- 沙箱与权限的关系
- 1、启用沙箱
- 2、配置沙箱
- 实例
- 使用 Hooks 扩展权限

## 复习重点

- 能说明 `Claude Code 权限配置` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
