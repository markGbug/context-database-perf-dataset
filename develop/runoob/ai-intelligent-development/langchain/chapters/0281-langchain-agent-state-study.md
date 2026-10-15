# LangChain：LangChain AgentState 状态管理

- 来源：[LangChain AgentState](https://www.runoob.com/langchain/langchain-agent-state.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：学习笔记
- 章节序号：0281

## 本章内容

Agent 在运行过程中需要维护状态，例如对话消息、工具执行结果、学习进度以及结构化输出。

在 LangChain 1.x 中，AgentState 负责定义 Agent 的状态结构，而 LangGraph 负责状态的更新、合并和管理。

本章节介绍 AgentState 的默认字段、Reducer 合并机制、Middleware 流程控制、自定义状态，以及如何通过 Command 和 Checkpointer 管理状态。


## 一、AgentState 基本结构

AgentState 基于 Python 的 TypedDict，主要包含以下三个字段：

可以通过 Python 查看当前版本的定义：


## 实例

其中最常用的是 messages，保存用户消息、AI 回复以及工具执行结果。

注意：AgentState 只是状态结构定义，并不意味着数据已经保存到数据库。是否能够跨调用恢复，需要配置 Checkpointer。


## 二、messages：消息历史与 Reducer

messages 使用 add_messages Reducer，负责合并新旧消息。

它支持三种主要操作：

- 追加：新消息 ID 不存在时，添加到消息列表。
- 替换：新消息 ID 与已有消息相同时，替换对应消息。
- 删除：通过 RemoveMessage 删除指定 ID 的消息。


### 1、追加消息


## 实例

输出：

```text
合并前： 2
合并后： 3
1 human 你好
2 ai 你好！
3 human 介绍 Python
```


### 2、相同 ID 替换消息


## 实例

输出：

```text
1 修改后的回答
```

这里比较的是消息 id，而不是消息内容或消息类型。


### 3、RemoveMessage 删除消息


## 实例

输出：

```text
1 你好
3 介绍 Python
```

注意：删除 Tool Calling 消息时，应同时考虑 AIMessage 和 ToolMessage 的关联关系，避免产生不符合模型 API 要求的消息历史。


## 三、jump_to：Middleware 流程控制

jump_to 用于让 Middleware 在特定阶段控制 Agent 的下一步执行方向。

jump_to 属于瞬态状态，用于控制执行流程，不适合保存长期业务数据。


### 实例：提前结束 Agent

下面使用 @before_model 拦截一个演示关键词，展示如何跳过模型调用。


## 实例

输出：

```text
请求已被演示规则拦截。
```

这里的中间件在模型执行前检查消息，如果符合条件，就添加一条 AIMessage 并跳转到结束流程。

注意：jump_to="tools" 不能凭空执行任意 Python 函数；工具节点仍然需要有效的 Tool Calling 请求。


## 四、structured_response：结构化输出

如果通过 create_agent() 的 response_format 参数设置结构化输出，Agent 会将解析结果存入 structured_response。

这个字段通常不需要用户在输入 State 时提供，但可以从执行完成后的返回值中获取。


### 实例：推荐课程


## 实例

如果模型正确完成结构化输出，可能得到：

```text
课程： Python 基础教程
理由： Python 语法简洁，适合零基础学习
难度： 入门
```

返回的是符合定义的 Pydantic 数据结构，而不是必须自行从自然语言中提取字段。

具体的结构化输出机制由模型及 LangChain 集成决定。模型不支持、Schema 不兼容或解析失败时，可能抛出异常。


## 五、自定义 AgentState

除了默认字段，还可以通过继承 AgentState 添加业务状态。

例如，学习助手可以保存学习等级、已完成主题和当前目标。


## 实例

其中 NotRequired 表示初始状态可以省略该字段，但不会自动设置默认值。

读取时建议使用：

```text
level = state.get("user_level", "入门")
topics = state.get("completed_topics", [])
```

创建 Agent 时指定：

```text
agent = create_agent(
    model="deepseek:deepseek-flash",
    tools=[],
    state_schema=LearningAgentState
)
```

注意，自定义 State 仅负责描述字段，工具需要通过正式的状态更新机制才能修改这些字段。


## 六、ToolRuntime：读取 Agent 状态

LangChain 1.x 推荐通过 ToolRuntime 访问当前 Agent State。

例如，可以在工具中读取学习等级和已完成主题：


## 实例

runtime 由 Agent 执行框架注入，模型不需要提供该参数。

因此，不应假设直接执行 view_progress.invoke({}) 就能获得完整 Agent State。

如果需要修改 State，应使用下一节介绍的 Command。


## 七、Command：更新 AgentState

直接修改 runtime.state 中的字典或列表，并不是可靠的状态更新方式。

推荐使用 Command(update=...) 提交修改。


### 实例：记录学习主题


## 实例

这里通过 Command 同时更新两个字段：

- completed_topics：保存新的学习主题列表。
- messages：追加一条与当前调用 ID 关联的工具结果。

在 Agent Tool Calling 场景中，返回 Command 时应保持对应的 ToolMessage，避免破坏消息协议。

注意：这里采用的是列表整体更新。如果多个工具并行修改同一字段，需要额外设计 Reducer 或顺序执行机制。


## 八、完整实例：学习进度 Agent

下面将自定义 State、ToolRuntime、Command 和 Checkpointer 结合起来，创建可以记录与查询学习进度的 Agent。

文件名：agent_state_demo.py

安装依赖：

```text
pip install -U langchain langchain-deepseek langgraph python-dotenv
```

配置 .env：

```text
DEEPSEEK_API_KEY=your_deepseek_api_key
```


## 完整实例

如果模型正确调用工具，第一轮状态应包含：

```text
['HTML 基础', 'Python 基础']
```

第二轮使用相同的 thread_id，可以读取此前保存的状态。

这里的 InMemorySaver 只保存进程内存。程序退出后，状态通常会丢失。

注意：模型是否调用工具并不保证。需要强制记录业务数据时，应由确定性的应用逻辑执行，而不是只依赖模型选择工具。


## 后续章节

- 九、购物车 Agent：状态管理实战
- 实例
- 十、自定义 Reducer
- 实例：追加学习日志
- 实例
- 十一、state_schema 与 Middleware state_schema
- 实例：中间件统计模型调用次数
- 实例
- 十二、Checkpointer：保存 AgentState
- 实例：保存多轮对话
- 实例
- 十三、AgentState 与 Store 的区别
- 十四、常见问题
- 1、AgentState 是普通字典吗？
- 2、add_messages 是否永远只追加消息？
- 3、jump_to="tools" 能直接执行某个 Python 函数吗？

## 复习重点

- 能说明 `LangChain AgentState` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
