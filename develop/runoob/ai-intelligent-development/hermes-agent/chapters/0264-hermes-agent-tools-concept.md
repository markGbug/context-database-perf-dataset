# Hermes Agent：Hermes Agent 工具集

- 来源：[Hermes Agent 工具集](https://www.runoob.com/hermes-agent/hermes-agent-tools.html)
- 分类：AI / 智能开发
- 技术：Hermes Agent
- 笔记类型：概念卡
- 章节序号：0264

## 本章内容

工具是 Hermes Agent 与外部世界交互的唯一通道——读写文件、执行命令、搜索网页、生成图片，所有能力都通过工具暴露。

Hermes 内置 70+ 工具，分为 28 个工具集。本章将逐一解析每个工具集的核心工具、参数和最佳实践。


## 工具系统架构

在深入具体工具之前，先理解工具的组织方式。

Hermes 采用三层结构管理工具：

```text
工具（Tool）          ← 单个可调用函数，如 read_file、web_search
  └── 工具集（Toolset）   ← 相关工具的逻辑分组，如 file、web
        └── 平台配置        ← 哪个平台加载哪些工具集
```

关键设计：禁用一个工具集，其中的工具从系统提示词中完全消失——不只是不可调用，而是 Agent 根本不知道它们的存在。这既节省 Token，也防止 Agent 误用不该用的工具。

管理工具集的方式：

```text
# TUI 交互式管理（推荐）
hermes tools

# 命令行管理
hermes tools list                # 列出所有工具及启用状态
hermes tools enable browser      # 启用指定工具集
hermes tools disable audio       # 禁用指定工具集
```

在 config.yaml 中配置：

```text
# 文件路径：~/.hermes/config.yaml
# 按平台指定启用的工具集
platform_toolsets:
  cli:
    - hermes-cli         # CLI 核心工具集
    - file
    - terminal
    - web
    - memory
    - skills
```

桌面版，在左侧的技能与工具菜单：

仪表盘上也可以管理工具，在左侧技能菜单里：


## 文件与系统工具集

这类工具集让 Agent 能够操作本地文件系统、执行命令和管理进程。


### file — 文件操作

最基础的工具集，Agent 几乎所有任务都依赖它来读写文件。

edit_file 的工作原理：它使用精确子串匹配定位修改位置。Agent 提供 old_string（文件中实际存在的文本），工具找到它并替换为 new_string。如果 old_string 匹配到多处，设置 replace_all: true 替换所有出现。

edit_file 是 Agent 最常用的文件修改方式——它比 write_file 更安全，因为如果 old_string 找不到，操作会失败报错，不会意外覆盖文件。


### terminal — Shell 命令执行

让 Agent 在指定的后端环境中执行 Shell 命令。

命令在配置的终端后端中执行——local（本机）、docker（容器）、ssh（远程）等。

执行结果包含 stdout、stderr 和退出码，Agent 可以根据这些信息判断命令是否成功。


### code — 沙箱代码执行

在隔离沙箱中执行代码片段，支持 Python、JavaScript 和 Bash。

与 terminal 的区别：code 工具在独立沙箱中运行，不能访问文件系统（除非显式挂载），适合运行算法验证、数据处理等不需要文件交互的代码。


### computer — 桌面 GUI 自动化

控制桌面环境的鼠标、键盘和截图。

computer 工具集主要用于 GUI 应用测试和自动化操作。如果你的使用场景不涉及桌面应用，可以禁用以节省 Token。


## 网络与内容工具集

这类工具集让 Agent 能够搜索互联网、提取网页内容和自动化浏览器操作。


### web — 网页搜索与内容提取

Agent 获取外部信息的主要渠道。

web_search 返回搜索结果列表（标题 + URL + 摘要），Agent 通常先搜索，再对感兴趣的页面调用 web_extract 获取详细内容。

需要配置搜索 API 才能使用。支持多种提供商：


## 实例


### browser — 浏览器自动化

完整的浏览器控制能力——导航、点击、填表、截图，像人一样操作网页。

browser 工具集需要 Playwright 或云端浏览器后端支持。

browser 工具集启动浏览器实例会消耗额外资源。如果只需要提取网页文本内容，优先使用 web_extract 而非 browser extract——前者是轻量 HTTP 请求，后者需要启动完整浏览器。


### vision — 图片分析

让 Agent 「看懂」图片内容。

vision 工具将图片发送给支持视觉的 LLM（如 claude-sonnet-4-6、gpt-4o），由模型识别和描述图片内容。


### audio — 音频处理

语音转文字和文字转语音。


## Agent 能力工具集

这类工具集管理 Agent 自身的状态——记忆、技能、子 Agent 协作。


### memory — 记忆管理

读写持久记忆和搜索跨会话历史。

memory 工具没有 read 操作——持久记忆在会话启动时已注入系统提示词，Agent 无需额外读取。


### skills — 技能管理

加载和管理可复用的工作流技能。


### delegation — 子 Agent 委托

派生子 Agent 并行执行任务。

子 Agent 拥有独立的上下文窗口，不会污染主 Agent 的对话历史。执行完毕后返回结果摘要。


### kanban — 多 Agent 看板

结构化的多 Agent 协作系统，需显式启用（all/* 也不自动开启）。

Kanban 是多 Profile 协作的核心机制——一个编排者 Profile 创建任务，多个工作者 Profile 认领执行。这需要多个 Profile 的网关同时运行。


## 媒体创作工具集

这类工具集通常需要 Nous Portal 订阅或对应的第三方 API Key。


### image_gen — AI 图片生成

根据文字描述生成图片，支持 9 种模型。


### tts — 文字转语音

独立于 audio 工具集的 TTS 功能，提供更丰富的提供商选择。


## 自定义工具集

你可以将现有工具集组合为项目专属的自定义工具集：


## 实例

使用时通过 --toolsets 参数指定：


## 实例


## 工具调用流程

了解一次工具调用的完整流程有助于理解 Agent 的行为和排查问题。

一次完整的工具调用经过以下步骤：

- LLM 在生成回复时决定调用某个工具，输出工具名和参数
- tool_request Middleware 执行（可以修改参数）
- 审批检查——如果工具是危险操作，根据 approvals.mode 决定是否弹出确认
- 工具实际执行
- tool_execution Middleware 执行（可以修改结果）
- post_tool_call Hook 记录遥测数据
- 执行结果返回给 LLM，LLM 继续生成回复

如果你的 Middleware 修改了工具参数，修改后的参数是审批和实际执行的输入。如果你在 Middleware 中短路了执行（返回自定义结果），实际工具不会运行。


## 后续章节

- 工具使用统计
- 实例
- 实例

## 记忆卡片

- 一句话定义：`Hermes Agent 工具集` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
