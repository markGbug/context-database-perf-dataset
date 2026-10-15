# LangChain：LangChain create_agent() 函数

- 来源：[LangChain create_agent() 函数](https://www.runoob.com/langchain/langchain-create_agent.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：概念卡
- 章节序号：0279

## 本章内容

create_agent() 是 LangChain 1.x 中创建 AI Agent 的核心函数。

它可以将语言模型、工具、系统提示词和中间件组合起来，创建一个能够自动调用工具并循环执行任务的 Agent。

与普通模型调用不同，Agent 不仅可以回答问题，还能根据任务需要调用 Python 函数、读取外部数据，并根据工具返回的结果决定下一步操作。

在 LangChain 1.x 中，create_agent() 基于 LangGraph 构建并编译 Agent 执行图，支持状态管理、流式输出、结构化响应、运行时上下文和会话持久化等功能。

本章节将完整介绍 create_agent() 的参数和常用方法，并使用 DeepSeek Flash 模型进行演示。


## 一、create_agent() 的工作原理

使用 create_agent() 创建的 Agent，通常按照以下流程运行：

```text
用户输入
    |
    v
  Model 节点
    |
    | 模型是否发起工具调用？
    |
    +-- 否 --> 返回最终结果
    |
    +-- 是
          |
          v
       Tools 节点
          |
          | 执行工具
          | 将结果加入消息历史
          |
          v
       Model 节点
          |
          | 继续判断是否调用工具
          v
        ...
```

其中：

- Model 节点：负责调用语言模型，生成回复或工具调用请求。
- Tools 节点：负责执行模型请求的客户端工具，并返回工具结果。
- Agent State：保存当前消息及其他状态字段。
- Middleware：可以在执行过程中的特定阶段修改或控制 Agent 行为。

Agent 一般会持续执行，直到模型不再请求工具，或者触发其他停止条件。

因此，create_agent() 创建的并不是单纯的聊天模型，而是一个具有执行流程和状态管理能力的应用组件。


## 二、安装与环境准备

本教程使用 LangChain 1.x，并以 DeepSeek 为主要模型提供商。

安装依赖：

```text
pip install -U langchain langchain-deepseek langgraph python-dotenv pydantic
```

在当前项目目录创建 .env 文件：

```text
DEEPSEEK_API_KEY=your_deepseek_api_key
```

Python 程序通过 load_dotenv() 加载密钥。


### 创建第一个 Agent


## 实例

这里没有给 Agent 配置任何工具，因此它主要通过模型生成回答。

虽然没有工具，create_agent() 依然会返回一个可执行的 LangGraph 对象。

注意：DeepSeek 当前推荐的模型名称包括 deepseek-flash 和 deepseek-v4-pro。新教程不再使用旧的 deepseek-v4-flash 作为默认模型名称。


## 三、create_agent() 函数语法

根据 LangChain 官方 API Reference，函数语法如下：

```text
from langchain.agents import create_agent

agent = create_agent(
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
    transformers=None,
)
```

参数说明：

对于初学者，最常用的是 model、tools 和 system_prompt。

构建复杂 Agent 时，再逐步使用 middleware、response_format、checkpointer 等高级参数。


## 四、model 参数：指定语言模型

model 是必填参数，主要支持两种形式：

- 模型名称字符串，例如 deepseek:deepseek-flash。
- 已经创建好的 BaseChatModel 实例。


### 方式一：直接传入模型名称


## 实例

这种写法简单直接，LangChain 会根据模型名称选择对应提供商并初始化模型。

推荐明确使用：

```text
provider:model
```

例如：

```text
deepseek:deepseek-flash
deepseek:deepseek-v4-pro
openai:gpt-4o-mini
```

实际使用时，需要安装对应提供商集成包并配置 API Key。


### 方式二：传入已初始化的模型


## 实例

这种方式适合需要配置模型超时、重试次数、输出上限或复用模型实例的场景。

注意：不推荐在传给 create_agent() 之前自行调用 model.bind_tools()。

因为 Agent 会根据其工具列表和运行时策略管理工具绑定。预先绑定工具可能与 Agent 的工具注册或动态工具管理机制发生冲突。


## 五、tools 参数：注册 Agent 工具

tools 用于指定 Agent 可以调用哪些工具。

官方支持的主要类型包括：

- BaseTool：LangChain 可执行工具对象。
- 普通 Python Callable：可以被转换为工具。
- 字典形式的提供商原生工具定义：由相应模型服务处理。

需要特别区分：工具的参数 Schema 不等于工具的实际执行逻辑。


### 方式一：使用 @tool 装饰器


## 实例

这种方式适合大部分工具定义场景。

模型可以看到工具名称、描述和参数 Schema，并决定是否请求调用工具。


### 方式二：使用普通 Python 函数

LangChain 也可以接受带有适当签名和描述的 Python 函数。


## 实例

这里的函数不需要手动添加 @tool，Agent 创建流程可以将其转换为可执行工具。


### 方式三：提供商原生工具

create_agent() 也支持某些模型提供商的原生工具定义。

这类工具可能由模型服务端执行，而不是由本地 Python 函数执行。

但其字典结构由具体提供商决定。

注意：不能简单地将任意 MCP 服务器描述字典直接传入 tools，就认为 LangChain 会自动连接 MCP 服务器。

如果需要访问 MCP 工具，应使用兼容的 MCP 集成或适配器，将远程工具转换为 Agent 可用的工具定义，并完成相应的连接、认证和执行配置。


### tools=None：不使用工具


## 实例

不传工具时，Agent 不会执行普通客户端工具调用循环。

但它依然是一个编译后的 LangGraph 对象，与直接调用 model.invoke() 的返回结构并不完全相同。


## 六、system_prompt 参数：系统指令

system_prompt 用于定义 Agent 的角色、任务目标和回答规则。

支持字符串和 SystemMessage 对象。


### 方式一：字符串

```text
agent = create_agent(
    model="deepseek:deepseek-flash",
    tools=[],
    system_prompt=(
        "你是菜鸟教程 RUNOOB 的编程助手。"
        "请使用简洁、准确的中文回答。"
    )
)
```


### 方式二：SystemMessage


## 实例

系统提示词通常会在模型调用时添加到消息列表前面。

如果需要根据用户、会话或任务动态生成系统提示词，可以使用 Middleware。

注意：系统提示词不等于可靠的安全边界。身份认证、用户权限和工具执行限制仍需在应用代码中实现。


## 七、middleware 参数：Agent 中间件

middleware 是 LangChain 1.x Agent 的重要扩展机制。

它可以在 Agent 执行过程中的特定阶段运行自定义逻辑。

例如：

- 在模型调用前修改消息。
- 根据用户身份选择模型。
- 限制模型调用次数。
- 对工具执行进行拦截。
- 处理部分模型或工具错误。
- 记录模型调用和工具执行信息。

官方提供了多种可直接使用的中间件。


### 实例：限制模型调用次数


## 后续章节

- 实例
- 八、response_format 参数：结构化输出
- 实例：使用 Pydantic 定义结构
- 实例
- 九、state_schema 参数：自定义 Agent 状态
- 1、定义自定义 State
- 实例
- 2、使用 Command 修改 State
- 实例
- 3、创建 Agent 并读取更新后的 State
- 实例
- 十、context_schema 参数：运行时上下文
- 实例：传入当前用户身份
- 实例
- 十一、checkpointer 参数：会话持久化
- 实例：保存多轮对话

## 记忆卡片

- 一句话定义：`LangChain create_agent() 函数` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
