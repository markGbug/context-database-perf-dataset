# AI Agent（智能体）：Vibe Coding 入门教程

- 来源：[Vibe Coding](https://www.runoob.com/ai-agent/vibe-coding-start.html)
- 分类：AI / 智能开发
- 技术：AI Agent（智能体）
- 笔记类型：学习笔记
- 章节序号：0030

## 本章内容

Vibe Coding（氛围编程）是一种全新的编程范式，我们不需要一行行手写代码，而是用自然语言描述你想要什么，AI 来写代码、我们负责审查和把控方向。

Vibe Coding 教程参考：https://www.runoob.com/vibe-coding/vibe-coding-tutorial.html


## 什么是 Vibe Coding

Vibe Coding 一词由前特斯拉 AI 总监、OpenAI 联合创始人 Andrej Karpathy 在 2025 年 2 月首次提出。

他用一句话概括了这种全新的编程方式：

「I just vibe. I don't even touch the keyboard sometimes. I just talk to the AI, it writes the code, I review it, and we iterate.」

翻译过来就是：你只管描述你的「感觉」，AI 来写代码，你审查，然后来回迭代。

简单来说，Vibe Coding 就是：你用人话告诉 AI 你想要什么功能，AI 帮你把代码写出来，不需要纠结语法细节、不需要记忆 API 参数、不需要手动调试每一个错误——这些都由 AI 来处理。

我们的角色从「写代码的人」转变为「描述需求的人」，或者说——从程序员变成了产品经理+架构师。

Vibe Coding 不是让 AI 替代你思考，而是让 AI 处理低价值的重复劳动，让你专注于更有创造性的部分：理解问题、设计架构、验证结果。


## Vibe Coding vs 传统编程

理解 Vibe Coding 与传统的编程方式有什么不同，有助于你更好地使用它。


## 为什么现在可以 Vibe Coding

Vibe Coding 之所以在 2025 年成为可能，是因为几个关键条件的成熟。


### 大模型编码能力的飞跃

GPT-5.5、Claude 5、Gemini 等模型在代码生成方面的准确率大幅提升。

它们不仅能写出语法正确的代码，还能理解项目上下文、遵循最佳实践、处理边界情况。

更重要的是，它们可以处理超长上下文——一次性阅读整个项目，理解你的代码库结构。


### AI 编程工具的爆发

Cursor、Claude Code、GitHub Copilot、Windsurf 等工具将 AI 能力深度集成到了开发流程中。

这些工具不仅能补全代码，还能直接修改文件、运行终端命令、搜索代码库——像一个真正的开发者一样工作。


### Agent 模式的出现

Agent 模式的工具可以自主执行多步骤任务：读取文件、编写代码、运行测试、根据测试结果修复错误。

你只需要下达一个初始指令，Agent 会自己循环迭代直到任务完成。


## 主流工具介绍

以下是目前最主流的 Vibe Coding 工具，各有侧重。

如果你是第一次接触 Vibe Coding，可以先使用国内的 Qoder 或 Trae 开始，操作类似 VS Code，学习曲线最平缓，且不会改变你熟悉的编辑器环境。


## 快速开始

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


## Vibe Coding 核心工作流

Vibe Coding 的核心工作流可以概括为四个步骤：描述、审查、迭代、交付。


### 完整工作流图示

```text
描述需求
    ↓
AI 生成代码
    ↓
你审查 Diff
    ↓
  ┌─ 不满意 → 描述修改意见 → AI 重新生成
  │
  └─ 满意 → 运行测试
              ↓
            ┌─ 测试失败 → 把报错贴给 AI → 修复
            │
            └─ 测试通过 → 提交代码
```


### 第一步：描述需求

用自然语言告诉 Claude Code 你想要什么。

不需要写代码，不需要说技术细节，说清楚「做什么」即可。

一个简单的需求描述示例：

```text
帮我创建一个 Python Flask 项目，有一个 /api/tasks 接口，
支持 GET 获取任务列表和 POST 创建新任务，
任务数据用 JSON 文件存储。
```

Claude Code 收到后会自己规划文件结构、生成代码、安装依赖、运行测试。


### 第二步：审查 Diff

Claude Code 生成代码后，会展示所有改动（Diff）供你审查。

这是 Vibe Coding 中最重要的环节——你必须看懂 AI 改了什么。

审查时重点关注：

审查不是为了找茬，而是确保你理解每一行代码在做什么。如果你看不懂某段代码，直接问 Claude Code：「这段代码是什么意思？为什么要这样写？」


### 第三步：迭代修改

审查发现问题后，用自然语言描述你想要的修改。

常见的迭代指令示例：

```text
把 JSON 文件存储改成 SQLite，用 SQLAlchemy 做 ORM。
```

```text
给 POST 接口加个验证：title 必填，不能为空字符串。
```

```text
报错了，看一下：
Traceback (most recent call last):
  File "app.py", line 42, in create_task
    db.session.add(task)
AttributeError: 'NoneType' object has no attribute 'session'
```

每次迭代后，Claude Code 会重新生成代码并展示 Diff，你再次审查，直到满意为止。


### 第四步：交付

当所有功能符合预期且测试通过后，提交代码。

Claude Code 会帮你写好 commit message 并提交：

```text
$ git log --oneline
a1b2c3d feat: add task CRUD API with SQLite storage
```


## 实战演示：用 Claude Code 从零构建一个 Todo 应用

下面通过一个完整的实战案例，演示 Vibe Coding 的整个流程。

我们将用 Claude Code 从零构建一个包含前端页面和后端 API 的 Todo 应用。


### 项目目标


### 第一步：初始化项目

在终端中创建项目目录并启动 Claude Code：

```text
$ mkdir vibe-todo && cd vibe-todo
$ claude
```

然后向 Claude Code 描述你的需求：

```text
帮我创建一个 Todo 应用，要求：
1. 后端用 Python Flask + SQLAlchemy + SQLite
2. 前端用纯 HTML/CSS/JS，风格简约现代
3. 支持添加、完成、删除、筛选任务
4. 所有 API 返回 JSON，前端用 fetch 调用
5. 代码注释用中文
```


### 第二步：Claude Code 做了什么

Claude Code 收到需求后，自动完成了以下步骤：

首先创建项目结构：

```text
vibe-todo/
├── app.py              # Flask 主应用
├── models.py           # 数据库模型
├── requirements.txt    # 依赖清单
├── static/
│   ├── style.css       # 样式文件
│   └── script.js       # 前端逻辑
└── templates/
    └── index.html      # 页面模板
```

然后生成后端代码，以下是 app.py 的核心内容：


## 实例

还有数据库模型 models.py：


## 实例


### 第三步：审查代码

Claude Code 展示 Diff 后，你逐行审查。

你可能会发现一些问题并提出修改意见。

例如，你注意到 API 路由没有统一前缀，提出修改：

```text
把所有 API 路由加上 /api/v1 前缀，方便以后版本管理。
```

Claude Code 会自动修改所有路由，你再次审查通过。


### 第四步：运行测试

审查通过后，让 Claude Code 启动应用并测试：

```text
$ python app.py
 * Running on http://127.0.0.1:5000
```

打开浏览器访问 http://127.0.0.1:5000，可以看到完整的 Todo 应用界面。

测试添加任务功能：

```text
$ curl -X POST http://127.0.0.1:5000/api/v1/tasks \
  -H "Content-Type: application/json" \
  -d '{"title": "学习 Vibe Coding"}'
```

返回结果：

```text
{
  "completed": false,
  "created_at": "2026-06-24T10:30:00",
  "id": 1,
  "title": "学习 Vibe Coding"
}
```


### 第五步：提交代码

所有功能验证通过后，提交代码：

```text
$ git add .
$ git commit -m "feat: 完成 Todo 应用基础功能"
```

整个实战过程，你一行代码都没有手动写。你做的事情是：描述需求、审查 Diff、描述修改、运行测试、提交代码。这就是 Vibe Coding 的核心体验。


## 后续章节

- 写好提示词的技巧
- 四要素模型
- 好提示词 vs 差提示词
- 常见误区与注意事项
- 误区一：AI 可以替代所有编程知识
- 误区二：一次性描述所有功能
- 误区三：不读 AI 写的代码
- 注意事项
- 适合 Vibe Coding 的场景

## 复习重点

- 能说明 `Vibe Coding` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
