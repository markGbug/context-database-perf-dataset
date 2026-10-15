# LangChain：LangChain 工具高级特性

- 来源：[LangChain 工具高级特性](https://www.runoob.com/langchain/langchain-tool-advanced.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：概念卡
- 章节序号：0277

## 本章内容

上一节我们学习了如何通过 @tool 装饰器定义工具，并将工具注册到 LangChain Agent 中。

实际开发时，除了定义工具的名称、参数和执行逻辑，还需要解决一些问题：

- 工具执行完成后，能不能直接返回结果，不再调用模型？
- 如何获取当前工具调用的唯一 ID？
- 工具运行失败时，如何避免整个 Agent 中断？
- 如何让模型根据工具错误信息调整下一步操作？

本章节介绍四个重要的工具高级特性：

- return_direct：控制工具执行后是否直接结束 Agent 循环。
- InjectedToolCallId：在工具执行时注入当前调用 ID。
- ToolException：用于表示工具执行过程中的可预期错误。
- handle_tool_error：控制工具如何处理 ToolException。

本教程采用 LangChain 1.x 的 create_agent() API，示例使用 DeepSeek Flash 模型。


## 一、安装与环境准备

首先安装依赖：

```text
pip install -U langchain langchain-deepseek python-dotenv
```

在项目目录创建 .env 文件：

```text
DEEPSEEK_API_KEY=your_deepseek_api_key
```

在 Python 中读取环境变量并初始化模型：


## 实例

本章的工具示例均使用模拟数据，不会实际访问菜鸟教程数据库、真实订单系统或天气服务。

需要注意，Tool Calling 的具体行为由模型能力与 LangChain 执行框架共同决定。模型是否选择工具、一次选择多少个工具，并不是完全固定的。


## 二、return_direct：直接返回工具结果

默认情况下，Agent 执行工具之后，会将工具结果发送回模型，让模型根据结果继续回答。

执行流程通常如下：

```text
用户提问
   ↓
模型请求调用工具
   ↓
工具执行
   ↓
结果返回模型
   ↓
模型生成最终回答
```

对于一些查询类工具，工具结果本身已经是完整的回答，不一定需要模型再次加工。

这时可以设置：

```text
@tool(return_direct=True)
```

在支持该功能的 Agent 执行框架中，工具执行完成后可以直接结束当前 Agent 循环。


### 1、普通工具与 return_direct 工具


## 实例

执行结果：

```text
普通工具： False
直接返回工具： True
```

可以通过工具对象的 return_direct 属性检查是否启用直接返回。


### 2、在 Agent 中比较两种模式

下面分别创建两个 Agent，一个使用普通工具，另一个使用直接返回工具。


## 实例

如果模型选择调用对应工具，普通模式通常会让模型再次处理工具结果；直接返回模式则可能在工具执行后结束当前 Agent 循环。

两者的区别如下：


### 3、最终消息不一定是 AIMessage

使用普通工具时，Agent 的最后一条消息通常是模型生成的 AIMessage。

但使用 return_direct=True 时，Agent 可能直接在工具执行后结束，因此最后一条消息可能是 ToolMessage。

例如：

```text
result = agent_direct.invoke(question)

last_message = result["messages"][-1]

print(last_message.type)
print(last_message.content)
```

如果工具执行成功并触发直接返回，可能输出：

```text
tool
Python 基础、Python 数据分析
```

因此，不能假设所有 Agent 的最终输出都必须是 AIMessage。


### 4、多个工具与 return_direct

对于当前 LangChain 1.x 的 create_agent()，如果模型在同一轮生成多个客户端工具调用，执行框架会结合这一批工具的 return_direct 属性判断是否结束循环。

当前实现要求这一批已执行的客户端工具都设置了 return_direct=True，才会通过该条件直接结束。

例如：

注意：这是当前 create_agent() 的执行行为，不应简单推广到旧版 AgentExecutor 或自定义 Agent 框架。

此外，即使工具被设置为直接返回，也不代表工具执行一定成功。生产环境仍然需要检查工具执行状态。

如果业务要求某个步骤一定执行、一定终止或一定完成后续汇总，应该通过程序逻辑明确编排。


## 三、InjectedToolCallId：注入工具调用 ID

当模型请求调用工具时，每一次工具调用通常会有一个唯一标识：

```text
tool_call_id
```

例如：

```text
{
    "name": "log_user_action",
    "args": {
        "action": "查询 Python 课程"
    },
    "id": "call_log_001",
    "type": "tool_call"
}
```

有时候，工具内部需要获取当前这一次调用的 ID，以便关联日志、工具结果或 Agent 状态更新。

LangChain 提供 InjectedToolCallId，可以通过参数注解，让运行时注入对应的工具调用 ID。


### 1、基本用法

使用 Annotated 标注工具参数：

```text
from typing import Annotated
from langchain.tools import InjectedToolCallId

tool_call_id: Annotated[str, InjectedToolCallId]
```

这个参数与普通参数不同，不需要由模型生成。


### 实例：记录工具调用 ID


## 实例

执行结果类似：

```text
返回类型： ToolMessage
返回内容： 操作：查询 Python 课程；工具调用 ID：call_log_001
关联 ID： call_log_001
```

这里传入的是完整的 ToolCall 字典，其中包含 id。

LangChain 根据它注入 tool_call_id，因此工具函数可以获取当前调用的标识。


### 2、InjectedToolCallId 不属于用户参数

普通工具参数由模型提供，例如：

```text
action="查询 Python 课程"
```

但 tool_call_id 属于运行时上下文。

使用 InjectedToolCallId 标记后，该字段不会作为普通参数暴露给模型。

可以通过以下代码查看工具向模型公开的参数：

```text
print(log_user_action.tool_call_schema.model_json_schema())
```

公开参数通常只包含 action，而不会要求模型填写 tool_call_id。

注意：工具调用 ID 只是当前 Tool Call 的标识，不代表用户身份、登录状态或权限信息。

如果业务需要识别真实用户，应从经过认证的应用上下文获取身份，不能使用工具调用 ID 代替用户 ID。


### 3、适用场景

InjectedToolCallId 常用于：

- 关联模型请求与工具执行日志。
- 跟踪某次工具调用的执行结果。
- 构造与当前 Tool Call 对应的 ToolMessage。
- 结合 LangGraph Command 更新 Agent 状态。

如果工具需要更多运行时信息，例如状态、上下文或存储对象，也可以进一步学习 LangChain 的 ToolRuntime。


## 四、ToolException：工具执行异常

在实际开发中，工具并不总能成功执行。

例如：

- 查询的课程不存在。
- 用户提供了无效参数。
- 外部 API 请求失败。
- 数据库没有找到相关记录。

对于工具执行过程中预期可能出现的错误，可以使用 ToolException 表示。

ToolException 是 LangChain 定义的工具异常类型，用于配合工具错误处理机制。


### 实例：模拟用户信息查询


## 实例

执行结果：

```text
张三，普通用户
工具异常： 用户 ID 必须是正整数
工具异常： 未找到 ID 为 999 的用户
```

这里的 ToolException 没有被工具内部处理，因此向调用方抛出。

我们通过 try/except 捕获错误。


### ToolException 与普通异常

注意：抛出 ToolException 不代表 Agent 一定会自动恢复错误。

是否将异常转换为工具结果，取决于工具自身的 handle_tool_error 设置，以及 Agent 的工具执行与中间件处理机制。


## 五、handle_tool_error：处理工具异常

handle_tool_error 是 LangChain BaseTool 的属性，用于控制工具遇到 ToolException 时如何处理。

默认值为：

```text
handle_tool_error = False
```

也就是说，默认情况下，ToolException 会继续向外抛出。

如果希望工具将错误转换为可读取的结果，可以设置：

```text
my_tool.handle_tool_error = True
```


### 1、正确设置 handle_tool_error

需要特别注意，在当前 LangChain 官方 API 中，@tool 装饰器并没有 handle_tool_error 这个直接参数。

因此，不要写成：

```text
# 错误写法：当前 @tool 不接受这个参数
@tool(handle_tool_error=True)
```

推荐先创建工具对象，再设置相应属性。


### 实例：转换为工具错误信息


## 实例

执行结果：

```text
未收录城市：北境。可查询杭州、北京和上海。
```

由于设置了 handle_tool_error=True，工具会将 ToolException 的错误文本作为结果返回，而不是继续向调用方抛出该异常。

这里调用工具时传入的是普通参数字典，因此结果以普通内容形式返回。

如果通过完整 ToolCall 执行，包含工具调用 ID，LangChain 可以生成带有错误状态的 ToolMessage。


### 2、使用 ToolCall 查看错误状态


## 后续章节

- 实例
- 六、handle_tool_error 的四种配置方式
- 1、False：默认抛出异常
- 2、True：返回原始错误信息
- 3、str：返回固定错误提示
- 4、Callable：自定义错误处理
- 实例
- handle_tool_error 与 handle_validation_error
- 七、工具错误处理与 Agent 的关系
- 实例：让 Agent 处理天气查询错误
- 实例
- 不能使用 with_config() 修改工具错误策略
- 八、完整示例：带异常处理的课程登记 Agent
- 完整代码
- 完整实例
- 运行结果说明

## 记忆卡片

- 一句话定义：`LangChain 工具高级特性` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
