# LangChain：LangChain 对话记忆——Checkpointer

- 来源：[LangChain 对话记忆](https://www.runoob.com/langchain/langchain-checkpointer.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：学习笔记
- 章节序号：0291

## 本章内容

默认情况下，Agent 每次独立调用 invoke() 时，并不会自动记住上一次对话的内容。

例如，第一轮告诉 AI"我叫小明"，第二轮再问"我叫什么名字"，如果没有传入历史消息，Agent 通常无法回答。

LangChain 提供 Checkpointer（检查点保存器），通过保存和恢复 Agent State，让同一个对话线程具备多轮记忆能力。

本章节介绍 InMemorySaver、SqliteSaver、PostgresSaver、thread_id、状态管理、历史检查点以及对话记忆在实际项目中的应用。


## 一、没有 Checkpointer 会怎样？

先看一个不使用 Checkpointer 的示例。

每次调用 Agent，只发送当前用户问题，没有主动传入前面的消息。


### 实例：两次独立对话


## 实例

可能得到：

```text
第一轮：你好，小明！Python 是很适合入门的编程语言。

第二轮：你还没有告诉我你的名字。
```

原因在于，第二次调用时只传入了新的用户问题。

对于当前这次模型请求，Agent 无法自动获取上一轮独立调用的历史消息。

注意：没有 Checkpointer 并不代表完全无法实现多轮对话。你也可以在应用程序中手动维护消息历史，并在每次调用时一并传入。

Checkpointer 的优势是由 LangGraph 统一管理状态持久化，减少手动拼接历史消息的工作。


## 二、使用 InMemorySaver 记住对话

最简单的 Checkpointer 是 InMemorySaver，它将 Agent State 保存在 Python 进程内存中。

只需要在创建 Agent 时传入 checkpointer：

```text
checkpointer=InMemorySaver()
```

然后通过 thread_id 标识一个对话线程。


### 完整实例：两轮对话记忆


## 实例

第二轮可能得到：

```text
你叫小明，正在学习 Python。
```

原因是两次调用都使用了相同的：

```text
thread_id = "learning-001"
```

LangGraph 会在下一次调用时恢复该线程已经保存的状态，然后合并本轮新增消息。

注意：模型的实际回复不是固定的。即使保存了历史，也不能保证模型每次都能准确回忆所有细节。


## 三、thread_id：对话线程标识

thread_id 是 Checkpointer 管理对话状态的关键参数。

同一个 thread_id 代表同一个逻辑对话线程，不同 thread_id 则用于区分不同会话。

一个用户可以有多个 thread_id：

```text
用户 user-001
    ├── chat-001：Python 学习
    ├── chat-002：Java 学习
    └── chat-003：项目调试
```

不同用户也可以使用同一个 Agent 实例，但必须为各自的会话分配独立线程。


### 实例：创建两个独立会话


## 实例

输出：

```text
Alice： 我是 Alice。
Bob： 我是 Bob。
```

这说明两个线程保存了不同的状态。

重要：thread_id 不是身份认证令牌，也不是安全隔离机制。Web 应用必须在后端检查当前用户是否有权限读取或继续某个 thread_id。

不能允许用户随意修改 URL 或请求参数，就能访问其他用户的对话。


## 四、Checkpointer 的工作原理

Checkpointer 不只是一个"聊天记录数据库"，它保存的是 LangGraph 执行过程中的状态检查点。

一个简化的执行过程：

```text
第一次 invoke()
    ↓
识别 thread_id
    ↓
读取已有 Checkpoint（如果存在）
    ↓
合并用户输入
    ↓
执行 Agent 节点
    ↓
保存状态检查点
    ↓
返回结果

第二次 invoke()（相同 thread_id）
    ↓
恢复该线程最新状态
    ↓
合并新的用户消息
    ↓
继续执行 Agent
    ↓
保存新的检查点
```

检查点可以记录：

- 消息历史 messages。
- 自定义 AgentState 字段。
- 当前执行状态。
- 后续待执行节点。
- 与执行恢复相关的检查点信息。

LangGraph 可以在执行过程中按步骤创建检查点，而不只是任务全部结束后才保存。

这也是 Checkpointer 能支持中断恢复和状态历史查看的重要原因。


## 五、查看当前对话状态 get_state()

使用 agent.get_state(config) 可以读取指定线程当前保存的 State。

返回的是 StateSnapshot，其中包含状态值以及执行相关信息。


### 实例：查看消息和执行状态


## 实例

对于已经正常完成的简单 Agent，state.next 通常是：

```text
()
```

表示当前检查点没有等待执行的后续节点。

如果 Agent 处于中断或等待状态，state.next 可能包含待执行节点名称。


### StateSnapshot 常用属性

注意：必须先有对应线程的检查点，才能读取有意义的历史状态。


## 六、查看多轮对话的状态变化

下面通过三次连续调用，观察消息历史如何增加。


### 实例：三轮对话


## 实例

如果每轮只有一次模型回答，可能得到：

```text
第1轮：消息数=2，next=()
第2轮：消息数=4，next=()
第3轮：消息数=6，next=()
```

但如果模型使用工具或 Middleware 添加了消息，实际消息数量可能更多。

因此，不能简单假设"每轮必定增加两条消息"。


## 七、Checkpointer 的类型

LangGraph 提供多种检查点存储实现，可以根据应用规模选择。

对应安装方式：

```text
# 基础 Checkpointer
pip install -U langgraph

# SQLite
pip install -U langgraph-checkpoint-sqlite

# PostgreSQL
pip install -U langgraph-checkpoint-postgres "psycopg[binary]"
```

其中，InMemorySaver 随 LangGraph 基础依赖提供，SQLite 与 PostgreSQL 的检查点实现需要额外安装。

生产部署还应考虑数据库访问权限、连接池、备份、状态清理以及敏感信息保护。


## 八、SqliteSaver：将对话保存到数据库

SqliteSaver 可以把 Agent State 持久化保存到 SQLite 文件。

即使 Python 程序退出，只要数据库文件没有丢失，之后仍可以通过原来的 thread_id 恢复会话。

SQLite 很适合本地工具、小型学习项目和单机应用。


### 完整实例：SQLite 对话记忆

文件名：sqlite_memory.py


## 实例

运行后，程序会在当前工作目录创建或使用：

```text
conversations.db
```

数据库会保存该线程的状态检查点。


### 重新运行程序恢复历史

第二次启动程序时，仍然使用相同的数据库文件与 thread_id：


## 实例

如果之前的状态已经成功保存，模型可以根据历史消息回答，例如：

```text
你之前正在学习 Python 装饰器。
```

需要注意：

- 两个示例必须使用相同的数据库文件。
- 必须使用相同的 thread_id。
- 数据库文件必须具有正确的读取和写入权限。
- with 代码块结束后，数据库连接会关闭。

对于长期运行的 Web 服务，Checkpointer 的生命周期应该由应用统一管理，不应在每次 HTTP 请求中无意义地重复创建和关闭。


## 九、PostgresSaver：生产环境持久化

当 Agent 需要服务大量用户，或者部署在多个应用实例中时，可以使用 PostgreSQL 保存检查点。

PostgreSQL 支持更完整的数据库管理能力，更适合生产环境。


## 后续章节

- 安装依赖
- 实例：使用 PostgreSQL 保存记忆
- 实例
- 十、异步 Checkpointer
- 实例：AsyncSqliteSaver
- 实例
- 十一、get_state_history()：查看历史检查点
- 实例：列出历史检查点
- 实例
- 十二、checkpoint_id：读取指定历史版本
- 实例：读取之前的检查点
- 实例
- 十三、update_state()：手动修改对话状态
- 实例：更新学习进度
- 实例
- 十四、修改或删除消息历史

## 复习重点

- 能说明 `LangChain 对话记忆` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
