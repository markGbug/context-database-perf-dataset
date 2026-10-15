# Claude Code：Claude Code 实战

- 来源：[Claude Code 实战](https://www.runoob.com/claude-code/claude-code-todo.html)
- 分类：AI / 智能开发
- 技术：Claude Code
- 笔记类型：学习笔记
- 章节序号：0174

## 本章内容

本章从打开终端到跑通一个完整的 Todo REST API，全程由 Claude Code + DeepSeek V4 驱动。

Claude Code + DeepSeek V4 配置参考：Claude Code DeepSeek 配置

先来看下 Claude Code 的基本操作界面和日常高频命令。


### 启动你的第一个 Claude Code 会话

打开终端，进入任意一个工作目录（或新建一个空文件夹），然后输入：

```text
$ mkdir runoob-todo-api
$ cd runoob-todo-api
$ claude
```

首次启动会看到欢迎界面和版本信息以及 DeepSeek 的环境变量配置。

如果不确定配置是否生效，进入后立刻输入 /status，确认 Base URL 指向的是 https://api.deepseek.com/anthropic。


### 常用斜杠命令速查表

在 Claude Code 的对话框中，以 / 开头的是内置命令，不会发送给模型。


### 权限提示机制

当 Claude Code 准备写入文件、执行命令时，它会先暂停，列出将要做的操作，等待你确认。

这是 Claude Code 最重要的安全机制，初学者不必担心 AI 失控乱改。

你会看到类似这样的提示：

```text
┌─────────────────────────────────────────────────┐
│  Claude wants to create the following files:     │
│                                                  │
│  • src/index.js                                  │
│  • src/routes/todos.js                           │
│  • package.json                                  │
│                                                  │
│  Allow? [Y/n]                                    │
└─────────────────────────────────────────────────┘
```

直接按 Enter 或输入 y 确认，输入 n 跳过。


## 实战项目：用 AI 从零搭一个 Todo API

本节带你用自然语言驱动 Claude Code，从零生成一个可运行的 Node.js REST API。


### 项目目标

我们要搭建一个具备以下功能的 REST API：

技术栈：Node.js + Express，数据暂存于内存（不需要数据库，降低复杂度）。


### 步骤 1：用自然语言描述需求

在 Claude Code 的对话框中输入以下内容（直接复制粘贴即可）：

```text
请帮我从零创建一个 Node.js + Express 的 Todo REST API 项目。

要求：
- 支持 GET /todos、POST /todos、PUT /todos/:id、DELETE /todos/:id 四个接口
- 数据先存在内存数组里，不需要数据库
- 每个 todo 包含：id、title、completed（布尔值）、createdAt 字段
- 请求和响应都使用 JSON 格式
- 加上基础的错误处理（404、400 等）
- 生成一份 README.md，说明如何启动和测试接口

项目结构建议：
my-todo-api/
├── src/
│   ├── index.js       # 入口文件
│   └── routes/
│       └── todos.js   # Todo 路由
├── package.json
└── README.md
```

写好提示词的三个要素：上下文（告诉 AI 技术栈和项目背景）、约束（明确你不想要什么）、期望输出（给出具体的文件结构或格式要求）。


### 步骤 2：Claude Code 生成文件结构

确认权限后，Claude Code 会依次创建以下文件。

生成过程中，有很多权限确认，一般直接选 Yes 就好了：

查看下生成的项目结构：


## 实例


## 实例


## 实例


### 步骤 3：审查并确认修改

Claude Code 生成代码后，不要急着直接运行，养成审查习惯。

你可以在对话中继续追问：

```text
你帮我生成的代码我看了一下，有几个问题想确认：
1. POST /todos 时，如果 title 是数字类型会怎么处理？
2. PUT 接口能同时更新 title 和 completed 吗？
3. 有没有对 id 不是数字的情况做处理？
```

Claude Code 会逐一回答，并可以当场修正代码。

这种「生成 → 质疑 → 修正」的循环是与 AI 协作的核心节奏。


### 步骤 4：安装依赖并启动服务

在 Claude Code 对话框中输入：

```text
请帮我安装依赖并启动项目，然后告诉我怎么用 curl 测试每个接口
```

Claude Code 会执行以下操作（每步都会请求你确认）。

```text
$ npm install
```

输出示例：

```text
added 64 packages in 2.3s
```

```text
$ npm start
```

输出：

```text
Server is running on http://localhost:3000
```

新开一个终端窗口，依次运行以下 curl 命令：

```text
# 创建第一条 Todo
$ curl -X POST http://localhost:3000/todos \
  -H "Content-Type: application/json" \
  -d '{"title": "学习 Claude Code"}'

# 创建第二条 Todo
$ curl -X POST http://localhost:3000/todos \
  -H "Content-Type: application/json" \
  -d '{"title": "完成 DeepSeek 配置"}'

# 获取所有 Todos
$ curl http://localhost:3000/todos

# 把第一条标记为完成
$ curl -X PUT http://localhost:3000/todos/1 \
  -H "Content-Type: application/json" \
  -d '{"completed": true}'

# 删除第二条
$ curl -X DELETE http://localhost:3000/todos/2

# 再次查看列表，确认删除成功
$ curl http://localhost:3000/todos
```

```text
[
  {
    "id": 1,
    "title": "学习 Claude Code",
    "completed": true,
    "createdAt": "2026-05-20T10:30:00.000Z"
  }
]
```

恭喜，你的第一个 AI 辅助开发的 API 跑起来了。


### 进阶挑战：让 Claude Code 帮你加新功能

API 跑通之后，试着用自然语言让 Claude Code 扩展功能：

```text
请给 Todo API 加上以下功能：
1. GET /todos 支持 ?completed=true/false 的查询参数过滤
2. GET /todos 支持 ?sort=createdAt&order=desc 的排序参数
3. 同时更新 README.md 里的接口文档
```

观察 Claude Code 如何理解已有代码结构，精准地在正确位置插入新逻辑，而不是重写整个文件。

这正是它比普通代码生成工具强的地方。


## CLAUDE.md：项目记忆文件

CLAUDE.md 是 Claude Code 的项目级记忆文件，让 AI 每次启动时自动了解项目规范。


### 为什么需要它

Claude Code 每次启动都是「全新的」——它不记得上次会话说过什么。

但如果项目根目录有一个 CLAUDE.md 文件，Claude Code 每次启动时会自动读取它，相当于给 AI 的「项目说明书」。

没有 CLAUDE.md 的痛点：

- 每次都要重新解释「我们用 Express 不用 Koa」
- AI 忘了你的命名规范，又生成了驼峰命名的文件
- 团队成员各自和 AI 说不同的约定，代码风格混乱


### CLAUDE.md 写法模板

在项目根目录创建 CLAUDE.md，内容参考以下模板：

```java
# 项目说明（CLAUDE.md）

## 项目概述
这是一个 Node.js + Express 的 Todo REST API 项目。
当前阶段：数据存在内存中，下一步会迁移到 SQLite。

## 技术栈
- 运行时：Node.js 18+
- 框架：Express 4.x
- 测试：（暂无，后续加 Jest）
- 代码风格：ESLint + Prettier（配置见 .eslintrc）

## 目录结构
src/
├── index.js        # 入口，只做 app 配置和监听
└── routes/
    └── todos.js    # Todo 业务逻辑全在这里

## 命名规范
- 文件名：kebab-case（如 todo-service.js）
- 变量/函数：camelCase
- 常量：UPPER_SNAKE_CASE
- 路由文件按资源名命名（如 users.js、products.js）

## 重要约定
- 所有接口返回 JSON，错误统一格式：{ "error": "错误描述" }
- HTTP 状态码语义要准确：创建成功用 201，删除成功用 204
- 禁止在路由文件里直接操作数据库（现在是内存数组，将来是 DB）
- 每个路由文件只处理一种资源

## 禁止事项
- 不要用 var，只用 const/let
- 不要用回调风格，统一用 async/await
- 不要在代码里写中文注释（英文注释即可）
- 不要安装 lodash，原生 JS 方法够用

## 启动方式
npm start          # 生产模式
npm run dev        # 开发模式（nodemon 热重载）

## 测试接口
见 README.md 的 curl 示例
```


### 让 Claude Code 自动生成 CLAUDE.md

不想手写？直接让 AI 帮你生成：

```text
请根据当前项目的代码结构和我们的对话记录，
帮我生成一份 CLAUDE.md 文件，
内容包括项目概述、技术栈、目录结构、命名规范和重要约定。
```

Claude Code 会分析所有已生成的文件，自动整理出适合本项目的 CLAUDE.md。


### CLAUDE.md 的维护节奏

把 CLAUDE.md 提交到 Git，团队所有成员和 AI 就共享同一份规范。

这是 AI 辅助团队协作的基础设施。


## 本章小结


## 复习重点

- 能说明 `Claude Code 实战` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
