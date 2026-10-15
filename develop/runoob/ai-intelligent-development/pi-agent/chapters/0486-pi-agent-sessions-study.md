# Pi Agent：Pi Agent 会话管理

- 来源：[Pi Agent 会话管理](https://www.runoob.com/pi-agent/pi-agent-sessions.html)
- 分类：AI / 智能开发
- 技术：Pi Agent
- 笔记类型：学习笔记
- 章节序号：0486

## 本章内容

Pi Agent 的会话管理系统是其最强大的特性之一。

本章详细介绍会话的保存、恢复、分支和导出。


## 会话存储机制

每次对话会自动保存为一个会话文件，以 JSONL 格式存储在 ~/.pi/agent/sessions/ 中，按项目路径分类。

目录名由项目的绝对路径转换而来：斜杠替换为连字符，并在前后各包裹一个 --。

文件名由创建时间戳和会话 UUID 拼接而成。

每个会话内部以树状结构组织——这意味着你可以在任意历史节点分叉，而不会丢失之前的对话内容。

```text
~/.pi/agent/sessions/
└── --Users-runoob-projects-runoob-demo--/        # 目录名为项目路径，斜杠已替换为连字符
    ├── 2026-08-31T02-40-11-000Z_019fc2a1-93b4-7c22-8d5e-2b3c4d5e6f7a.jsonl    # 时间戳_UUID.jsonl
    ├── 2026-08-31T04-12-38-000Z_2c8f71ba-4a19-4e63-9d02-7f5a6b8c9d0e.jsonl
    └── 2026-08-31T08-55-02-000Z_5e3d92f4-8b26-47ac-a174-9c0d1e2f3a4b.jsonl
```


### 会话文件的内部结构

会话文件的第一行是一条固定的元数据，记录会话格式版本、会话 ID、创建时间与工作目录。

这条元数据没有 id 和 parentId 字段，不参与对话树。

从第二行开始每行一个条目，都带有 id 与 parentId 字段，二者共同构成树状结构。

条目类型包括 message、compaction、branch_summary、label、custom 等。

由 /fork 或 /clone 创建的会话，首行元数据还会多一个 parentSession 字段，指向原会话文件。

```text
{"type":"session","version":3,"id":"019fc2a1-93b4-7c22-8d5e-2b3c4d5e6f7a","timestamp":"2026-08-31T02:40:11.000Z","cwd":"/Users/runoob/projects/runoob-demo"}
{"type":"message","id":"m1","parentId":null,"message":{"role":"user","content":[{"type":"text","text":"帮我实现登录功能"}]}}
{"type":"message","id":"m2","parentId":"m1","message":{"role":"assistant","content":[{"type":"text","text":"好的，我用 JWT 来实现"}]}}
```

会话目录也可以自定义，优先级从高到低依次为：--session-dir 参数、环境变量 PI_CODING_AGENT_SESSION_DIR、settings.json 中的 sessionDir。


## 启动时的会话选项

通过命令行参数在启动时控制会话行为：

```text
$ pi -c
Resumed session abc123-def456 (42 messages, model claude-sonnet-4-5)

$ pi -r
┌ 选择要恢复的会话：
│ > abc123  快速审查      3 分钟前
│   def456  重构认证模块  2 小时前
└

$ pi --session ~/.pi/agent/sessions/--Users-runoob-projects-runoob-demo--/2026-08-30T09-15-04-000Z_019fbb5d-7a2e-7f31-b5c4-1a2b3c4d5e6f.jsonl
Resumed session 019fbb5d-7a2e-7f31-b5c4-1a2b3c4d5e6f

$ pi --session abc123
Resumed session abc123-def456

$ pi --fork abc123
Forked to session 9f2e7a01-5c48

$ pi --name "重构认证模块"
Session renamed: 重构认证模块

$ pi --no-session
Temporary session (will not be saved)
```


## 会话管理命令

进入交互模式后，以下命令覆盖了会话的日常管理工作。


### /resume 会话选择器

输入 /resume 或用 pi -r 启动，会打开当前项目的会话选择器。

在列表中直接输入字符即可过滤会话，其余操作按键如下：


## 会话树（/tree）

这是 Pi Agent 最独特的特性——会话以树状结构存储，你可以在任意历史节点分叉。


### 树的结构

以下是一个典型的会话树结构：

```text
├─ user: "帮我实现一个登录功能..."
│  └─ assistant: "好的，我来实现..."
│     ├─ user: "用 JWT 方案..."
│     │  └─ assistant: "使用 JWT 实现..."
│     │     └─ user: "测试通过了"  ← 当前活跃分支
│     └─ user: "还是用 Session 方案..."
│        └─ assistant: "使用 Session 实现..."
```

在这个例子中，你从同一个起点出发，分别探索了 JWT 和 Session 两个方案，每个方案的对话都被完整保留。


### 树浏览器操作

打开 /tree 后，用以下按键在树中移动和选择。


### 过滤模式

过滤模式决定树浏览器中显示哪些条目，按 Ctrl+O 循环切换。

选中用户消息会将其文本填入编辑区，让你可以重新编辑并提交，创建新的分支。

选中 AI 回复或工具调用则会直接跳转到那个位置，让你可以从那里继续对话。


## /tree 与 /fork 与 /clone 的区别

三者都能回到历史位置，差别在于是否产生新的会话文件，以及能看到多大范围的对话。


## 分支摘要

当你通过 /tree 从一个分支跳到另一个分支时，Pi Agent 可以为你生成被放弃分支的摘要。

这个摘要会附加到新的位置，让你知道之前的分支做了什么：

你可以在 ~/.pi/agent/settings.json 中控制摘要行为：


## 实例

设置 skipPrompt 为 true 可以在 /tree 导航时跳过「是否生成摘要」的提问。

跳过提问后默认不生成摘要，直接跳转到目标位置。


## 导出与分享会话

会话可以导出为本地文件，也可以直接上传生成分享链接。


### 导出为 HTML

导出会生成一个可直接在浏览器打开的单文件页面，适合离线查看。

```text
# 导出到默认位置
/export

# 导出到指定文件
/export ~/Desktop/my-session.html
```


### 分享为 GitHub Gist

不想传文件时，用 /share 一条命令生成在线链接。

```text
/share
```

执行后会创建一个私有 GitHub Gist，并生成可分享的 HTML 链接。


### 命令行导出

不进入交互模式也可以导出已有会话。

```text
$ pi --export session.jsonl output.html
Exported to output.html (128 KB)
```

如果你做开源项目并希望将会话发布用于研究目的，可以查看 pi-share-hf 工具，它可以将会话发布到 Hugging Face 数据集。


## 复习重点

- 能说明 `Pi Agent 会话管理` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
