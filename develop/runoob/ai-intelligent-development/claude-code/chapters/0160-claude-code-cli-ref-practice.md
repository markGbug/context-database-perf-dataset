# Claude Code：Claude Code CLI 参考手册

- 来源：[Claude Code CLI 参考手册](https://www.runoob.com/claude-code/claude-code-cli-ref.html)
- 分类：AI / 智能开发
- 技术：Claude Code
- 笔记类型：练习笔记
- 章节序号：0160

## 本章内容

## 一、CLI 命令


## 二、CLI 标志

通过以下标志可自定义 Claude Code 运行行为：

提示：--output-format json 标志非常适合脚本和自动化场景，可直接编程解析 Claude 响应结果。


## 三、扩展说明


### 3.1 代理标志格式

--agents 标志接收 JSON 对象，用于定义一个或多个自定义子代理。每个子代理需配置唯一名称作为键，值为包含以下字段的对象：

示例

```text
claude --agents '{
  "code-reviewer": {
    "description": "Expert code reviewer. Use proactively after code changes.",
    "prompt": "You are a senior code reviewer. Focus on code quality, security, and best practices.",
    "tools": ["Read", "Grep", "Glob", "Bash"],
    "model": "sonnet"
  },
  "debugger": {
    "description": "Debugging specialist for errors and test failures.",
    "prompt": "You are an expert debugger. Analyze errors, identify root causes, and provide fixes."
  }
}'
```


### 系统提示标志

Claude Code 提供 3 种系统提示自定义方式，满足不同使用需求：

- --system-prompt：完全接管系统提示，清空默认指令 claude --system-prompt "You are a Python expert who only writes type-annotated code"
- --system-prompt-file：从文件读取提示，适合标准化场景 claude -p --system-prompt-file ./prompts/code-review.txt "Review this PR"
- --append-system-prompt：保留默认功能，追加定制要求（推荐大多数场景使用） claude --append-system-prompt "Always use TypeScript and include JSDoc comments"

注意：--system-prompt 和 --system-prompt-file 互斥，不可同时使用。 提示：优先使用 --append-system-prompt，既能保留 Claude Code 内置能力，又能满足定制需求；仅需完全自定义时，再使用另外两个标志。

打印模式（-p）的详细用法（输出格式、流式传输、程序化集成等），参考 SDK 文档。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Claude Code CLI 参考手册` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
