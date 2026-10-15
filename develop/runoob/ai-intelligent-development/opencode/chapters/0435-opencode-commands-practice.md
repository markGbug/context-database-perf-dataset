# OpenCode：OpenCode 自定义命令

- 来源：[OpenCode 自定义命令](https://www.runoob.com/opencode/opencode-commands.html)
- 分类：AI / 智能开发
- 技术：OpenCode
- 笔记类型：练习笔记
- 章节序号：0435

## 本章内容

自定义命令允许你将常用的提示词封装成一个短命令，在 TUI 中通过 /命令名称 的方式一键执行，避免重复输入相同的提示词。

例如，将"运行测试并分析失败原因"这个复杂提示词封装为 /test，每次只需输入两个字符即可触发。

自定义命令是 /init、/undo、/redo、/share、/help 等内置命令之外的扩展。

如果你定义的自定义命令与内置命令同名，自定义命令会覆盖内置命令。请避免使用 init、undo、redo、share、help 作为自定义命令名称，除非你明确需要替换内置行为。


## 两种定义方式

自定义命令支持两种定义方式，效果完全相同，可以按照个人习惯选择：


## 方式一：JSON 配置

在 opencode.json 的 command 字段中定义，键名即为命令名称：


## 实例

配置完成后，在 TUI 输入框中输入 /test 并回车即可执行该命令。


## 方式二：Markdown 文件

在 commands/ 目录下创建 .md 文件来定义命令，文件名即为命令名，文件内容分为两部分：

- Frontmatter（--- 包裹的 YAML 部分）：定义命令的属性
- 正文（Frontmatter 下方的内容）：成为发送给 LLM 的提示词模板

Markdown 文件支持两个存放位置：

- 项目级：.opencode/commands/命令名.md（仅对当前项目有效）
- 全局：~/.config/opencode/commands/命令名.md（对所有项目有效）

```text
<!-- 文件路径：.opencode/commands/test.md -->
---
description: Run tests with coverage
agent: build
model: anthropic/claude-3-5-sonnet-20241022
---

Run the full test suite with coverage report and show any failures.
Focus on the failing tests and suggest fixes.
```

该文件名为 test.md，因此命令名为 test，在 TUI 中通过 /test 调用。


## 提示词模板语法

命令的提示词（template 字段或 Markdown 正文）支持以下特殊语法，可以让提示词动态响应参数、实时注入命令输出或引用文件内容。


### 1、传入参数（$ARGUMENTS）

使用 $ARGUMENTS 占位符接收命令调用时传入的参数，整体作为一个字符串插入：

```text
<!-- 文件路径：.opencode/commands/component.md -->
---
description: Create a new React component
---

Create a new React component named $ARGUMENTS with TypeScript support.
Include proper typing and basic structure.
```

调用时在命令名后附加参数：

```text
/component Button
```

$ARGUMENTS 会被替换为 Button，实际执行的提示词变为：

```text
Create a new React component named Button with TypeScript support.
Include proper typing and basic structure.
```


### 2、位置参数（$1、$2、$3…）

当需要传入多个独立参数时，可以使用位置参数 $1、$2、$3 分别引用每个参数，空格分隔，含空格的参数用引号包裹：

```text
<!-- 文件路径：.opencode/commands/create-file.md -->
---
description: Create a new file with content
---

Create a file named $1 in the directory $2
with the following content: $3
```

调用示例（含空格的参数用引号包裹）：

```text
/create-file config.json src "{ \"key\": \"value\" }"
```

各占位符的替换结果：


### 3、注入 Shell 命令输出（!`command`）

使用 !`shell命令` 语法可以在命令执行时运行一段 Shell 命令，并将其输出结果直接插入提示词中。Shell 命令在项目根目录下运行。这在需要让 LLM 分析实时数据（如测试结果、git 日志等）时非常有用：

```text
<!-- 文件路径：.opencode/commands/analyze-coverage.md -->
---
description: Analyze test coverage
---

Here are the current test results:
!`npm test`

Based on these results, suggest improvements to increase coverage.
```

```text
<!-- 文件路径：.opencode/commands/review-changes.md -->
---
description: Review recent git changes
---

Recent git commits:
!`git log --oneline -10`

Review these changes and suggest any improvements or potential issues.
```

执行命令时，!`git log --oneline -10` 会被替换为实际的 git 日志输出，然后连同提示词一起发送给 LLM。


### 4、引用文件内容（@文件路径）

使用 @文件路径 语法可以将指定文件的内容自动包含在提示词中，无需手动复制粘贴：

```text
<!-- 文件路径：.opencode/commands/review-component.md -->
---
description: Review a component for performance issues
---

Review the component in @src/components/Button.tsx.
Check for performance issues and suggest improvements.
```

执行命令时，@src/components/Button.tsx 会被替换为该文件的完整内容，LLM 可以直接分析文件代码。


## 配置选项详解

以下是自定义命令支持的所有配置选项，Markdown 文件中写在 frontmatter 里，JSON 配置中写在命令对象下：


### agent 与 subtask 的关系

agent 和 subtask 共同控制命令的执行方式：

- 若 agent 指定的是一个子代理（mode 为 subagent），命令默认触发子代理调用，在独立上下文中执行，不影响主会话
- 若不希望此行为，将 subtask 设为 false 可强制在主会话中执行
- 若将 subtask 设为 true，无论代理的 mode 设置如何，命令始终以子代理方式运行，适合需要完全隔离上下文的场景


## 实例


## 综合使用示例


### 示例一：多参数代码生成命令

```java
<!-- 文件路径：.opencode/commands/gen-api.md -->
---
description: Generate a REST API endpoint
agent: build
---

Generate a $1 REST API endpoint for the resource "$2".
Place the file in the $3 directory.
Include input validation, error handling, and JSDoc comments.

<!-- 调用示例：/gen-api POST user src/api -->
<!-- $1 = POST，$2 = user，$3 = src/api -->
```


### 示例二：结合 Shell 输出和文件引用的代码审查命令

```text
<!-- 文件路径：.opencode/commands/pr-review.md -->
---
description: Review changes in current branch against main
agent: plan
subtask: true
---

Please review the following changes for code quality, potential bugs, and security issues.

## Recent commits
!`git log main..HEAD --oneline`

## Changed files
!`git diff main --name-only`

## Diff content
!`git diff main`

## Project coding guidelines
@.opencode/AGENTS.md

Provide structured feedback with severity levels (critical / warning / suggestion).
```


### 示例三：定时数据快照命令（JSON 方式）

```text
{
  "$schema": "https://opencode.ai/config.json",
  "command": {
    "healthcheck": {
      "description": "Check project health status",
      "template": "Analyze the project health based on the following data:\n\nDependency vulnerabilities:\n!`npm audit --json`\n\nOutdated packages:\n!`npm outdated`\n\nTest results:\n!`npm test -- --passWithNoTests 2>&1 | tail -20`\n\nSummarize the issues by severity and suggest a prioritized action plan.",
      "model": "anthropic/claude-3-5-sonnet-20241022",
      "subtask": true
    }
  }
}
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `OpenCode 自定义命令` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
