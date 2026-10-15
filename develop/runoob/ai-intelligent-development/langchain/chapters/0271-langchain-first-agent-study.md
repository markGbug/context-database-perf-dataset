# LangChain：第一个 LangChain Agent

- 来源：[LangChain Agent](https://www.runoob.com/langchain/langchain-first-agent.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：学习笔记
- 章节序号：0271

## 本章内容

我们要完成一个任务，有时需要查询外部数据、进行计算，或者连续执行多个操作，单纯依靠模型生成文本就不够了。

这时可以使用 Agent（智能体）。

Agent 可以根据用户的问题决定是否调用工具，在获得工具执行结果后再次调用模型，并重复这个过程，直到生成最终回答或达到停止条件。

本章节将使用 LangChain 的 create_agent() 创建第一个 Agent，并通过天气查询和数学计算两个工具，理解 Agent 的完整执行过程。


## 一、什么是 Agent？

Agent 是一种能够结合语言模型与外部工具完成任务的程序。

Agent 不只是生成回答，还可以根据任务需要选择工具，并利用工具返回的结果继续处理问题。


### 普通模型与 Agent 的区别


### Agent 的工作循环

Agent 的工作过程通常可以概括为：

```text
用户输入
   ↓
调用语言模型
   ↓
模型是否请求调用工具？
   ├── 否 → 生成最终回答
   │
   └── 是
        ↓
      执行工具
        ↓
      获得工具结果
        ↓
      再次调用模型
        ↓
      继续判断是否需要工具
```

这种循环常被概括为推理、行动、观察（Reasoning、Action、Observation）。

例如，用户提问：

```text
杭州今天的天气怎么样？
```

Agent 可能先调用天气查询工具，将返回的天气数据提供给模型，再由模型组织成自然语言回答。

注意：Agent 能否获取实时天气，取决于是否接入了真实的天气 API。本章节首先使用模拟数据，目的是学习 Agent 的运行机制，而不是查询真实天气。


## 二、安装与环境准备

本教程使用 LangChain 1.x 风格的 create_agent() API。

首先安装所需依赖：

```text
pip install -U langchain langchain-deepseek python-dotenv
```

其中：

- langchain：提供 Agent、工具以及统一模型调用接口。
- langchain-deepseek：提供 DeepSeek 模型集成。
- python-dotenv：读取项目中的环境变量配置。


### 配置 DeepSeek API Key

在项目目录创建 .env 文件：

```text
DEEPSEEK_API_KEY=your_deepseek_api_key
```

将 your_deepseek_api_key 替换为实际的 API Key。

然后在 Python 中加载：

```text
from dotenv import load_dotenv

load_dotenv()
```

本教程使用 DeepSeek 官方推荐的 deepseek-flash 模型。

对应的 LangChain 初始化方式为：

```text
from langchain.chat_models import init_chat_model

model = init_chat_model(
    "deepseek:deepseek-flash"
)
```

使用前请确认模型服务可访问，并且所用模型支持工具调用。

DeepSeek 官方同时提供 deepseek-v4-pro，如果需要，可以将模型名称修改为：

```text
model = init_chat_model(
    "deepseek:deepseek-v4-pro"
)
```


## 三、创建第一个 Agent

创建 Agent 主要分为三个步骤：

- 定义 Agent 可以调用的工具。
- 使用 create_agent() 创建 Agent。
- 调用 agent.invoke() 执行任务。


### 步骤 1：定义工具函数

LangChain 提供 @tool 装饰器，可以将普通 Python 函数转换为 Agent 可以使用的工具。

这里创建两个工具：

- get_weather()：查询指定城市的模拟天气。
- calculate()：计算简单的数学表达式。


## 实例

这里使用的是预先定义的字典数据。

如果用户查询杭州，工具返回：

```text
晴，25°C，湿度60%
```

如果查询没有收录的城市，就返回未找到数据的提示。

注意：这些数值是教学样例，并不代表真实天气。实际项目可以将字典替换为天气 API 请求。

@tool 会将 Python 函数转换为 LangChain 工具对象，并根据函数签名和描述信息建立工具定义。

例如：

```text
@tool
def get_weather(city: str) -> str:
    """查询指定城市的模拟天气数据。"""
    ...
```

其中：

- get_weather：工具名称。
- city: str：工具接收的参数及类型。
- 文档字符串：描述工具的用途。
- 返回值：工具执行后提供给 Agent 的结果。

模型会利用这些信息判断何时调用工具，以及应该传入什么参数。

因此，工具描述应尽量明确，并说明参数的含义。

第二个工具用于执行简单的数学计算。

原先使用 eval() 直接计算模型生成的表达式并不安全。即使移除了内置函数，也不建议将不可信表达式直接交给 eval()。

这里改用 Python 的 ast 模块，只允许数字、括号、加减乘除和一元正负号。


## 实例

例如，计算：

```text
3 * 7 + 2
```

工具返回：

```text
计算结果：3 * 7 + 2 = 23
```

这个计算器只支持有限的数学语法，不允许调用函数、访问对象属性或执行任意 Python 代码。

它适合教学演示。正式应用中仍应根据业务要求限制输入长度、计算复杂度和执行资源。


### 步骤 2：创建 Agent

定义工具之后，通过 create_agent() 将语言模型和工具组合起来。


## 实例

这里的 create_agent() 会创建一个由 LangGraph 支持的 Agent 执行图。

Agent 会根据模型返回的工具调用请求执行对应工具，并将工具结果加入消息历史。

对于初学者，通常只需要关注 model、tools 和 system_prompt 三个参数。

注意：工具列表为空时，Agent 不会执行工具调用循环，但仍可以使用语言模型完成回复。


### 步骤 3：运行 Agent

Agent 创建完成后，可以通过 invoke() 执行任务。

输入格式为：

```text
{
    "messages": [
        {
            "role": "user",
            "content": "杭州天气怎么样？"
        }
    ]
}
```

其中 messages 表示发送给 Agent 的消息列表。


## 实例

示例回答可能为：

```text
杭州的模拟天气为晴天，气温25°C，湿度60%。
```

这里的回答基于 get_weather() 中的模拟数据。

由于 Agent 的工具选择及模型输出具有一定动态性，实际回答可能有所不同。

如果希望查看完整执行过程，可以打印消息历史。


### 查看完整消息历史


## 实例

一次典型执行过程可能类似：

```text
消息类型： human
----------------------------------------
消息类型： ai
工具名称： get_weather
工具参数： {'city': '杭州'}
----------------------------------------
消息类型： tool
工具名称： get_weather
工具结果： 晴，25°C，湿度60%
----------------------------------------
消息类型： ai
AI 回复： 杭州的模拟天气是晴天，气温25°C，湿度60%。
----------------------------------------
```

这里可以看到四条消息：

- 用户消息 HumanMessage。
- 模型发起工具调用的 AIMessage。
- 工具执行结果 ToolMessage。
- 模型生成最终回答的 AIMessage。

注意：请求调用工具的 AI 消息，其 content 可能为空，但 tool_calls 中仍然包含工具名称、参数等信息。


## 四、Agent 执行流程解析

下面结合天气查询示例，解释 Agent 的内部执行流程。


### 第一步：接收用户问题

用户输入：

```text
杭州的模拟天气怎么样？
```

Agent 将用户消息发送给语言模型，同时提供当前可使用的工具定义。


### 第二步：模型判断是否调用工具

模型根据问题、系统提示词和工具描述，可能决定使用 get_weather。

此时模型返回的消息可能包含：

```text
{
    "name": "get_weather",
    "args": {
        "city": "杭州"
    }
}
```

这称为工具调用请求（Tool Call）。

这里要注意：模型负责提出工具调用请求，但不等于模型自己直接执行 Python 函数。


### 第三步：Agent 执行工具

LangChain 根据工具调用请求找到对应的工具，并传入参数。

例如：

```text
get_weather(city="杭州")
```

工具执行后返回：

```text
晴，25°C，湿度60%
```

该结果作为 ToolMessage 加入消息历史。


### 第四步：再次调用模型

模型读取工具执行结果，决定是否还需要调用其他工具。

如果不需要继续执行工具，就生成最终回答。

如果还需要其他数据，则可以再次发起工具调用。

因此，Agent 的核心机制可以概括为：

```text
Model → Tool Call → Tool Result → Model
```

这个循环通常持续到模型不再请求工具，或者达到执行限制、错误等停止条件。


## 五、让 Agent 调用多个工具

Agent 不仅可以调用一个工具，也可以根据任务需要组合多个工具。

例如：

```text
杭州和北京的模拟气温相差多少度？
```

对于这个问题，Agent 可能需要：

- 查询杭州的模拟天气。
- 查询北京的模拟天气。
- 计算两地气温差。
- 生成最终回答。


## 实例

一次可能的执行过程如下：

```text
[调用工具] get_weather 参数：{'city': '杭州'}
[调用工具] get_weather 参数：{'city': '北京'}
[工具结果] get_weather: 晴，25°C，湿度60%
[工具结果] get_weather: 多云，18°C，湿度45%
[调用工具] calculate 参数：{'expression': '25 - 18'}
[工具结果] calculate: 计算结果：25 - 18 = 7

最终回答：
根据模拟数据，杭州为25°C，北京为18°C，
两地气温相差7°C。
```

这里的重点是：用户不需要编写一套固定的工具调用顺序，模型可以根据当前任务和已返回的结果继续选择工具。


### 工具一定按顺序执行吗？

不一定。

如果模型一次返回多个工具调用请求，LangChain 的工具执行节点可以处理这些调用，其中独立调用可能并发执行。

但也可能出现以下情况：

- 模型先查询杭州，再查询北京。
- 模型一次请求查询两个城市。
- 模型获得天气数据后，自己完成简单减法，没有调用计算器。
- 模型根据用户请求调用计算器，再生成最终回答。

因此，不能假设 Agent 一定会调用三个工具，也不能保证两个天气工具调用一定并行。

如果某个步骤必须执行，或者必须按照特定顺序完成，应该通过明确的程序流程、工具编排或 LangGraph 工作流控制，而不是只依赖提示词。


## 六、工具调用与消息类型

LangChain Agent 执行过程中，主要涉及以下消息类型：


## 后续章节

- AIMessage.tool_calls
- ToolMessage
- 七、完整可运行示例
- 完整实例
- 运行代码
- 八、同步与异步调用
- 同步调用：invoke()
- 异步调用：ainvoke()
- 实例
- 九、Agent 流式输出
- 实例
- 十、限制 Agent 执行次数
- 十一、常见问题
- 1、为什么 Agent 没有调用工具？
- 2、为什么 AIMessage 的 content 为空？
- 3、为什么工具调用顺序与示例不同？

## 复习重点

- 能说明 `LangChain Agent` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
