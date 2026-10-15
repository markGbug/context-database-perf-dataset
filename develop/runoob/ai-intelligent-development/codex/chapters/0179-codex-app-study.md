# Codex：Codex 桌面应用

- 来源：[Codex 桌面应用](https://www.runoob.com/codex/codex-app.html)
- 分类：AI / 智能开发
- 技术：Codex
- 笔记类型：学习笔记
- 章节序号：0179

## 本章内容

目前 Codex 主流有三种使用方式：

Codex App 是官方推荐的桌面客户端，提供完整功能和流畅的多项目并行体验。


## 下载与安装

Codex App 支持 macOS（Apple Silicon）和 Windows。

下载地址：https://chatgpt.com/codex


## 首次使用

安装完成后，按以下步骤开始：

1、打开 Codex App

2、使用 ChatGPT 账号或 OpenAI API Key 登录

如果使用 API Key 登录，部分云端功能可能不可用。

3、登录成功后界面如下：

我们刚使用可以先关注对话和项目就好了，对话就跟普通的 ChatGPT 的网页版一样进行聊天就可以了。

项目（ Project ）我们可以把它理解成：ChatGPT 的聊天 + IDE 的工程目录 + AI Agent 的长期记忆 的组合体。

项目（ Project ） 会绑定到你电脑上的一个文件夹，Codex 只会在这个目录内工作。

我这里选择 "添加新项目"，把 codex-runoob-test 添加：

4、发送第一条 Prompt 开始使用


## 界面结构

Codex App 主要包含以下区域：

导航按钮

左上角返回/前进箭头

对话栏右侧漏斗图标


## 三种运行模式

每个项目可以选择三种运行模式：


### 模式选择

在创建新项目时，在输入框下方选择模式：

- Local：直接在当前目录工作，变更立即可见
- Worktree：创建独立分支，完成后可合并到 Local
- Cloud：任务在云端运行，结果通过 PR 或报告呈现

Worktree 模式使用 Git worktree 技术，允许同时在不同分支工作。


## Review 模式

Review 模式让你查看和审批 Codex 所做的更改。


### 审查面板功能


### 切换审查视图

审查面板支持两种视图：

- 所有更改：显示项目的 Git 状态，包括非 Codex 的更改
- Last turn 更改：只显示最近一轮 Codex 的更改


## 审查操作


## Automations（自动化）

Automations 让你安排 Codex 定期在后台运行任务。


### 使用前提

- Codex App 正在运行
- 选择的项目在磁盘上可用


### 创建自动化

- 打开侧边栏 Automations 面板
- 点击 "New Automation"
- 配置触发频率和任务描述
- 设置沙箱模式


### 自动化示例

自动化任务结果会添加到 Triage 收件箱，无结果时自动归档。


## Worktrees 管理

Codex App 内置 Git worktree 支持。


### Worktree 优势

- 并行处理多个任务而不互相干扰
- 保持主分支干净
- 后台运行任务时专注前台工作


### Handoff 流程

Handoff 允许在 Local 和 Worktree 之间切换：

- 在 Worktree 中完成任务
- 创建 commit 和 PR
- 选择 Handoff 到 Local 继续测试

Worktree 只继承 Git 中的文件，.gitignore 中的文件不会随项目移动。


## 本地环境配置

通过 Local Environments 定义 worktree 的设置脚本和常用操作。


### 设置脚本

创建新 worktree 时自动运行的脚本：


## 设置脚本示例


### Actions（操作）

定义常用任务，在顶部操作栏快速访问：


## 快捷键


## 常见问题


### Q: App 与 CLI/IDE 如何同步？

当在同一项目中使用 App 和 IDE 扩展时，它们会自动同步 Auto Context 和活跃项目。


### Q: 如何找到归档的项目？

在 Settings 中查看 Archived Threads，选择 Unarchive 恢复。


## 后续章节

- Q: Worktree 代码与本地不同？
- Q: App 和 CLI 版本不同导致功能差异？

## 复习重点

- 能说明 `Codex 桌面应用` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
