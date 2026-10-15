# Claude Code：Claude Code 输出样式

- 来源：[Claude Code 输出样式](https://www.runoob.com/claude-code/claude-code-outputstyles.html)
- 分类：AI / 智能开发
- 技术：Claude Code
- 笔记类型：概念卡
- 章节序号：0158

## 本章内容

输出样式（Output Style）让你可以定制 Claude Code 的交互风格和响应方式，使其适配软件开发之外的更多使用场景，同时保留运行本地脚本、读写文件、跟踪待办事项等核心功能。

其本质是通过修改系统提示（System Prompt），改变 Claude Code 的交互逻辑和响应风格。


## 内置输出样式

Claude Code 提供 3 种开箱即用的输出样式：


## 工作原理

切换输出样式时，Claude Code 会按以下规则调整系统提示：

- 所有样式都会移除默认的"简洁回复、高效输出"等约束指令
- 自定义样式默认会剔除"用测试验证代码"等编码相关指令（如需保留，可在样式文件中开启 keep-coding-instructions: true）
- 每种样式会在系统提示末尾追加自定义规则，覆盖默认行为
- 对话过程中会触发合规检查，确保 Claude 始终遵守当前样式的指令


## 切换输出样式

切换样式有两种方式，配置保存在项目目录的 .claude/settings.local.json 文件中，仅对当前项目生效：

方式一：菜单选择——输入命令后，在交互菜单中选择目标样式：

```text
/output-style
```

方式二：直接指定——在命令后直接加上样式名称，一步到位：

```text
/output-style explanatory
```

```text
/output-style learning
```

```text
/output-style default
```

除了使用命令切换，也可以直接编辑 .claude/settings.local.json（项目级）或 ~/.claude/settings.json（全局级）文件，修改 outputStyle 字段的值来切换样式。


## 创建自定义输出样式

如果内置样式不满足需求，可以通过 Markdown 文件定义专属样式。


### 1、文件保存位置


### 2、文件格式

自定义样式文件由两部分组成：顶部的 YAML frontmatter（元数据配置）和下方的 Markdown 正文（具体指令内容）。


## 实例


### 3、frontmatter 参数说明


### 4、使用步骤

- 按上述格式创建 .md 文件（例如 data-analyst.md）
- 将文件放到对应目录： 所有项目可用：~/.claude/output-styles/data-analyst.md 仅当前项目可用：.claude/output-styles/data-analyst.md
- 在 Claude Code 中执行 /output-style，即可在菜单中看到并选择新创建的样式


## 与相关功能的区别

输出样式与以下几个功能看起来相似，但作用层面不同：


## 自定义样式模板

以下是一个通用的自定义输出样式模板，将 [ ] 中的内容替换为你的实际需求，保存为 .md 文件即可使用：


## 实例


## 记忆卡片

- 一句话定义：`Claude Code 输出样式` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
