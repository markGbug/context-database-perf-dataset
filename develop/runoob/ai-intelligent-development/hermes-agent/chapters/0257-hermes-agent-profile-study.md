# Hermes Agent：Profile 系统与发行版

- 来源：[Hermes Agent Profile](https://www.runoob.com/hermes-agent/hermes-agent-profile.html)
- 分类：AI / 智能开发
- 技术：Hermes Agent
- 笔记类型：学习笔记
- 章节序号：0257

## 本章内容

我们可以使用 Hermes 创建多个独立 Agent——一个专门写代码，一个负责运维，一个做研究。

本章介绍 Profile 系统如何在一台机器上运行多个完全隔离的 Agent 实例，以及如何将整个 Agent 打包为发行版共享给他人。


## Profile 系统：一台机器，多个独立 Agent


### 什么是 Profile

Profile 是一个独立的 Hermes 主目录。每个 Profile 拥有自己完全隔离的配置和数据：

```html
~/.hermes/profiles/<name>/
├── config.yaml     # 模型、工具、终端后端等所有设置
├── .env            # API Key、Bot Token（各档案各自独立）
├── SOUL.md         # Agent 人格与身份设定
├── memories/       # 独立的持久记忆（MEMORY.md、USER.md）
├── skills/         # 独立的技能目录
├── cron/           # 独立的定时任务
└── state.db        # 独立的会话历史数据库
```

关键设计：创建 Profile 后，它自动成为一个独立命令。创建名为 coder 的 Profile，你立即拥有 coder chat、coder setup、coder gateway start 等所有子命令——就像装了一个完全独立的 Hermes 实例。


### 快速上手

三步创建一个独立的编码助手：


## 实例


### 三种创建模式


## 实例


### 切换和使用 Profile


## 实例

判断当前在哪个 Profile：

- 命令提示符显示 coder ❯（而非普通的 ❯）
- 启动横幅显示 Profile: coder
- 运行 hermes profile 查看当前 Profile 名称、路径、模型、网关状态


### Profile 与工作目录、沙箱的区别

这是最容易混淆的三个概念：

Profile 不是沙箱——默认 local 后端下，Agent 仍然拥有和你相同的文件系统权限。如果需要限制访问范围，切换终端后端（见第 05 章）。

让某个 Profile 固定从特定目录开始工作：


## 实例


### 多 Profile 网关：每个 Agent 连接不同平台

每个 Profile 运行自己独立的网关进程，使用各自的 Bot Token：


## 实例

安全防护：如果两个 Profile 意外使用了同一个 Bot Token，第二个网关会立即报错并指出冲突的 Profile 名称，不会发生静默冲突。


### Profile 管理命令


## 实例

不能删除默认 Profile（~/.hermes）。要完全卸载，使用 hermes uninstall。


## Profile 发行版：把整个 Agent 共享给他人

Profile Distribution（发行版）将一个完整的 Hermes Agent——人格设定、技能、定时任务、MCP 连接、配置——打包成一个 Git 仓库。

任何人都可以一条命令安装整个 Agent，并在保留自己的记忆、会话和 API Key 的同时接收你的更新。


### 发行版 vs Profile 备份


### 发行版适合场景

- 向团队分发专用 Agent（合规监控、代码审查、研究助手）
- 向多台机器部署同一个 Agent，不想手动复制文件
- 持续迭代 Agent，让接收方通过一条命令拿到最新版本
- 把 Agent 作为产品分发给社区


### 创建和发布发行版

第一步：在已有的 Profile 中添加 distribution.yaml：


## 实例

第二步：推送到 Git 仓库：


## 实例

.env 和 auth.json 被自动排除——API Key 不会进入仓库。记忆和会话历史也不会被包含。


### 安装和更新发行版


## 实例


## 常用命令速查


## 实例


## 复习重点

- 能说明 `Hermes Agent Profile` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
