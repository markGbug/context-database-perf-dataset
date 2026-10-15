# Hermes Agent：Hermes Agent 仪表盘（Dashboard）

- 来源：[Hermes Agent 仪表盘](https://www.runoob.com/hermes-agent/hermes-agent-web-dashboard.html)
- 分类：AI / 智能开发
- 技术：Hermes Agent
- 笔记类型：学习笔记
- 章节序号：0262

## 本章内容

Dashboard 是 Hermes 的 Web 可视化管理界面。

通过浏览器，你可以集中管理所有 Profile 的配置、模型、技能、MCP 服务器、定时任务和会话——无需记住任何命令行参数。

本章将逐一介绍 Dashboard 的每个功能模块，以及如何用它提升日常运维效率。


## 仪表盘（Dashboard） 是什么

如果把命令行比作 Hermes 的终端界面，仪表盘（Dashboard） 就是它的控制中心。

Dashboard 是一个本地运行的 Web 应用，通过浏览器访问，提供图形化的管理体验。

它的核心价值在于：

- 多 Profile 统一管理：在同一个界面中切换和管理所有 Profile，无需反复启动不同的终端窗口
- 可视化配置：下拉菜单选择模型、拖拽启用技能、一键安装 MCP 服务器，降低配置门槛
- 用量一目了然：Token 消耗、费用统计、会话历史以图表形式展示
- 在线聊天：直接在浏览器中与任意 Profile 的 Agent 对话，测试配置效果

Dashboard 不是命令行的替代品，而是互补工具。命令行适合快速操作和脚本化，Dashboard 适合浏览、探索和管理。


## 启动与访问


### 基本启动

一条命令即可启动 Dashboard：

```text
hermes dashboard
```

启动后，在浏览器中打开 http://localhost:9119 即可访问。


### 启动选项

```text
# 启动并预选指定 Profile（跳过 Profile 选择步骤）
coder dashboard

# 指定自定义端口
hermes dashboard --port 8080

# 绑定到所有网络接口（谨慎使用，建议配合防火墙）
hermes dashboard --port 8080 --host 0.0.0.0
```

默认 Dashboard 只绑定 127.0.0.1，仅本机可访问。如果你需要在其他设备上访问（比如在服务器上部署后远程管理），使用 --host 0.0.0.0 并配合防火墙规则限制来源 IP。


### Docker 环境中启动

在 Docker 部署中，Dashboard 作为独立服务运行：


## 实例


## 功能模块详解


### Profile 切换器

侧边栏顶部是 Profile 切换器，这是 Dashboard 最重要的导航组件。

它的核心能力是在不同 Profile 之间即时切换，无需重启 Dashboard：

- 下拉菜单列出所有已创建的 Profile（default、coder、researcher 等）
- 切换后，下方所有模块——Models、Skills、MCP、Chat——自动刷新为当前 Profile 的数据
- 当前选中的 Profile 名称始终显示在顶部，避免误操作

这解决了多 Profile 管理中最常见的痛点：之前你需要记住「coder 的模型是什么、researcher 装了什么技能」，现在切换一下就能看到全部。


### Models 模型管理

Models 模块负责模型配置和用量监控，是 Dashboard 中使用频率最高的功能之一。

主模型配置：从下拉菜单选择默认使用的模型，支持按提供商（OpenAI、Anthropic、OpenRouter 等）筛选。

切换模型后，配置即时生效——当前会话使用旧模型，新会话使用新模型。

辅助模型配置：为特定任务指定独立模型以降低费用：

用量与费用统计：Models 页面以图表形式展示：

- 每个模型的累计 Token 消耗（输入 + 输出）
- 按美元估算的累计费用
- 近期用量趋势（过去 7 天 / 30 天）
- 按 Profile 分组的用量对比

辅助模型是控制成本最有效的手段。以 background_review 为例——使用 claude-sonnet 每次回顾可能花费 $0.02，换成 gemini-flash 可能只需 $0.001。每日几十轮对话下来差距可观。


### Skills 技能管理

Skills 模块提供了一个完整的技能管理界面，覆盖从浏览到安装到创建的全生命周期。

技能浏览与搜索：

- 网格视图展示所有已安装的技能，每个卡片显示名称、描述和分类标签
- 搜索框支持按名称和描述关键词过滤
- 按分类目录（software-development、research、devops 等）分组浏览

技能安装：

- 一键安装内置可选技能
- 从 agentskills.io Hub 搜索并安装社区技能
- 从 URL 直接安装技能（粘贴 SKILL.md 的公开链接）
- 安装后自动出现在斜杠命令列表中

Learn a skill 面板：这是 Dashboard 独有的功能——图形化的 /learn 命令面板。

它提供三个输入框，对应三种学习来源：

填写任意一个或多个输入框后，点击 Learn 按钮，Agent 会收集材料并生成 SKILL.md 草稿，你预览后确认保存。


### MCP 服务器管理

MCP 模块将命令行的 hermes mcp 操作转化为可视化界面。

MCP 目录浏览：

- 网格视图展示 Nous 精选目录中的所有条目
- 每个条目显示名称、描述和当前状态（available / enabled / disabled）
- 状态标签用颜色区分——绿色 enabled、灰色 available、黄色 disabled

安装与配置：

- 点击条目进入详情页，查看服务器暴露的工具列表
- 一键安装——自动引导配置 API Key 或 OAuth 登录
- 安装后可在工具选择界面勾选要启用的具体工具（include/exclude 过滤）

已安装服务器管理：

- 查看所有已安装服务器的详细信息
- 重新配置工具选择列表
- 启用/禁用服务器，无需编辑 config.yaml
- 测试服务器连接状态


### Chat 在线聊天

Chat 模块让你在浏览器中直接与当前 Profile 的 Agent 对话。

它的界面类似于消息应用，支持：

- 文本消息输入与流式回复显示
- 工具调用过程实时展示（可以看到 Agent 正在调用哪个工具，参数和结果是什么）
- 消息历史保留在当前会话中（关闭浏览器标签后不保留）
- 支持所有斜杠命令（/new、/skills、/memory 等）

Chat 模块的主要用途是快速测试配置效果——修改模型或技能配置后，无需切换到终端，直接在 Dashboard 里发送一条消息验证。

Chat 模块的会话是临时的——关闭标签页后对话历史不会保留。如果你需要持久化的聊天体验，使用 CLI（hermes chat）或消息平台（Telegram/Discord）。


### Cron 定时任务管理

Cron 模块提供定时任务的可视化创建和管理。

任务列表：

- 表格展示所有定时任务，列包含：名称、调度计划、目标平台、状态（启用/暂停）
- 支持按状态筛选（全部 / 运行中 / 已暂停）
- 每个任务旁有快捷操作按钮：立即执行一次、暂停、恢复、删除

创建任务：图形化的任务创建表单，字段包括：

- 任务名称（唯一标识）
- 调度计划——支持自然语言输入（如「every day at 8am」）和 cron 表达式
- Prompt 内容——Agent 每次执行的任务描述
- 目标平台——任务结果投递到哪里
- 目标聊天 ID——投递到哪个具体会话
- 启用的工具集——任务执行时可用的工具

执行历史：查看每次执行的触发时间、完成状态和简要结果摘要。


### 其他功能

配置管理：Dashboard 的部分页面可以直接编辑 config.yaml 的常用设置，包括：

- 终端后端切换（local / docker / ssh 等）
- 审批模式设置（manual / smart / off）
- 显示偏好（记忆通知详细程度等）

检查点管理：查看和恢复文件系统检查点，与命令行的 hermes checkpoints list 功能一致。

插件管理：查看已安装插件、启用或禁用插件。


## Dashboard 最佳实践


### 日常使用场景


### 安全建议

- Dashboard 默认只绑定 127.0.0.1，如需远程访问，务必配置防火墙规则限制来源 IP
- 不要在不可信的网络中暴露 Dashboard 端口
- Docker 部署时，Dashboard 服务应放在 internal 网络中（仅内部可访问），通过 Gateway 的端口映射从外部访问


## 常用命令速查

```text
# ─── 启动 Dashboard ─────────────────────────────────────────
hermes dashboard                    # 默认端口 9119，仅本机访问
hermes dashboard --port 8080        # 指定端口
coder dashboard                     # 启动并预选 coder Profile

# ─── Docker 中运行 ──────────────────────────────────────────
docker run -d \
  --name hermes-dashboard \
  -v ~/.hermes:/home/hermes/.hermes \
  -p 127.0.0.1:9119:9119 \
  nousresearch/hermes-agent:latest \
  hermes dashboard

# ─── Dashboard 中可执行的操作 ──────────────────────────────
# Models 页：选择主模型、配置辅助模型、查看用量统计
# Skills 页：浏览、搜索、安装技能，使用 Learn a skill 面板
# MCP 页：浏览目录、一键安装、管理工具过滤
# Chat 页：在线与 Agent 对话，测试配置效果
# Cron 页：创建、暂停、恢复定时任务，查看执行历史
```


## 复习重点

- 能说明 `Hermes Agent 仪表盘` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
