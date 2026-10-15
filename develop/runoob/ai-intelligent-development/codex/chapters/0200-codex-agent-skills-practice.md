# Codex：Codex Agent Skills 技能系统

- 来源：[Codex Agent Skills](https://www.runoob.com/codex/codex-agent-skills.html)
- 分类：AI / 智能开发
- 技术：Codex
- 笔记类型：练习笔记
- 章节序号：0200

## 本章内容

Agent Skills（代理技能）是一种开放的技能组织格式，可以将任务指令、脚本和参考资料整理成可复用的技能，让 AI Agent 按照指定流程完成工作。

在 Codex 中，我们可以通过 Skills 扩展它的工作能力。例如，让 Codex 按照固定规范审查代码、生成测试、编写技术文档或者处理数据文件。

与每次手动输入一大段提示词不同，Skills 可以将经常使用的操作流程保存下来，在需要时重复使用。

一个 Skill 本质上是包含 SKILL.md 文件的目录。这个文件负责描述技能的用途、适用场景以及具体执行步骤。

例如，一个简单的 Skill 目录可以是：

```text
my-skill/
├── SKILL.md           # 必需：技能说明与执行指令
├── scripts/           # 可选：Python、Shell 等脚本
├── references/        # 可选：参考文档
└── assets/            # 可选：模板、图片等资源
```

其中，只有 SKILL.md 是必需的。对于简单任务，只需要这个文件就可以创建一个 Skill。


## 什么是 Agent Skills？

Skills 可以理解为提供给 AI Agent 的一套可复用操作说明。

例如，我们希望 Codex 在检查 Python 代码时，始终按照以下要求执行：

- 检查代码语法及潜在运行错误。
- 识别可能存在的安全问题。
- 检查代码可读性和维护性。
- 给出修改建议，并说明原因。
- 未经允许，不直接修改源文件。

如果没有 Skill，可能每次都需要重复输入这些要求。

创建一个代码审查 Skill 后，就可以直接告诉 Codex：

```text
使用 python-code-review 技能，检查当前项目的 Python 代码。
```

Codex 会读取相关技能说明，并按照定义的规则执行任务。

Skills 可以用于 Codex CLI、IDE 扩展和支持技能的桌面应用。部分技能也可以通过 Plugins 打包，在其他受支持的 ChatGPT 环境中使用。

需要注意，Skill 本身主要提供操作指令和相关资源，并不意味着它自动获得额外权限。真正能够执行哪些操作，仍取决于 Codex 当前可使用的工具和运行环境。


### Skills、MCP 与 Plugins 的区别

在使用 Codex 时，经常会同时遇到 Skills、MCP 和 Plugins 三个概念。

例如，一个生成销售报告的 Skill 可以规定如何分析数据、绘制图表和整理结果；MCP 可以提供访问业务数据库的工具；Plugin 则可以将这些能力打包分发。

三者可以配合使用，但一个简单的 Skill 并不需要同时配置 MCP 和 Plugin。


### 查看 Codex Skills

在支持 Skills 管理功能的 Codex 客户端中，可以查看已安装技能，也可以使用内置创建工具编写新技能。

Codex 提供了 skill-creator，可以通过对话方式创建或修改 Skill。

创建完成后，可以在技能列表中查看对应的技能。


## Skills 的工作原理

Codex 可以同时安装多个 Skills，但不会在每次任务开始时都读取所有技能的完整内容。

为了减少上下文占用，Codex 使用渐进式加载（Progressive Disclosure）机制。


### 渐进式加载

技能加载通常分为以下几个阶段：

- 发现技能：Codex 读取技能的名称、描述和文件路径等信息。
- 选择技能：根据用户显式指定的技能，或者当前任务与技能描述的匹配情况，决定使用哪个 Skill。
- 读取指令：加载对应的 SKILL.md 文件。
- 读取资源：根据任务需要访问相关的脚本、参考文档或模板。
- 执行任务：按照技能指令，使用当前环境中可用的工具完成工作。

例如，安装了 20 个 Skills，并不代表 Codex 每次都会将这 20 个技能的完整内容放入模型上下文。

Codex 的初始技能列表有上下文预算限制：最多使用模型上下文窗口的约 2%；无法确定上下文窗口大小时，使用 8,000 字符的预算。

当技能数量较多时，Codex 可能缩短描述，必要时省略部分初始列表中的技能并给出警告。

这个限制主要针对初始技能列表，不表示被选中的 Skill 只能使用这么少的内容。


### 技能调用方式

Codex 支持显式调用和隐式匹配两种主要方式。

显式调用是指用户明确指定要使用哪个 Skill。

在 Codex CLI 或 IDE 扩展中，可以使用 /skills 查看或选择技能，也可以通过 $ 引用技能。

例如：

```text
$python-code-review 检查当前项目的代码
```

这里的 $python-code-review 是 Codex 对话中的技能引用，不是终端中的普通 Shell 命令。

隐式匹配是指用户没有明确指定技能，但 Codex 根据当前任务和 Skill 的 description 判断某个技能是否适用。

例如，用户输入：

```text
帮我检查这个 Python 项目有没有安全问题。
```

如果安装了适用于 Python 代码审查的 Skill，Codex 可能自动选择该技能。

隐式匹配并不保证每次都会触发，因此 description 应该清楚地描述技能适用于哪些任务，以及哪些情况不应该使用。


## Skills 目录结构

一个完整的 Skill 可以包含指令文件、执行脚本、参考资料和其他资源。

```text
my-skill/
├── SKILL.md
├── scripts/
│   └── check.py
├── references/
│   └── coding-rules.md
├── assets/
│   └── report-template.md
└── agents/
    └── openai.yaml
```

各个文件和目录的作用如下：

对于初学者，建议先从一个 SKILL.md 文件开始。只有确实需要执行代码或使用参考资料时，再添加其他目录。


## 创建第一个 Skill

创建 Skill 可以通过内置的 skill-creator 完成，也可以手动编写。


### 方法一：使用 skill-creator

在 Codex 对话中输入：


## 实例

然后说明希望创建的技能，例如：

```text
帮我创建一个 Python 代码审查 Skill。

要求：
1. 检查代码语法和潜在错误。
2. 检查常见安全问题。
3. 提出可读性和性能方面的建议。
4. 输出包含文件位置、问题和修改建议的报告。
5. 不要自动修改源文件。
```

创建器会根据任务描述生成技能文件，并可以帮助完善描述和执行步骤。

创建完成后，需要检查生成的 SKILL.md 是否符合预期，并使用实际任务测试调用效果。


### 方法二：手动创建 Skill

如果希望更清楚地了解 Skills 的结构，可以手动创建。

下面以 Python 代码审查为例。

第一步：创建目录

进入需要使用 Skills 的项目目录，创建技能文件夹：

```text
mkdir -p .agents/skills/python-code-review
```

目录结构如下：

```text
project/
└── .agents/
    └── skills/
        └── python-code-review/
            └── SKILL.md
```

第二步：编写 SKILL.md

在技能目录中创建 SKILL.md 文件，写入以下内容：


## 实例

其中，文件开头的 --- 区域是 YAML 元数据：

- name：技能名称，通常使用简洁的英文标识。
- description：技能的用途和适用条件，也是隐式匹配的重要依据。

后面的 Markdown 正文则定义技能的执行步骤、输出格式和限制条件。

第三步：调用技能

在项目目录启动 Codex 后，可以通过以下提示词调用：

```text
$python-code-review 检查当前项目的 Python 代码。
```

也可以使用普通任务描述测试隐式匹配：

```text
请对当前 Python 项目进行代码审查，
重点检查安全漏洞和潜在运行错误。
```

如果技能能够正确加载，Codex 就会参考 SKILL.md 中定义的规则执行审查。

第四步：测试技能

建议分别测试以下情况：

- 明确引用 Skill，检查是否能够正常调用。
- 仅描述 Python 代码审查任务，观察是否自动匹配。
- 要求编写普通 Python 程序，检查是否出现不必要的技能调用。
- 检查最终输出是否包含文件位置、问题描述和修改建议。

通过测试可以进一步调整 description 和具体指令。

建议在项目中保留测试样例，便于以后更新 Skill 时进行回归检查。


## Skills 存储位置

Codex 可以从多个位置发现 Skills，包括仓库级、用户级、管理员级和系统内置技能。

常见路径如下：

对于 Git 仓库，Codex 可以从当前工作目录向上扫描到仓库根目录，查找各级 .agents/skills 文件夹。

例如：

```text
project/
├── .agents/
│   └── skills/
│       └── project-review/
└── backend/
    └── .agents/
        └── skills/
            └── api-check/
```

项目根目录下的技能适合整个项目共享，子目录中的技能则可以用于更具体的模块。

如果两个 Skill 使用相同的 name，Codex 不会自动合并它们，可能会在选择器中同时显示。因此，建议为技能使用清晰且不重复的名称。


### 如何选择安装位置？

如果技能只用于某个项目，建议保存在项目的 .agents/skills/ 中，并通过 Git 进行版本管理。

如果技能适用于所有项目，例如通用的 Python 代码审查或文档编写规范，可以保存到用户级目录：

```text
~/.agents/skills/
```

这样不需要在每个项目中重复创建同一个 Skill。


## Skills 配置说明


### 启用与禁用技能

对于本地 Codex，可以通过 ~/.codex/config.toml 中的 [[skills.config]] 配置禁用指定技能。


## 实例

其中，path 应填写技能对应 SKILL.md 文件的实际路径。

设置 enabled = false 后，可以在不删除技能文件的情况下禁用该技能。

修改配置后，通常需要重启 Codex。


### 配置技能显示信息

除了 SKILL.md，还可以使用可选文件 agents/openai.yaml 配置技能显示信息及调用策略。

例如：


## 实例

常见配置项如下：

allow_implicit_invocation 默认允许隐式调用。设置为 false 后，Codex 不会仅根据任务描述自动选择该技能，但仍可以显式引用。

例如，如果某个 Skill 涉及敏感操作，可以选择只允许显式调用。

注意：禁用隐式调用并不等于限制工具权限。涉及删除文件、修改数据库等操作时，仍然需要使用独立的权限和审批机制。


### 声明 MCP 工具依赖

如果 Skill 需要使用外部 MCP 服务，还可以在 agents/openai.yaml 中声明工具依赖。

例如：


## 实例

该配置用于声明技能对 MCP 工具的依赖，不应理解为它会自动完成所有 MCP 服务器的安装、授权和连接。

实际使用时，仍需确认运行环境中对应的 MCP 服务可用，并具备所需的访问权限。


## 安装与分发 Skills


### 安装精选技能

Codex 提供 skill-installer，用于安装精选技能或从其他仓库获取技能。

例如，在 Codex 对话中输入：


## 实例

该示例表示调用技能安装器，请求安装名为 linear 的技能。

同样需要注意，这属于 Codex 的技能调用方式，而不是普通终端命令。

技能安装完成后，如果没有出现在技能列表中，可以尝试重新启动 Codex。


## 后续章节

- 从 GitHub 安装技能
- 使用 Plugins 分发
- 编写 Skills 的最佳实践
- 如何编写 description？
- 常见问题
- 1、技能创建后没有显示？
- 2、Skill 为什么没有自动触发？
- 3、两个 Skill 名称相同怎么办？
- 4、Skill 可以执行 Python 脚本吗？
- 5、Skill 和 AGENTS.md 有什么区别？
- 6、一个 Skill 可以包含多个文件吗？
- 7、什么时候使用 Skill，什么时候使用 Plugin？
- 总结

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Codex Agent Skills` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
