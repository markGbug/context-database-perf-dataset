# Vibe Coding：GitHub Copilot 入门教程

- 来源：[GitHub Copilot 入门教程](https://www.runoob.com/vibe-coding/github-copilot-usage.html)
- 分类：AI / 智能开发
- 技术：Vibe Coding
- 笔记类型：学习笔记
- 章节序号：0685

## 本章内容

GitHub Copilot 已经不是 2021 年那个 代码补全工具 了。

GitHub Copilot 现在是一个覆盖 IDE、CLI、Github 的 AI 编程平台：在 IDE 里自主编辑多个文件，在云端把 Issue 变成 PR，在终端运行并行子 Agent，在 PR 页面做智能代码审查。


### GitHub Copilot 发展

今天的 Copilot 是一个跨 IDE、CLI、GitHub.com、手机的统一 AI 编程平台，而不只是一个补全插件。


### 核心能力全图


## VS Code 使用

VS Code 凭借丰富的 AI 插件，成为落地 Vibe Coding 最主流的编辑器，既可以用 Copilot 实现轻量开发，也可以安装专用 VIBE 智能体插件实现全自动多文件开发。

VS Code 教程：https://www.runoob.com/vscode/vscode-tutorial.html

新版 VS Code（1.116+ 最新正式版）原生内置 Copilot，不用手动装插件，点击左上角图标调出：

打开编辑器就能看到 Copilot 入口，只需要登录 GitHub 账号即可，无需去扩展市场安装插件。

登录后查看：

旧版 VS Code（1.115 及更早版本）必须手动安装两个扩展：

- GitHub Copilot：行内代码自动补全
- GitHub Copilot Chat：对话式 AI 编码助手


### 开始 Vibe Coding

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


### 官方资源

- GitHub Copilot 功能总览：docs.github.com/copilot/get-started/features
- 套餐与价格：github.com/features/copilot/plans
- Cloud Agent 文档：docs.github.com/copilot/concepts/agents
- 自定义指令指南：docs.github.com/copilot/customizing-copilot
- 学生免费申请：education.github.com/pack
- Copilot Changelog：github.blog/changelog


## 复习重点

- 能说明 `GitHub Copilot 入门教程` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
