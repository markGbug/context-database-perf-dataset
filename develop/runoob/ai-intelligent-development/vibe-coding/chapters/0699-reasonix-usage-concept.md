# Vibe Coding：Reasonix 入门教程

- 来源：[Reasonix 入门教程](https://www.runoob.com/vibe-coding/reasonix-usage.html)
- 分类：AI / 智能开发
- 技术：Vibe Coding
- 笔记类型：概念卡
- 章节序号：0699

## 本章内容

Reasonix 是一个专为 DeepSeek 深度优化的开源终端 AI 编程 Agent，整个运行循环围绕 DeepSeek 的 prefix-cache 机制从零设计，目标是让 AI 编程足够便宜，可以一直挂着跑。

Reasonix的设计哲学："A coding agent that stays cheap enough to leave on."（足够便宜，可以一直挂着跑的编程 Agent）。


### 适合谁用？


### Reasonix 不做的事情

Reasonix 是有主见的，以下是它刻意不做的事：

使用 Reasonix 前需要获取 DeepSeek API Key，访问 platform.deepseek.com/api_keys，登录或注册账号。

点击 创建 API key，命名（如 reasonix），复制保存。

首次运行 reasonix 时会提示粘贴 API Key，输入后自动持久化，以后不需要再输。


## 安装：CLI 与桌面版

Reasonix 提供 CLI 和桌面版两种安装方式，下面分别介绍。


### CLI 安装

系统要求：Node.js ≥ 22，支持 macOS、Linux、Windows（PowerShell、Git Bash、Windows Terminal）。

全局安装（推荐日常使用）：

```text
npm install -g reasonix
```

免安装体验（npx，始终使用最新版）：

```text
# 进入项目目录，直接使用 npx 运行
cd my-project
npx reasonix code
```

验证与健康检查，查看版本号：

```text
reasonix --version
```

健康检查：Node 版本、API Key 可达性、MCP 配置：

```text
reasonix doctor
```

升级到最新版：

```text
reasonix update
```

通过交互式向导完成配置，始化 API Key、语言、主题等配置。

```text
reasonix setup
```

选择语言：

选择主题：

输入 DeepSeek API key：

回车保存：

接下来进入项目 vibe-coding-runoob，就可以开始使用了：

```text
cd vibe-coding-runoob
```

输入以下命令开始使用：

```text
reasonix
```

输入 / 查看支持的命令：


### 桌面版安装

桌面版是基于 Tauri 的原生客户端，多标签，右侧面板显示 Agent 本次会话读取或编辑过的文件。

底部显示与 CLI 顶栏相同的费用/缓存/Token 计数器。使用相同的 DeepSeek API Key 和 ~/.reasonix 配置。

桌面版内置 Node 运行时，无需单独 npm install。

从官网（https://reasonix.io/#start）下载对应平台安装包：

下载后，双击安装，然后输入 API key：

启动后，桌面也是经典的左右布局：

输入框输入信息就可以开始对话了：

点击右上角图标，可以打开三栏布局：

三种协作方式：

常用设置，包含主题、外观、语言、插件、MCP 等：

首次启动注意事项：

macOS 第一次启动会触发 Gatekeeper 拦截。一次性解除：在终端执行 xattr -dr com.apple.quarantine /Applications/Reasonix.app，或右键点击 → 打开 → 确认。

Windows：SmartScreen 显示「未知发布者」，点击「更多信息 → 仍要运行」。Linux：.deb 和 .AppImage 直接运行，无需额外步骤。

桌面版目前是 Prerelease 状态，循环和协议与 CLI 完全相同，但 UI 仍在打磨中，安装包暂未代码签名。CLI 是主要开发界面，任何 CLI 中有的功能桌面版的输入框都能用。


## 第一次运行

进入项目目录，启动 Reasonix 编程模式。

```text
cd your-project

# 启动编程模式（以下两种方式等价）
reasonix code
# 或者直接
reasonix
```

试着发送第一条消息：

```text
分析这个项目的目录结构，告诉我主要模块的职责
```

Reasonix 会调用 list_directory、read_file 等工具扫描项目，输出结构化分析。


### 无头运行（管道友好）

```text
# 单次执行，结果流式输出到 stdout
reasonix run "统计 src 目录中每个 .ts 文件的行数，按从多到少排序"

# 结合 git diff 使用
git diff HEAD~1 | reasonix run "给这段 diff 写一个 Conventional Commits 格式的 commit message"
```


## 两种模式：code 与 chat

Reasonix 提供两种运行模式，适用于不同的使用场景。

code 是默认模式，也是唯一有文件系统和 shell 工具的模式，从这里开始。

chat 是更轻量的无磁盘访问模式——用于需要思考伙伴但不想让 AI 碰文件时，或者挂载 MCP 做信息检索时。

chat 模式系统 Prompt 更短，Token 成本更低。

Reasonix 把文件系统工具作用域绑定到启动目录，通过 --dir 重定向。中途切换目录不受支持（记忆路径会与旧的根路径混乱）——退出后重新启动。

```text
# 在指定目录下启动 code 模式
reasonix code --dir /path/to/other-project
```


## 编辑门控：SEARCH/REPLACE 预览流程

这是 Reasonix 最重要的安全机制——AI 永远不会在你不知情的情况下修改文件。


### 三种编辑门控模式

通过 /mode 或 Shift+Tab 切换：


### 典型编辑流程（review 模式）

```html
1. 你：帮我把 getUserById 函数加上错误处理

2. Reasonix 分析代码，提出 SEARCH/REPLACE 修改方案：

   ─── src/services/user.ts ───
   - async function getUserById(id: string) {
   -   const user = await db.users.findOne({ id });
   -   return user;
   - }
   + async function getUserById(id: string): Promise<User | null> {
   +   try {
   +     const user = await db.users.findOne({ id });
   +     return user ?? null;
   +   } catch (error) {
   +     logger.error({ id, error }, 'getUserById failed');
   +     throw new AppError('USER_FETCH_FAILED', 500);
   +   }
   + }

3. 你：/apply        ← 确认应用，文件写盘
        /discard      ← 丢弃不应用
        /walk         ← 逐块 git-add-p 风格审查
```


### 编辑历史

```html
# 列出本次会话的所有编辑批次
/history

# 查看某次编辑的 diff
/show <id>

# 回滚最近一次 /apply
/undo
```


## Plan 模式：只读分析门

Plan 模式让 Reasonix 进入只读状态——AI 只能读文件、分析代码、提出方案，不能写文件，不能执行命令，直到你明确批准计划。


### 开启与工作流

```text
/plan                ← 切换 Plan 模式（顶栏出现 PLAN MODE 标记）

你：我想把这个 Express 应用迁移到 Fastify，先给我分析影响范围

AI 分析后提交计划：
  ✓ 需要替换 5 个路由文件
  ✓ 3 个中间件需要适配
  ✓ 12 个测试需要更新
  预计改动：43 个文件，约 800 行

plan-confirm 模态框出现
  → Ctrl+P 展开/折叠完整计划详情
  → 批准后 AI 进入执行模式
  → 执行过程中每次修改仍走编辑门控
```


### 什么时候用 Plan 模式


## 模型与成本控制

Reasonix 提供灵活的模型切换和成本控制机制。


### 切换预设

```text
# 默认 smart（v4-flash + max 推理）
reasonix code

# 快速任务，v4-flash + high 推理，成本最低
reasonix code --preset fast

# 复杂任务，v4-pro + max 推理
reasonix code --preset max
```

会话中切换：

```text
/preset auto         # 开启自动升级逻辑（flash 优先，失败升级 pro）
/preset flash        # 锁定 flash
/preset pro          # 锁定 pro
```


### /pro 单次升级

用户输入 /pro，下一轮使用 v4-pro，然后自动解除。没有预设切换，没有忘记恢复。

激活状态显示为顶栏的黄色 "pro armed" 标记。

```text
> /pro
> 解释这段 Rust 异步代码里的生命周期标注为什么必须这样写
# 回答完成后自动恢复 v4-flash
```


### 失败自动升级

每轮计数可见的「flash 力不从心」事件：edit_file/write_file 的 SEARCH-not-found 错误，以及 ToolCallRepair 触发。

一旦计数达到 3，当前轮次的剩余部分自动切换到 v4-pro，并通过黄色警告行公告——没有静默成本。


### 设置会话预算上限

```text
# 本次会话上限 $0.50
reasonix code --budget 0.50
```

```text
/budget 0.20                     # 会话中设置 $0.20 上限
/budget off                      # 取消上限
```

到达 80% 时警告，到达 100% 时拒绝下一轮。


### 上下文压缩与费用查询

```text
/compact         # 手动将旧轮次折叠为摘要（缓存安全）
                 # 上下文达到 50% 时自动触发，这是手动触发

/cost            # 上一轮花费
/cost 这段文字   # 预估发送这段文字的成本
/stats           # 跨会话成本仪表板（今天/本周/本月/所有时间）
```


## 技能（Skills）：Markdown 可复用剧本

技能是 AI 可以按需调用的 Markdown 剧本，没有远程注册表——直接编写，立即生效。


### 创建技能

```html
# 项目级技能：<project>/.reasonix/skills/code-review.md
/skill new code-review

# 全局技能：~/.reasonix/skills/deploy-check.md
/skill new deploy-check --global
```


### 技能文件格式

文件路径：.reasonix/skills/code-review.md

```text
---
description: 对当前改动做系统性代码审查，按 P0-P3 优先级分级
runAs: subagent
tools: [read_file, list_directory, search_content]
---

分析 `git diff HEAD` 中的所有改动。

对每个发现的问题，按如下格式输出：

**[P0]** 严重（阻止合并）：安全漏洞、逻辑错误、数据丢失风险
**[P1]** 重要（强烈建议修复）：性能问题、错误处理缺失
**[P2]** 一般（建议修复）：代码质量、可读性
**[P3]** 改进（可选）：最佳实践、未来优化

每条包含：文件名和行号 · 问题描述（一句话）· 修复建议。

最后给出总体评估：是否可以合并，以及最重要的三个改进点。
```

runAs: subagent 让技能在隔离的子 Agent 循环中执行，主会话的上下文不会膨胀。


## 后续章节

- 调用与管理
- 兼容 Claude 格式的技能
- 记忆（Memory）：跨会话上下文持久化
- 手动写入
- 管理记忆
- 项目记忆文件（REASONIX.md）
- MCP 集成：连接外部工具
- 会话中动态添加
- 命令行挂载
- 配置文件预设（推荐）
- 实例
- 浏览 MCP 工具
- Hooks：生命周期自动化
- 支持的事件
- 配置示例
- 实例

## 记忆卡片

- 一句话定义：`Reasonix 入门教程` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
