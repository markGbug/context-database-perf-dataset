# Codex：Codex 命令行工具

- 来源：[Codex 命令行工具](https://www.runoob.com/codex/codex-cli.html)
- 分类：AI / 智能开发
- 技术：Codex
- 笔记类型：学习笔记
- 章节序号：0192

## 本章内容

Codex CLI 是官方命令行工具，用 Rust 编写，轻量高效，适合终端爱好者。


## 安装 CLI

Codex CLI 支持 macOS、Linux 和 Windows（实验性）。


### npm 安装


## npm 全局安装


### Homebrew 安装


## Homebrew 安装


### 更新 CLI


## 更新版本


## 首次使用

首次运行 Codex 会引导你完成认证：


## 启动 Codex

Codex 会打开浏览器进行认证：

- 使用 ChatGPT 账号登录
- 或使用 OpenAI API Key
- 授权后返回终端继续


## 交互式 TUI

CLI 默认进入终端用户界面（TUI）模式，提供沉浸式体验。


### TUI 界面区域


### TUI 模式设置


## TUI 配置

替代屏幕模式让 Codex 使用独立屏幕，退出时恢复原终端状态。


## Approval 模式

Approval 模式控制 Codex 执行操作前的确认行为。


### 四种模式


## 设置 Approval 模式

full-auto 模式下 Codex 会自动执行所有操作，包括删除文件，请谨慎使用。


## Sandbox 模式

Sandbox 模式限制 Codex 的文件和命令访问范围。


## 设置 Sandbox 模式


## 斜杠命令

CLI 提供丰富的斜杠命令：


### 命令使用示例


## 斜杠命令


## Shell 命令执行

在 CLI 中直接执行 Shell 命令：


## 执行命令


### 命令确认

危险命令需要确认：

- 删除文件（rm）
- 终止进程（kill）
- 修改系统配置


## 后续章节

- 图片输入
- 附加图片
- 图片用途
- 非交互模式（exec）
- exec 命令
- exec 常用参数
- 快捷键
- 常见问题
- Q: Windows 支持情况？
- Q: 如何禁用替代屏幕？
- Q: 命令找不到？
- Q: 如何查看详细日志？

## 复习重点

- 能说明 `Codex 命令行工具` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
