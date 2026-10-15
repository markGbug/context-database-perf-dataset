# Vibe Coding：第一个 Vibe Coding

- 来源：[第一个 Vibe Coding](https://www.runoob.com/vibe-coding/vibe-coding-usage.html)
- 分类：AI / 智能开发
- 技术：Vibe Coding
- 笔记类型：学习笔记
- 章节序号：0682

## 本章内容

Vibe Coding 的平台工具很多，有的主打零代码拖拽，有的强调工程化定制，还有不少专注于业务流程编排与多智能体协同开发。

不同工具平台，有不同的使用场景，本章节介绍四个工具，两个在线工具，两个本地工具：


## 使用 MonkeyCode 进行 Vibe Coding

MonkeyCode 不仅是可以进行 Vibe Coding 的 AI 编程工具，它覆盖了 需求 → 设计 → 开发 → Review 全流程，免费使用，无需安装，内置云端开发环境。


### 注册与登录

进入页面后，点击右上角 注册 创建新账号，已有账号可直接登录使用。

注册成功后，我们进入控制台，输入我们的需求：

```text
帮我写一个 JavaScript 小游戏：程序随机生成 1 到 100 的数字，让我猜，猜大了提示「太大了」，猜小了提示「太小了」，猜中了就结束。
```

开始执行，我们可以选择模型： 开始任务：

任务完成后可以查看生成的效果地址：

查看效果：


## VS Code 中 Vibe Coding

VS Code 凭借丰富的 AI 插件，成为落地 Vibe Coding 最主流的编辑器，既可以用 Copilot 实现轻量开发，也可以安装专用 VIBE 智能体插件实现全自动多文件开发。

VS Code 教程：https://www.runoob.com/vscode/vscode-tutorial.html

新版 VS Code（1.116+ 最新正式版）原生内置 Copilot，不用手动装插件。

打开编辑器就能看到 Copilot 入口，只需要登录 GitHub 账号即可，无需去扩展市场安装插件。

旧版 VS Code（1.115 及更早版本）必须手动安装两个扩展：

- GitHub Copilot：行内代码自动补全
- GitHub Copilot Chat：对话式 AI 编码助手

接下来我们创建一个目录文件夹：

```text
mkdir runoob-vibe-coding
```

进入目录：

```text
cd runoob-vibe-coding
```

使用 VS Code 打开：

```text
code .
```

在编辑器里添加一个文件 vibe-coding-runoob.html ：

左侧文件菜单我们选中创建的文件，点击右上角面板切换按钮，切换出 AI 工具，然后在对话框输入提示词：

```text
帮我写一个 JavaScript 小游戏：程序随机生成 1 到 100 的数字，让我猜，猜大了提示「太大了」，猜小了提示「太小了」，猜中了就结束。
```

AI 就会开始工作，看看最终效果：

全程我们不需要参与编码，HTML 代码、CSS 样式代码、 JavaScript 代码都帮我们自动生成。


## CLI 编程工具

下面以 Claude Code（终端 CLI） 为例，展示 Vibe Coding 的典型工作流。

Claude Code 完整教程参考：https://www.runoob.com/claude-code/claude-code-tutorial.html


### 第一个项目：Hello, Vibe World!

目标：用 5 分钟，通过纯自然语言，让 Claude Code 帮你创建一个个人名片网页。

第一步：创建项目文件夹

```text
mkdir my-card && cd my-card
claude
```

第二步：向 Claude 描述你想要的东西

在 Claude Code 的交互界面中，输入：

```text
帮我创建一个个人名片网页，要求：
- 显示我的名字（张三）和职业（前端开发者）
- 有一个简短的个人简介区域
- 列出3个技能标签（React、Python、设计）
- 设计风格：简洁现代，深色背景，有轻微的渐变效果
- 单个 HTML 文件，不需要外部依赖
```

第三步：观察 Claude 工作

你会看到 Claude Code 自动：

```text
分析你的需求
创建 index.html 文件
写入完整的 HTML、CSS 和少量 JavaScript
```

第四步：查看结果

```text
open index.html   # macOS
# 或
xdg-open index.html   # Linux
```

第五步：迭代修改

如果不满意，继续对话：

```text
把背景色改成深蓝色渐变，字体换成更现代的 sans-serif，
技能标签加上悬停动画效果
```

Claude Code 会直接修改文件，无需你碰任何代码。


## 复习重点

- 能说明 `第一个 Vibe Coding` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
