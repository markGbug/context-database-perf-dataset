# Claude Code：Claude Code DeepSeek 配置

- 来源：[Claude Code DeepSeek](https://www.runoob.com/claude-code/claude-code-deepseek.html)
- 分类：AI / 智能开发
- 技术：Claude Code
- 笔记类型：练习笔记
- 章节序号：0138

## 本章内容

Claude Code 是 Anthropic 推出的一款运行在终端内的 AI 编程助手，支持通过环境变量配置第三方兼容 API，从而接入 DeepSeek 等模型。

本文介绍如何将 Claude Code 与 DeepSeek 结合使用，以更低的成本获得强大的 AI 辅助编程能力。

关键点：

- Claude Code 通过 ANTHROPIC_BASE_URL 环境变量指向 DeepSeek 兼容接口。
- DeepSeek 提供与 Anthropic API 兼容的接口，路径为 https://api.deepseek.com/anthropic。
- 通过一组环境变量，可将不同层级的模型（Opus / Sonnet / Haiku）分别映射到对应的 DeepSeek 模型。
- 配置完成后，直接在项目目录执行 claude 命令即可使用。

简单来说：Claude Code + DeepSeek = 终端 AI 编程助手 + 高性价比大模型

- Claude Code：提供完整的终端 AI 编程交互体验，支持代码生成、重构、调试、解释等。
- DeepSeek API：提供与 Anthropic 兼容的接口，支持 DeepSeek 系列模型调用。
- 环境变量桥接：通过标准环境变量将两者连接，无需修改任何 Claude Code 源码。


### 前置条件

如果已安装了 Claude Code 这一步可以跳过。

- 已安装 Node.js 18 及以上版本。
- Windows 用户还需安装 Git for Windows（提供 bash 环境）。
- 已在 DeepSeek Platform 注册账号并创建 API Key。

在命令行界面执行以下命令，安装 Claude Code：

```text
curl -fsSL https://claude.ai/install.sh | bash
```

安装完成后，执行以下命令验证，若正常输出版本号则安装成功：

```text
claude --version
```

如果遇到权限问题，Linux / macOS 用户可在命令前加 sudo。

如果有登录的校验，可以找到用户目录下的 .claude.json：

- macOS/Linux：~/.claude.json
- Windows：C:\Users\你的用户名\.claude.json

```text
{
  "hasCompletedOnboarding": true
}
```

保存后重启终端，再跑：

```text
claude
```

这时不会再弹出 登录 claude.ai 的窗口 / 提示。


### 获取 DeepSeek API Key

前往 DeepSeek Platform 登录后创建 API Key，妥善保存，配置环境变量时会用到。

API Key 具有账户操作权限，请勿将其提交到代码仓库或分享给他人。建议使用操作系统的密钥管理工具或环境变量文件（如 .env）进行管理，并将相关文件加入 .gitignore。


## 配置环境变量

Claude Code 通过以下环境变量与 DeepSeek API 进行对接，各变量含义如下：


### Linux / macOS

在终端执行以下命令（将 <你的 DeepSeek API Key> 替换为实际的 Key）：

```text
export ANTHROPIC_BASE_URL=https://api.deepseek.com/anthropic
export ANTHROPIC_AUTH_TOKEN=<你的 DeepSeek API Key>
export ANTHROPIC_MODEL=deepseek-v4-pro[1m]
export ANTHROPIC_DEFAULT_OPUS_MODEL=deepseek-v4-pro[1m]
export ANTHROPIC_DEFAULT_SONNET_MODEL=deepseek-v4-pro[1m]
export ANTHROPIC_DEFAULT_HAIKU_MODEL=deepseek-v4-flash
export CLAUDE_CODE_SUBAGENT_MODEL=deepseek-v4-flash
export CLAUDE_CODE_EFFORT_LEVEL=max
```

以上 export 命令仅在当前终端会话中生效。

如需永久生效，可将上述命令追加到 ~/.bashrc（Bash）或 ~/.zshrc（Zsh）文件末尾，然后执行 source ~/.bashrc 使其立即生效。


### Windows（PowerShell）

在 PowerShell 中执行以下命令：

```text
$env:ANTHROPIC_BASE_URL="https://api.deepseek.com/anthropic"
$env:ANTHROPIC_AUTH_TOKEN="<你的 DeepSeek API Key>"
$env:ANTHROPIC_MODEL="deepseek-v4-pro[1m]"
$env:ANTHROPIC_DEFAULT_OPUS_MODEL="deepseek-v4-pro[1m]"
$env:ANTHROPIC_DEFAULT_SONNET_MODEL="deepseek-v4-pro[1m]"
$env:ANTHROPIC_DEFAULT_HAIKU_MODEL="deepseek-v4-flash"
$env:CLAUDE_CODE_SUBAGENT_MODEL="deepseek-v4-flash"
$env:CLAUDE_CODE_EFFORT_LEVEL="max"
```

PowerShell 的 $env: 赋值仅对当前会话生效。如需永久生效，可在「系统属性 → 环境变量」中添加对应的用户环境变量，或将上述命令写入 PowerShell Profile 文件（$PROFILE）。


### 验证是否生效

配置完成后，启动 Claude Code 并执行 /status 命令验证：

```text
$ cd 你的项目目录
$ claude
/status
```

如果配置正确，你将看到类似以下的输出：

```text
Base URL: https://api.deepseek.com/anthropic
Model: deepseek-v4-pro[1m]
Small fast model: deepseek-v4-flash
```

看到这些信息即表示配置成功，Claude Code 现在已经在使用 DeepSeek V4 进行推理了。

如果显示的不是上述信息，请逐项检查：环境变量是否设置正确、API Key 是否有效、变量名是否有拼写错误。


## 开始使用

进入你的项目目录，执行 claude 命令即可启动 Claude Code：

```text
cd /path/to/my-project
claude
```

成功启动后，终端将进入 Claude Code 的交互界面，你可以直接用自然语言描述编程需求，例如：

```text
# 让 Claude Code 解释当前项目结构
> 帮我梳理一下这个项目的目录结构和主要模块的作用

# 生成代码
> 给 user.go 新增一个根据邮箱查询用户的方法，并补充单元测试

# 调试问题
> 运行 npm test 后报错，帮我分析原因并修复
```


## 参考配置


### 环境变量完整


### 模型名称速查


### Shell 配置文件路径速查


### Claude Code 配置文件速查


### 模型选择建议

不同 DeepSeek 模型在性能与成本之间有不同的权衡，以下是常见场景的推荐配置：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Claude Code DeepSeek` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
