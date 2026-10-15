# Obsidian：Obsidian + Claude Code

- 来源：[Obsidian + Claude Code](https://www.runoob.com/obsidian/obsidian-claude-code.html)
- 分类：DevOps / 工程化
- 技术：Obsidian
- 笔记类型：学习笔记
- 章节序号：1862

## 本章内容

Obsidian 是主打本地存储的 Markdown 笔记工具，文件全部保存在你自己电脑的文件夹里，安全、私密、可离线使用，加上双向链接和海量插件，它特别适合程序员用来存代码、记笔记、做长期知识沉淀。

Claude Code 是 Anthropic 推出的 AI 编程助手，基于 Claude 大模型优化，擅长读代码、改代码、写代码、查问题。

我们可以在 Obsidian 里安装 Claudian 插件，把 Claude Code 直接集成进来，让 AI 帮你写文档、整理笔记和项目进度、自动推送每日 AI 热点，让笔记库变成智能工作空间。


## 环境安装与配置


### 1、Obsidian 下载

我们需要先去 Obsidian 官方网站 https://obsidian.md/download 下载 Obsidian，提供了各种系统版本:


### 2、安装 Claude Code

终端执行（全局安装一次就好）：

```text
npm install -g @anthropic-ai/claude-code
```

安装完成后，运行一次授权：

```text
claude
```

它会让你登录 Claude 账号，完成 OAuth 授权（只需要做一次）。

注意：如果没有 Claude 账号，我们也可以用国内的大模型代替，参考：Claude Code API 配置。

Claude Code 详细内容参考：https://www.runoob.com/claude-code/claude-code-tutorial.html


### 3、安装 Obsidian 社区插件 Claudian

我们可以从 GitHub Release https://github.com/YishenTu/claudian/releases/latest 下载 main.js、manifest.json 和 styles.css 这三个文件：

在你的 Obsidian 库的插件文件夹 plugins 中（如果没有创建一个），新建一个名为 claudian 的文件夹，路径示例：

```text
/path/to/vault/.obsidian/plugins/claudian/
```

注：/path/to/vault/ 需替换为你自己的 Obsidian 库实际路径。

仓库管理菜单可以看到详细的路径：

将下载好的三个文件复制到这个 claudian/plugins/ 文件夹中。

```text
.obsidian/
└── plugins/
    └── claudian/
        ├── main.js         # 插件的编译后 JavaScript 主文件（包含所有逻辑）
        ├── manifest.json   # 插件元数据（ID、名称、版本、描述、最低 Obsidian 版本等）
        └── styles.css      # 插件的 CSS 样式
```

在 Obsidian 中启用该插件：设置 → 社区插件 → 开启「Claudian」插件开关。

通过设置，可以设置为中文语言：


## 第一次使用 Claudian

打开任意笔记，左侧边栏会出现一个 机器人图标（或用命令面板 Ctrl/Cmd+P 输入 Claudian: Open Chat）:

第一次打开会提示你选择 Claude 模型（可以设置国内的大模型），输入框打 / 会出现所有可用技能（skills）：

测试：

```text
写一篇新笔记（最常用场景）text帮我写一篇关于「2026年最值得关注的5个AI编程工具」的文献笔记，格式用我 vault 里最常用的文献笔记模板，从今天更新的网页抓取信息
```

接下来就开始正常干活了：


### 功能与使用方法

通过侧边栏功能区图标或命令面板打开聊天侧边栏，选中文本并使用快捷键即可进行行内编辑。

所有操作都与你熟悉的编码代理（Claude Code、Codex、Opencode、Pi）一致 —— 与代理对话，它就能读取、写入、编辑和搜索你库中的文件。

- 行内编辑 — 选中文本或定位光标后按下快捷键，可直接在笔记中编辑内容，并提供单词级别的差异预览。
- 斜杠命令与技能 — 输入 / 或 $ 可调用可复用的提示词模板，或来自用户级 / 库级作用域的技能（Skills）。
- @ 提及 - 输入 @ 可提及任何你希望代理处理的对象，包括库文件、子代理、MCP 服务器或外部目录中的文件。
- 规划模式 — 通过 Shift+Tab 切换。代理会先探索设计方案再执行实现，随后呈现规划内容供你确认。
- 指令模式 # — 可在聊天输入框中添加精细化的自定义指令。
- MCP 服务器 — 通过模型上下文协议（Model Context Protocol，支持标准输入输出、服务器发送事件、HTTP）连接外部工具。Claude 可在应用内管理库级 MCP；Codex 则使用其独立的命令行界面（CLI）管理 MCP 配置。
- 多标签页与对话 — 支持多聊天标签页、对话历史记录、对话分支、恢复对话及紧凑视图模式。


## 复习重点

- 能说明 `Obsidian + Claude Code` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
