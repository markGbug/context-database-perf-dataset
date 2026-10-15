# OpenCode：OpenCode LSP 服务器配置

- 来源：[OpenCode LSP 服务器配置](https://www.runoob.com/opencode/opencode-lsp.html)
- 分类：AI / 智能开发
- 技术：OpenCode
- 笔记类型：学习笔记
- 章节序号：0438

## 本章内容

OpenCode 与语言服务器协议（LSP，Language Server Protocol）深度集成，通过 LSP 服务器为 LLM 提供代码诊断、错误提示等实时反馈，帮助 AI 更准确地理解和操作你的代码库。

简单来说，LSP 服务器就是让 OpenCode 具备"读懂代码"能力的组件，类似于 VS Code 中提供代码补全、错误提示的插件。当文件中出现语法错误或类型不匹配时，LSP 服务器会将这些诊断信息反馈给 LLM，从而做出更准确的修改。


## 工作原理

OpenCode 的 LSP 集成是全自动的，无需手动干预。当 OpenCode 打开一个文件时，会依次执行以下流程：

```text
打开文件
  │
  ▼
读取文件扩展名（如 .ts、.py、.go）
  │
  ▼
与所有已启用的 LSP 服务器进行匹配
  │
  ├── 匹配成功且服务器已运行 → 直接使用
  │
  └── 匹配成功但服务器未运行 → 自动启动对应 LSP 服务器
```

整个过程在后台静默完成，LSP 服务器启动后会持续为当前会话提供诊断信息。


## 内置 LSP 服务器

OpenCode 内置了主流语言的 LSP 服务器支持，当检测到对应文件扩展名且满足相应要求时，LSP 服务器会自动启用，大部分情况下无需任何配置。


## 配置 LSP 服务器

LSP 相关配置写在 opencode.json 的 lsp 字段中。大多数情况下无需任何配置，LSP 会自动启用；但在需要定制行为时，每个 LSP 服务器支持以下配置项：


### 1、设置环境变量（env）

使用 env 属性在启动 LSP 服务器时注入环境变量。常用于开启调试日志或指定运行时所需的路径：


## 实例


### 2、设置初始化选项（initialization）

initialization 用于向 LSP 服务器传递服务器特定的配置，这些选项在 LSP 握手（initialize 请求）阶段一次性发送，影响该服务器此后的所有行为：


## 实例


## 禁用 LSP 服务器


### 1、禁用所有 LSP 服务器

如果完全不需要 LSP 功能，可以将 lsp 整体设置为 false，一次性关闭所有 LSP 服务器：


## 实例


### 2、禁用特定 LSP 服务器

如果只想关闭某一个 LSP 服务器而保留其他的，对该服务器单独设置 disabled: true：


## 实例


## 添加自定义 LSP 服务器

如果你使用的语言不在内置支持列表中，可以通过指定 command 和 extensions 来手动添加任意 LSP 服务器，只要该服务器遵循标准的 LSP 协议并支持 --stdio 模式（通过标准输入输出通信）即可：


## 实例

还可以同时为自定义 LSP 服务器配置环境变量和初始化选项，与内置服务器写法完全一致：


## 实例


## 补充说明


### PHP Intelephense 许可证

PHP Intelephense 提供免费版和付费高级版。高级版通过许可证密钥解锁，包含导入整理、代码折叠、调用层级查看等增强功能。如果你购买了许可证，将密钥单独写入以下路径的文本文件中即可自动激活，无需任何额外配置：

许可证文件中只需包含许可证密钥本身，不要添加任何其他内容（包括多余的空格或换行符），否则可能导致激活失败。


### 禁用自动下载

OpenCode 默认会在检测到对应文件扩展名时自动从网络下载所需的 LSP 服务器。如果你处于网络受限的环境，或希望完全手动管理 LSP 工具，可以通过设置以下环境变量来禁用自动下载：

```text
# Linux / macOS：临时禁用（仅当前终端会话有效）
export OPENCODE_DISABLE_LSP_DOWNLOAD=true

# Linux / macOS：永久禁用（写入 shell 配置文件）
echo 'export OPENCODE_DISABLE_LSP_DOWNLOAD=true' >> ~/.bashrc
source ~/.bashrc

# Windows（PowerShell：仅当前会话）
$env:OPENCODE_DISABLE_LSP_DOWNLOAD = "true"
```

禁用后，OpenCode 不会再自动下载任何 LSP 服务器，但已预先安装在系统中的 LSP 工具仍然可以正常被检测和使用。


## 复习重点

- 能说明 `OpenCode LSP 服务器配置` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
