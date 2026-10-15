# LangChain：LangChain Agent API 参考

- 来源：[LangChain Agent API](https://www.runoob.com/langchain/langchain-agent-api.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：练习笔记
- 章节序号：0304

## 本章内容

LangChain 1.x 提供了统一的 Agent API，可以将大语言模型、工具调用、Middleware、对话记忆和结构化输出组合为一个可运行的智能体。

其中最核心的函数是 create_agent()。

与旧版 AgentExecutor 不同，LangChain 1.x 的 create_agent() 基于 LangGraph 实现，返回一个编译后的 CompiledStateGraph，支持同步、异步、流式输出、状态持久化和人工介入。

本章节系统整理 create_agent() 的完整参数、CompiledStateGraph 常用方法、AgentState 结构、运行时上下文和各种配置的实际用法。


## 一、create_agent() 是什么？

create_agent() 是 LangChain 1.x 创建 Agent 的核心入口。

一个典型的 Agent 执行流程如下：

```text
用户消息
    ↓
   Agent
    ↓
 调用 Chat Model
    ↓
 是否需要工具？
    |
    ├── 否 → 生成最终回复 → 结束
    |
    └── 是 → 调用 Tool
                 ↓
              工具结果
                 ↓
             再次调用模型
                 ↓
               循环判断
```

开发者只需要提供模型、工具和必要的配置，LangChain 就可以自动组织模型与工具之间的执行循环。


### 最简单的 Agent


## 实例

这里没有注册工具，因此 Agent 主要执行模型调用，不会进入普通的工具调用循环。

如果提供工具，模型可以根据问题选择调用对应工具。


## 二、create_agent() 完整函数签名

LangChain 当前 API 的主要函数签名如下：

```text
create_agent(
    model,
    tools=None,
    *,
    system_prompt=None,
    middleware=(),
    response_format=None,
    state_schema=None,
    context_schema=None,
    checkpointer=None,
    store=None,
    interrupt_before=None,
    interrupt_after=None,
    debug=False,
    name=None,
    cache=None,
    transformers=None
)
```

其中 model 是必填参数，其余参数都有默认值。


### 参数速查表

参数看起来比较多，但实际开发时通常只需要使用 model、tools 和 system_prompt。

随着功能增加，再逐步加入 Middleware、Checkpointer、Store 等配置。


## 三、model：语言模型

model 指定 Agent 使用的大语言模型。

支持两种方式：

- 模型名称字符串。
- BaseChatModel 实例。


### 方式一：字符串指定模型


## 实例

字符串一般采用：

```text
provider:model_name
```

需要提前安装对应模型服务商的集成包。

例如 DeepSeek：

```text
pip install -U langchain-deepseek
```


### 方式二：传入模型实例


## 实例

这种方式适合需要配置超时、重试以及其他模型参数的场景。

注意：模型必须具备对应的功能。例如，如果 Agent 需要调用工具，底层模型和集成接口就必须支持工具调用。


## 四、tools：注册工具

tools 指定 Agent 可以使用的工具集合。

常见工具形式包括：

- 使用 @tool 装饰的函数。
- BaseTool 实例。
- 符合要求的 Python Callable。
- 受支持的工具定义字典。

Pydantic BaseModel 通常用于定义工具参数 Schema，而不是直接替代可执行的 Python 工具函数。


### 实例：注册多个工具


## 实例

模型可以根据工具名称、说明和参数 Schema 选择需要调用的工具。

注意：工具注册并不意味着模型一定会调用工具。如果业务必须执行某个操作，应使用确定性工作流或进一步约束执行流程。


## 五、system_prompt：系统提示词

system_prompt 用于定义 Agent 的角色、目标和行为规则。

支持普通字符串或 SystemMessage。


### 实例


## 实例

system_prompt 在模型调用时作为系统消息使用。

如果需要根据时间、用户身份或其他上下文动态生成提示词，可以使用 @dynamic_prompt Middleware。

注意：system_prompt 不能替代程序中的身份验证、数据库权限或工具执行安全检查。


## 六、middleware：Agent 中间件

middleware 用于在 Agent 执行过程中加入自定义逻辑。

例如：

- 模型调用之前检查消息。
- 动态修改系统提示词。
- 限制工具调用次数。
- 模型失败时自动重试。
- 在执行敏感工具前请求人工审批。


### 常用 Middleware Hook


### 实例：使用动态提示词


## 实例

如果需要用户当地日期，应使用可信用户时区，而不是直接依赖服务器默认时间。

多个 Middleware 可以组合使用。对于包裹式 Hook，通常是列表中靠前的 Middleware 位于外层。


## 七、response_format：结构化输出

response_format 用于让 Agent 返回符合指定 Schema 的结构化数据。

支持直接传入 Pydantic 模型，也可以显式指定结构化输出策略。


### 主要策略

直接传入 Schema 时，LangChain 可以尝试根据模型能力选择适当的策略。


### 实例：Pydantic 结构化输出


## 实例

结构化输出通常保存在：

```text
result["structured_response"]
```

它与普通的：

```text
result["messages"][-1].content
```

是不同的数据读取方式。

注意：不是每个模型都支持所有结构化输出策略。结构化数据通过 Schema 校验，也不意味着其中的业务事实已经得到验证。


## 后续章节

- 八、state_schema：自定义 Agent 状态
- 实例：添加任务类别
- 实例
- 九、context_schema：运行时上下文
- 实例：向工具注入用户身份
- 实例
- 十、checkpointer：对话持久化
- 实例：InMemorySaver
- 实例
- 十一、store：跨会话长期存储
- 实例：配置 InMemoryStore
- 实例
- 十二、interrupt_before 与 interrupt_after
- 实例：工具执行前暂停
- 实例
- 十三、debug：调试模式

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `LangChain Agent API` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
