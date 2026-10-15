# LangChain：LangChain 配置与错误类 API 参考

- 来源：[LangChain 配置与错误类](https://www.runoob.com/langchain/langchain-config-errors.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：学习笔记
- 章节序号：0308

## 本章内容

在前面的教程中，我们已经学习了 LangChain 的 Chat Model、Agent、Tools、Messages、Middleware 和 RAG。

本章节继续介绍实际开发中经常使用的 RunnableConfig、Checkpointer、Store 以及常见异常类。

这些接口不直接决定 AI 的回答内容，却影响 Agent 的运行方式、并发执行、对话记忆、数据持久化、日志追踪和错误处理。

例如：

- 使用 RunnableConfig 控制执行参数。
- 使用 thread_id 识别对话线程。
- 使用 Checkpointer 保存和恢复 Agent 状态。
- 使用 Store 保存用户长期偏好。
- 通过异常类型判断是否应该重试、终止或提示用户。

本章节基于 LangChain 1.x 与 LangGraph 1.x，提供常用 API 速查表、Python 示例、异常处理方法及运行环境排查清单。


## 一、RunnableConfig 是什么？

RunnableConfig 是 LangChain 用于配置 Runnable 执行行为的数据结构。

Chat Model、Agent、Chain 以及其他 Runnable 通常都支持通过 config 参数传入运行时配置。

例如：

```text
result = agent.invoke(
    {"messages": [{"role": "user", "content": "你好"}]},
    config={
        "tags": ["demo"],
        "metadata": {"source": "web"}
    }
)
```

RunnableConfig 可以在不修改 Agent 定义的情况下，为不同请求设置不同的执行标签、追踪信息以及其他参数。

主要作用包括：

- 控制运行时配置。
- 设置并发限制。
- 限制图执行步骤。
- 添加追踪标签和元数据。
- 配置回调处理器。
- 指定线程和运行标识。


## 二、RunnableConfig 完整字段

RunnableConfig 是 TypedDict，配置字段通常都是可选的。

其中使用频率最高的是：

```text
configurable
tags
metadata
recursion_limit
max_concurrency
```

注意：RunnableConfig 中的 recursion_limit 与 Python 解释器的 sys.setrecursionlimit() 不是同一回事。


## 三、configurable：运行时动态配置

configurable 用于传入运行时配置。

在 LangGraph Agent 中，最常见的用途是设置：

```text
thread_id
```

例如：


## 实例：配置对话线程

当 Agent 配置了 Checkpointer 后，同一个 thread_id 可以用于读取和继续此前保存的对话状态。

例如：

```text
thread_id = conversation-001

第一轮：你好
第二轮：我正在学习 Python
第三轮：我刚才说在学什么？
```

这些调用可以共享同一个线程历史。

如果换成新的 thread_id，则会使用另一个线程。

注意：thread_id 只是线程标识，不是用户身份认证凭证。多用户系统必须验证当前用户是否有权访问指定线程。


## 四、configurable 不只用于 thread_id

除了 Checkpointer，configurable 还可以修改已经明确声明为可配置的 Runnable 参数。

例如：


## 实例：动态修改模型参数

这个例子允许调用时修改 temperature。

如果没有通过 configurable_fields 或其他可配置机制声明某个参数，不能假定在 configurable 中添加同名字段就会修改模型行为。

安全提醒：不要直接允许普通用户通过 configurable 修改 api_key、base_url 等敏感配置。


## 五、recursion_limit：执行步骤限制

LangChain Agent 基于 LangGraph 执行。

Agent 可能在模型和工具之间多次循环：

```text
模型
 ↓
工具
 ↓
模型
 ↓
工具
 ↓
模型
 ...
```

如果流程始终没有结束，就可能超过最大执行步骤限制。

RunnableConfig 的默认递归限制为：

```text
recursion_limit = 25
```

可以在运行时调整：


## 实例

这里将本次运行的限制设为 20。

需要特别注意：recursion_limit 不等于最多调用 20 次模型。

因为一次 Agent 工具调用循环通常包含多个图执行步骤。


### 超过限制会怎样？

如果执行步骤超过限制，通常会抛出：

```text
GraphRecursionError
```

例如：


## 实例：捕获递归限制异常

建议：遇到 GraphRecursionError 时，首先检查 Agent 是否重复调用工具、工具返回内容是否完整，以及模型能否判断任务已经完成。

不要仅通过不断提高 recursion_limit 掩盖无限循环问题。


## 六、max_concurrency：并发控制

RunnableConfig 可以通过 max_concurrency 控制 Runnable 并行调用的数量。

例如使用 batch() 批量向模型发送问题：


## 实例：批量调用

这里最多允许两个并发调用任务。

需要注意，max_concurrency 控制的是相关 Runnable 的并发执行，不等于服务商 API 的每秒请求数限制。

如果需要控制请求频率，还应使用 Rate Limiter 或服务端限流机制。


## 七、tags：追踪标签

tags 用于给本次运行添加标签。

例如：

```text
development
production
rag
customer-service
course-search
```

这些标签可以在 LangSmith 等追踪系统中用于筛选和分组。


### 实例


## 实例

tags 可以随父级 Runnable 配置向部分子调用传播，方便关联整个执行流程。


## 八、metadata：附加元数据

metadata 适合保存运行环境和业务分类信息。

例如：


## 实例

与 tags 的区别：

注意：metadata 应尽量使用可以 JSON 序列化的数据，不要存放 API Key、密码、身份凭据等敏感信息。


## 九、callbacks：回调处理器

callbacks 可以指定 Runnable 执行时使用的回调处理器。

例如，自定义回调可以记录：

- 模型调用开始。
- 模型调用结束。
- 模型发生错误。
- 工具调用。

可以继承 BaseCallbackHandler 创建处理器。


### 实例：记录模型执行


## 实例

这个示例定义了模型回调处理器。

具体触发的回调事件取决于模型集成和执行方式。聊天模型通常还会使用专门的 Chat Model 启动事件，因此不要假定所有模型都只通过 on_llm_start 触发。

对于基于 LangChain 1.x 的 Agent 执行控制，更推荐使用 Middleware；对于模型和工具的运行追踪，可以结合 callbacks 与 LangSmith。


## 十、run_name 与 run_id

这两个字段主要用于执行追踪。


### 实例


## 实例

其中 run_id 是追踪运行的标识，不应与 Checkpointer 的 thread_id 混淆。

同一个 thread_id 可以包含多次不同的运行，每次运行都可以有独立的 run_id。


## 十一、RunnableConfig 完整使用示例

将常用字段组合起来：


## 后续章节

- 实例
- 十二、Checkpointer 是什么？
- 十三、Checkpointer 实现类速查
- 十四、InMemorySaver：内存检查点
- 实例：多轮对话
- 实例
- 十五、SqliteSaver：SQLite 持久化
- 安装
- 正确的使用方式
- 实例
- 十六、PostgresSaver：PostgreSQL 持久化
- 安装依赖
- 实例：PostgresSaver
- 实例
- 十七、Checkpointer 常用方法
- 实例：读取当前状态

## 复习重点

- 能说明 `LangChain 配置与错误类` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
