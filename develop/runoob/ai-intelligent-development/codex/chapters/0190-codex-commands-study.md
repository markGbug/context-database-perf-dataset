# Codex：Codex 速查表

- 来源：[Codex 速查表](https://www.runoob.com/codex/codex-commands.html)
- 分类：AI / 智能开发
- 技术：Codex
- 笔记类型：学习笔记
- 章节序号：0190

## 本章内容

本附录包含命令速查表、常见问题和版本更新信息。


## 命令速查表


### CLI 基础命令


### 斜杠命令


### CLI 参数


### Shell 命令执行


## 配置文件路径


### 配置文件位置


### 技能目录


## 快捷键


### CLI 快捷键


### App 快捷键


## 常见问题


### 安装与认证

使用 npm 或 Homebrew：

```text
npm install -g @openai/codex
# 或
brew install codex
```

运行 codex 命令会自动打开浏览器进行认证，使用 ChatGPT 账号或 API Key 登录。

Windows 原生支持为实验性，推荐使用 WSL2 获得最佳体验。


### 使用问题

使用 /status 命令查看当前会话的配置和状态。

使用 codex --no-alt-screen 或配置 alternate_screen = "never"。

确保 PATH 包含 npm 全局安装目录，或使用 Homebrew 安装。

日志位于 ~/.codex/log/ 目录。


### 功能问题

exec 单次执行后退出，适合自动化脚本；交互模式持续对话，适合日常开发。

使用 /resume 命令或 codex resume --last。

可以，设置 sandbox: workspace-write。

使用 CODEX_API_KEY 环境变量，作为 Secrets 存储。


### 安全问题

使用 read-only 或 workspace-write 沙箱模式，配置 Rules 禁止危险命令。

full-auto 会自动执行所有操作，包括删除文件，请谨慎使用。

使用 Secrets 存储，仅在设置脚本中可用。


## 版本更新


### 近期更新


### 更新 CLI


## 更新命令


## 相关资源


### 官方资源


### 教程系列


## 术语表


## 后续章节

- 反馈与支持
- 获取帮助
- 报告问题

## 复习重点

- 能说明 `Codex 速查表` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
