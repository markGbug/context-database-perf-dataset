# Claude Code：Claude Code 斜杠 / 命令

- 来源：[Claude Code 斜杠 / 命令](https://www.runoob.com/claude-code/claude-code-slash-commands.html)
- 分类：AI / 智能开发
- 技术：Claude Code
- 笔记类型：概念卡
- 章节序号：0162

## 本章内容

斜杠 / 命令是 Claude Code 交互式会话的快捷控制入口，通过输入 / 开头的指令，就能快速调用功能、管理会话、自定义工作流。

查看所有可用命令：

```text
/help
```

/help 会列出所有内置命令、当前项目的自定义命令（Skills / Commands），以及已连接 MCP 服务器暴露的命令。

命令类型：

命令优先级（同名时）：企业级 > 个人级 > 项目级 > 内置


## 一、常用内置斜杠命令

内置命令是 Claude Code 自带的核心功能，直接输入就能用。新手优先掌握这几类高频命令：


### 基础操作命令

例如我们使用 /help 命令查看帮助信息，Tab 键可以切换菜单，Esc 退出：


### 会话管理命令


### 上下文与记忆


### 项目与配置


### 模型与输出

可用模型对照表（2026）：


### 代码与工具


### 集成与扩展

/plugin 子命令详情：


### 统计与账户


## 二、内置 Skills NEW

内置 Skills 是随 Claude Code 附带的预置 AI 工作流，与内置命令不同——它们加载详细提示词后由 Claude 推理执行，可产出更丰富的分析和操作结果，同样用 / 触发。


## 三、命令前缀语法

! 前缀使用示例：

```text
> ! ls
> !git log --oneline -10
> !npm test -- --coverage
> !cat logs/error.log | tail -50
```

@ 前缀使用示例：

```text
> 对比 @src/auth/v1.ts 和 @src/auth/v2.ts 的实现差异
> 审查 @src/api/users.ts 中的错误处理逻辑是否完善
```


## 四、自定义 Skills（新推荐格式）

Skills 是自定义命令的新一代格式，取代旧版 .claude/commands/。两种格式均可正常使用，但新项目建议直接使用 Skills。


### Skills vs Commands 对比


### 创建 Skill 步骤

自定义 Skills 分两种，存储位置不同：

- 项目 Skill：只在当前项目生效，团队共享 → 目录：.claude/skills/<名称>/
- 个人 Skill：所有项目通用，自己用 → 目录：~/.claude/skills/<名称>/

```text
# 创建项目级 Skill（团队共享，纳入 git）
mkdir -p .claude/skills/optimize

# 创建个人级 Skill（跨项目通用，本地私有）
mkdir -p ~/.claude/skills/fix-bug
```

新建 SKILL.md 文件，YAML frontmatter 写配置，下方 Markdown 正文写提示词。name 字段定义触发命令名。

示例：创建代码性能优化 Skill

```text
---
name: optimize
description: 分析代码性能瓶颈，给出优化建议。当用户提到性能问题时自动触发。
allowed-tools: Read, Grep, Glob
argument-hint: [目标文件或目录]
model: claude-sonnet-4-6
---

分析以下代码的性能瓶颈，给出具体的优化建议，优先考虑时间复杂度和内存占用：
$ARGUMENTS
```

使用时输入：

```text
/optimize src/utils/data-processor.ts
```


### 子目录命名空间组织

可在 .claude/skills/ 下用子目录按职能分类管理，目录名即命令名：

```text
.claude/skills/
├── optimize/            → /optimize
│   ├── SKILL.md
│   └── examples/        # 可选：示例文件辅助 Claude 理解
├── debug/               → /debug
│   ├── SKILL.md
│   └── scripts/         # 可选：辅助脚本
└── commit/              → /commit
    └── SKILL.md
```


## 五、自定义斜杠命令（旧格式，兼容）

如果有重复使用的提示词（比如固定的代码审查要求、重复的指令模板），可以把它做成自定义命令，一键调用。

命令文件存储位置：

参数语法：


### 核心原理

自定义命令本质是 Markdown 文本文件——文件名就是命令名，文件内容就是要执行的提示词，支持传参数、调用 Bash 命令。


### 步骤创建自定义命令

自定义命令分两种，存储位置不同：

- 项目命令：只在当前项目生效，团队共享 → 目录：.claude/commands/
- 个人命令：所有项目通用，自己用 → 目录：~/.claude/commands/

以创建项目命令为例，先建目录：

```text
# 在项目根目录执行
mkdir -p .claude/commands
```

新建一个 .md 文件，文件名就是命令名（比如 optimize.md → 命令 /optimize），文件内容写提示词。

示例：创建代码性能优化命令

```text
# 写入提示词到文件
echo "分析这段代码的性能瓶颈，给出具体的优化建议，优先考虑时间复杂度和内存占用：" > .claude/commands/optimize.md
```

现在，在会话里输入 /optimize，再粘贴代码，Claude 就会按你的要求做性能分析！


### 高级技巧：给命令加参数

命令可以带参数，用 $ARGUMENTS（捕获所有参数）或 $1 $2（按位置取参数）。

示例：带参数的 Bug 修复命令

创建命令文件 .claude/commands/fix-issue.md：

```text
修复 Issue #$ARGUMENTS，要求：
1. 符合项目编码规范
2. 附上测试用例
3. 说明修复思路
```

使用命令：

```text
/fix-issue 123  # $ARGUMENTS 会被替换成 "123"
```


## 六、Frontmatter 字段参考

自定义命令文件（commands/*.md）和 Skills（skills/*/SKILL.md）顶部均可添加 YAML Frontmatter 进行精细配置：

```text
---
name: commit                          # Skills 中必填；命令文件中可选（默认取文件名）
allowed-tools: Bash(git add:*), Bash(git commit:*), Read, Edit
argument-hint: [commit-message]
description: 检查代码质量后提交
model: claude-haiku-4-5-20251001
context: fork
agent: general-purpose
disable-model-invocation: false
user-invocable: true
hooks:
  PreToolUse:
    - matcher: "Bash"
      hooks:
        - type: command
          command: "./scripts/validate.sh"
          once: true
---
```


### 字段说明


### allowed-tools 写法示例


### Hook 触发时机


## 七、插件与 MCP 命令

除了自己写，还能通过插件和 MCP 服务器获取更多扩展命令。

命名格式：

```text
/mcp__<服务器名>__<命令名> [参数]
```


## 后续章节

- 常用 MCP 命令示例
- 1. 插件命令
- 2. MCP 命令
- 八、实用命令模板库
- 模板概览
- 附：配置文件说明

## 记忆卡片

- 一句话定义：`Claude Code 斜杠 / 命令` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
