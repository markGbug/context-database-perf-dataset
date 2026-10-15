# Skills（技能）：VS Code 创建与使用 Skill

- 来源：[VS Code Skills](https://www.runoob.com/skills/vs-code-skill.html)
- 分类：AI / 智能开发
- 技术：Skills（技能）
- 笔记类型：概念卡
- 章节序号：0621

## 本章内容

本教程将带你从头开始创建一个 Agent Skill，并在 VS Code + GitHub Copilot 中实际运行它。

我们将创建一个掷骰子 Skill，让 Agent 学会通过终端命令生成随机数。


## 准备工作


### 环境要求

- 安装 VS Code

安装 GitHub Copilot 扩展

本教程使用 VS Code，但 Agent Skills 是开放格式。相同的 Skill 也可以在 Claude Code、OpenCode、OpenAI Codex 等兼容工具中使用。

更多 VS Code 内容可以参考：VS Code 教程。


## 创建 Skill 目录和文件

VS Code 默认在项目的 .agents/skills/ 目录下查找 Skill。

首先在你的项目中创建以下目录结构：


## 创建目录结构

然后在 .agents/skills/roll-dice/SKILL.md 中创建以下文件：


## 实例：SKILL.md 完整内容

一个文件、不到 20 行，就完成了一个完整的 Skill。


## 文件结构解析

让我们逐部分理解这个文件的作用。


### YAML 头部（Frontmatter）


### 正文（Markdown Body）

正文是 Agent 激活 Skill 后实际遵循的指令。

这里我们告诉 Agent：当用户要求掷骰子时，使用操作系统的随机数命令，并把骰子面数传入命令中。

我们同时提供了 macOS/Linux 和 Windows 两种平台的命令，Agent 会根据当前环境自动选择。


## 测试你的 Skill

创建好文件后，按以下步骤验证：

- 用 VS Code 打开你的项目
- 打开 Copilot Chat 面板（快捷键 Ctrl+Shift+I 或 Cmd+Shift+I），或者点击右上角的按钮：
- 在聊天面板底部选择 Agent 模式
- 输入 /skills 命令，确认 roll-dice 出现在 Skill 列表中
- 可以看到技能列表有 roll-dice：

如果在 /skills 列表中看不到 roll-dice，请检查文件路径是否正确：.agents/skills/roll-dice/SKILL.md，注意 SKILL.md 必须大写。

确认 Skill 已加载后，在聊天中输入：

```text
Roll a d20
```

Agent 应该会自动激活 roll-dice Skill，运行终端命令并返回 1 到 20 之间的随机数。


## 背后的工作过程

当你在 Copilot Chat 中使用这个 Skill 时，底层经历了三个步骤：


### 步骤一：发现

聊天会话开始时，Agent 扫描默认 Skill 目录（.agents/skills/），找到了 roll-dice。

它只读取了 name 和 description，知道了"这个 Skill 是用来掷骰子的"。


### 步骤二：激活

当你输入 "Roll a d20" 时，Agent 将你的问题与 roll-dice 的 description 进行了匹配。

匹配成功后，Agent 将完整的 SKILL.md 正文加载到了上下文中。


### 步骤三：执行

Agent 按照正文中的指令，识别出你用的是 macOS（或 Linux），选择了 bash 命令。

它将 d20 对应的 20 替换到命令中，执行 echo $((RANDOM % 20 + 1))，然后把结果返回给你。


## 常见问题排查


## 跨工具使用提示

虽然本教程使用 VS Code，但 Skill 同样可以用于其他工具：

不同的工具可能使用不同的默认目录，但 Skill 本身的格式和文件结构是通用的。


## 记忆卡片

- 一句话定义：`VS Code Skills` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
