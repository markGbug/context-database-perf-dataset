# Pi Agent：Pi Agent 交互模式

- 来源：[Pi Agent 交互模式](https://www.runoob.com/pi-agent/pi-agent-interactive.html)
- 分类：AI / 智能开发
- 技术：Pi Agent
- 笔记类型：练习笔记
- 章节序号：0483

## 本章内容

本章全面介绍 Pi Agent 交互模式下的核心操作，包括 Slash 命令、模型管理和键盘操作。


## Slash 命令大全

在编辑区输入 / 会触发命令自动补全。

以下是 Pi Agent 交互模式下的常用内置命令：

除了内置命令，Extensions（扩展）也可以注册自定义命令。

Skills 会自动注册为 /skill:名称 命令，提示词模板则通过 /模板名 来调用。


## 模型管理

模型管理涵盖切换模型、设定循环切换范围和调整推理等级三个方面。

下面分别介绍对应的命令与快捷键。


### 切换模型（/model 和 Ctrl+L）

使用 /model 命令或 Ctrl+L 打开模型选择器，浏览所有可用的 AI 模型。

在模型选择器中，你可以按名称搜索，选中后按 Ctrl+S 可保存为启动默认。

下面是一个打开模型选择器并切换模型的操作过程：

```text
/model
┌ 选择模型（输入关键词过滤，↑/↓ 移动，Enter 确认）：
│ > anthropic/claude-sonnet-4-5
│   anthropic/claude-opus-4-1
│   openai/gpt-4o
│   google/gemini-2.5-pro
└
已切换到 anthropic/claude-sonnet-4-5
```

列表中的模型取决于你已配置的提供商，实际显示会与示例不同。


### 快速循环切换（Ctrl+P）

Ctrl+P 向前循环切换模型，Shift+Ctrl+P 向后切换。

切换范围由 /scoped-models 命令或 enabledModels 设置控制。


### 推理等级（Shift+Tab）

Shift+Tab 循环切换推理等级。

编辑器边框颜色会随等级变化，让你直观感知当前的推理深度：

在 /thinking 选择器内按 Ctrl+S 可把当前等级保存为启动默认。

模型不支持的推理等级不会生效，也不会出现在切换列表中。

模型的能力决定了推理等级的上限。


## Shell 命令集成

你可以在编辑区直接执行 shell 命令，无需离开 Pi Agent：

使用示例：

```text
!npm test
!git diff --stat
!python -m pytest -v

!!cat ~/.zshrc
!!ls -la
```

下面执行 !npm test 后的实际效果，输出会同时显示在本地并交给 AI：

```text
!npm test
> pi-demo@1.0.0 test
> vitest run

 PASS  src/utils/format.test.ts (6 tests) 12ms
 PASS  src/utils/parse.test.ts (4 tests) 8ms

 Test Files  2 passed (2)
      Tests  10 passed (10)
```

! 命令的输出会占用 AI 的上下文窗口。

如果输出很大（如完整日志），考虑使用 !! 或者将输出重定向到文件再让 AI 读取。


## 消息队列深入

消息队列让你在 AI 正在工作时也能发送指令，大幅提升交互效率：

你可以通过设置中的 steeringMode 和 followUpMode 来控制消息的发送策略。

在 Windows 和 WSL 下，Alt+Enter 常被终端占用（如 Windows Terminal 默认绑定全屏切换），此时实际默认可用 Ctrl+Q 发送 follow-up 消息。


## 编辑器功能

编辑区提供文件引用、路径补全、多行输入等增强能力，减少来回切换工具的次数。

多行输入中的「Windows Terminal 用 Ctrl+Enter」是 Windows Terminal 下的自动适配，并非 keybindings.json 中的默认值。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Pi Agent 交互模式` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
