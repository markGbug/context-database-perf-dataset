# Codex：Codex GitHub 集成

- 来源：[Codex GitHub 集成](https://www.runoob.com/codex/codex-github.html)
- 分类：AI / 智能开发
- 技术：Codex
- 笔记类型：练习笔记
- 章节序号：0206

## 本章内容

Codex 与 GitHub 深度集成，可以在拉取请求中直接进行代码审查。本节详细介绍如何配置和使用 GitHub 集成。


## 功能概述

通过 GitHub 集成，你可以：

- 在 PR 评论中直接请求 Codex 审查
- 自动审查每个拉取请求
- 让 Codex 修复 CI 失败问题
- 查看代码变更并提供建议


## 设置 GitHub 集成


### 前提条件

- Codex Cloud 订阅
- GitHub 账号


### 配置步骤

- 设置 Codex Cloud
- 前往 Codex 设置
- 为仓库开启 Code review 功能
- 授权 Codex 访问你的仓库


## 请求代码审查


### 手动触发审查

在拉取请求评论中提及 @codex review：


## 请求审查


### Codex 响应

Codex 会：

- 对 PR 做出反应（👀）
- 分析代码变更
- 发布审查意见
- 标记发现的问题（P0 和 P1）


### 自动审查

在设置中开启 Automatic reviews：

- 前往 Codex 设置
- 开启 Automatic reviews
- 新 PR 打开时自动发布审查


## 自定义审查内容


### 设置仓库审查指南

在仓库的 AGENTS.md 中添加审查指南：


## 添加审查指南


### 模块特定规则

在子目录放置更具体的审查规则：


## 模块特定规则


### 一次性审查重点

在评论中指定审查重点：


## 指定审查重点


## 给 Codex 其他任务

在评论中提及 @codex（不是 review）会启动云任务：


## 其他任务


### GitHub Actions 集成

你也可以在 GitHub Actions 中使用 Codex：


## GitHub Actions 工作流


## 最佳实践


### 审查指南

- 在 AGENTS.md 中明确定义审查标准
- 为不同模块设置特定规则
- 指定问题优先级（P0/P1）


### 自动化

- 为常规 PR 开启自动审查
- 对于大型变更使用手动触发
- 结合自动化工作流使用


## 常见问题


## 后续章节

- Q: Codex 审查需要付费吗？
- Q: Codex 能访问私有仓库吗？
- Q: 可以限制 Codex 审查的仓库吗？
- Q: Codex 标记哪些级别的问题？

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Codex GitHub 集成` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
