# LangChain：LangChain 工具访问——InjectedState、InjectedStore 与 ToolRuntime

- 来源：[LangChain 工具访问](https://www.runoob.com/langchain/langchain-state-store.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：概念卡
- 章节序号：0278

## 本章内容

前面我们学习了如何使用 @tool 定义工具，以及如何将工具注册到 Agent 中。

普通工具主要通过函数参数接收模型提供的数据。例如，查询天气工具需要模型传入城市名称。

但在实际开发中，工具往往还需要访问一些不能由模型直接提供的信息：

- 当前对话的消息历史。
- 用户在对话中已经确认的设置。
- 登录用户的身份信息。
- 跨会话保存的学习进度和个人偏好。
- 当前工具调用的 ID 和执行配置。

LangChain 提供运行时依赖注入机制，让工具可以访问这些信息，而不需要把所有内部数据暴露给语言模型。

早期教程常使用 InjectedState 和 InjectedStore。在 LangChain 1.x 中，官方更推荐使用 ToolRuntime 统一访问运行时信息。

本章节将介绍三种机制及其关系，并通过完整的 Agent 示例说明如何正确使用。


## 一、State、Context 与 Store 的区别

在编写工具之前，需要先理解 Agent 运行时的三种数据。

可以通过下面的示意图理解：

```text
用户发起请求
      |
      v
  LangChain Agent
      |
      +-- State
      |     当前消息、任务状态
      |
      +-- Context
      |     用户身份、请求配置
      |
      +-- Store
            用户偏好、学习记录
      |
      v
  ToolRuntime
      |
      v
  Python 工具函数
```

其中，State、Context 和 Store 的生命周期不同。

State：默认用于当前 Agent 执行过程。如果配置了 Checkpointer，可以按会话线程保存，并在之后的调用中恢复。

Context：通常由应用程序在调用 Agent 时传入，提供本次运行需要的上下文信息。

Store：可以保存跨会话的数据。实际能保存多久，取决于 Store 的具体实现。


## 二、ToolRuntime——官方推荐的工具运行时接口

LangChain 1.x 推荐通过 ToolRuntime 访问工具执行上下文。

只需要在工具函数中添加：

```text
runtime: ToolRuntime
```

Agent 执行工具时，LangChain 会自动注入运行时对象。

不需要添加 Annotated，也不需要让模型传入这个参数。


### ToolRuntime 常用属性


### 实例：读取当前 Agent 消息数量


## 实例

在这个工具中，runtime.state 提供当前 Agent 的状态，其中通常包含 messages。

需要注意，runtime 不会出现在提供给模型的工具参数列表中。

模型只需要知道工具可以执行对话统计，不需要了解 Agent 内部如何保存消息。


### 在 Agent 中调用


## 实例

如果模型调用了 conversation_stats，工具就可以访问执行时的消息状态，并返回统计结果。

实际消息数量取决于工具被执行时 Agent 已经产生了多少条消息，因此不能假设总数始终固定。

注意：不能简单地直接执行：

```text
# 不适合作为运行时注入的测试方式
conversation_stats.invoke({})
```

因为普通的工具调用没有自动提供完整的 Agent 运行时上下文。

如果需要测试这种工具，应通过 create_agent() 或正确配置的 LangGraph ToolNode 执行。


## 三、InjectedState——旧式状态注入方式

InjectedState 用于标记需要从 Agent 状态中自动注入的参数。

它仍可用于支持这种注入机制的 LangGraph ToolNode，但在新的 LangChain 教程中，推荐优先使用 ToolRuntime。


### InjectedState 的基本语法

```text
from typing import Annotated
from langgraph.prebuilt import InjectedState

state: Annotated[dict, InjectedState()]
```

当工具通过支持状态注入的执行节点运行时，LangGraph 会从当前图状态中取得相应数据。


### 实例：读取完整 State


## 实例

这里的 state 不是由模型填写的普通工具参数。

执行框架会在工具真正运行前，将当前 State 注入对应参数。


### 只注入某个 State 字段

InjectedState 也支持只读取状态中的一个字段。

例如：

```text
InjectedState("messages")
```

表示只注入 messages 字段。


## 实例

相比注入整个 State，这种方式只读取工具需要的字段。

但在新项目中，通常可以直接使用：

```text
runtime.state["messages"]
```

避免使用多个不同的注入参数。


## 四、读取 State 不等于修改 State

原文中的 remember_preference() 只是读取状态并返回文字，并没有真正把用户偏好保存到 Agent 状态中。

如果希望工具修改状态，LangChain 官方推荐返回 Command。

Command 可以声明需要写入哪些状态字段，并将工具调用结果关联回消息历史。


### 实例：保存当前会话的偏好


## 实例

这里定义了一个额外状态字段：

```text
theme: str
```

当 set_theme 返回 Command 时，可以通过 update 更新该字段。

其中的 ToolMessage 必须与当前工具调用 ID 对应。

如果只有读取操作，就不需要返回 Command。


### 创建支持自定义 State 的 Agent

```text
agent = create_agent(
    model=model,
    tools=[set_theme, get_theme],
    state_schema=CustomState,
    system_prompt="你是一名用户设置助手。"
)
```

这样就可以让 Agent 管理自定义会话字段。

注意：State 是工作流状态，不建议直接修改 runtime.state 内部字典并假设修改一定会持久化。应通过受支持的状态更新方式提交变化。

如果多个工具可能同时更新相同字段，还需要考虑并行写入冲突及 reducer 的配置。


## 五、Checkpointer——让 State 跨调用保存

State 不是只能存在于单次 invoke() 调用中。

LangGraph 提供 Checkpointer，用于保存会话状态。

例如，同一用户连续发送多个问题时，可以通过相同的 thread_id 恢复此前的消息和状态。


### 实例：保存对话历史


## 实例

这里使用 InMemorySaver 保存会话检查点。

两次调用使用相同的 thread_id，因此第二次调用可以访问此前保存的会话历史。

但 InMemorySaver 只将数据保存在当前 Python 进程的内存中。

当程序退出或重启后，这些记录通常会丢失。

如果需要持久保存，可以使用数据库支持的 Checkpointer。


## 六、InjectedStore——旧式存储注入方式

InjectedStore 用于向工具注入 LangGraph 的 Store 对象。

工具可以通过 Store 保存和读取用户偏好、学习进度等长期信息。

其基本语法为：

```text
from typing import Annotated
from langgraph.prebuilt import InjectedStore
from langgraph.store.base import BaseStore

store: Annotated[
    BaseStore,
    InjectedStore()
]
```

与 InjectedState 类似，InjectedStore 参数也不会作为普通工具参数暴露给模型。


### 实例：读取 Store 中的数据


## 实例

这个工具需要通过配置了 Store 的 Agent 或 ToolNode 执行。

直接调用：

```text
get_preference.invoke({"key": "theme"})
```

并不能凭空获得 Store 实例。

因此，这种写法只适合展示旧版注入参数的结构。下面使用官方推荐的 ToolRuntime 实现完整示例。


## 七、ToolRuntime.store——访问共享存储

在 LangChain 1.x 中，推荐通过：

```text
runtime.store
```

获取当前 Agent 使用的 Store 对象。

Store 通过命名空间（Namespace）和键（Key）组织数据。

例如：

```text
store.put(
    ("users", "user_001"),
    "profile",
    {"name": "小明"}
)
```

其中：

- ("users", "user_001") 是命名空间。
- "profile" 是键。
- {"name": "小明"} 是保存的数据。

读取时使用：

```text
item = store.get(
    ("users", "user_001"),
    "profile"
)

print(item.value)
```


## 后续章节

- InMemoryStore 的生命周期
- 八、完整实例：保存用户学习进度
- 完整代码
- 实例
- 运行结果说明
- 九、在 Agent 中结合 Store 查询课程数据
- 实例
- 实例
- 十、ToolRuntime.context——获取可信用户上下文
- 实例
- 实例
- 十一、InjectedToolArg——通用注入参数标记
- 实例
- 十二、State、Checkpointer 与 Store 对比
- 十三、生产环境注意事项
- 1、不能信任模型提供的用户 ID

## 记忆卡片

- 一句话定义：`LangChain 工具访问` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
