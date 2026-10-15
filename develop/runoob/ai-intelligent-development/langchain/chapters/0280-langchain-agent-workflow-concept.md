# LangChain：LangChain Agent 工作流程

- 来源：[LangChain Agent 工作流程](https://www.runoob.com/langchain/langchain-agent-workflow.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：概念卡
- 章节序号：0280

## 本章内容

上一节我们学习了 create_agent() 函数的参数及基本用法。

本章节将进一步了解 Agent 的内部执行机制：模型如何选择工具、工具结果如何返回模型、Agent 在什么条件下结束，以及如何通过流式接口观察整个执行过程。

在 LangChain 1.x 中，create_agent() 基于 LangGraph 构建 Agent 执行图，能够自动管理模型调用、工具执行和状态更新。

本教程继续使用 DeepSeek Flash 模型，并使用模拟天气、模拟时间和课程查询工具进行演示。

注意：本章使用 LangGraph 1.1 及以上版本支持的 version="v2" 流式事件格式。旧版 LangGraph 的流式返回结构可能不同。


## 一、Agent 的基本执行循环

Agent 的核心机制可以概括为：

```text
调用模型 → 判断工具调用 → 执行工具 → 再次调用模型
```

当模型返回工具调用请求时，Agent 执行对应工具，并将结果加入消息历史。

随后，模型可以根据工具结果继续处理任务。

整个过程通常持续到模型不再请求工具，或者遇到其他停止、暂停或错误条件。

Agent 的基本流程如下：


### Model 节点与 Tools 节点

一个典型的 Agent 可以抽象成两个核心节点：

例如，用户提问：

```text
杭州的模拟天气和模拟时间分别是什么？
```

模型可能生成两个工具调用：

```text
get_weather(city="杭州")
get_time(city="杭州")
```

工具执行完成后，结果会作为 ToolMessage 返回，模型再生成最终回答。

注意：模型可能一次请求多个工具，也可能分多轮调用工具。因此，执行图的节点顺序和次数并不固定。


## 二、安装与环境准备

本教程使用 LangChain 1.x，并采用 LangGraph v2 流式格式。

安装或更新依赖：

```text
pip install -U langchain langgraph langchain-deepseek python-dotenv
```

使用 version="v2" 需要 LangGraph 1.1 或更新版本。

项目目录中的 .env 文件：

```text
DEEPSEEK_API_KEY=your_deepseek_api_key
```

创建模型时使用：

```text
model = init_chat_model(
    "deepseek:deepseek-flash"
)
```

实际调用前需要确认已正确配置 API Key，并且对应模型支持工具调用。


## 三、追踪 Agent 的完整执行过程

接下来定义两个工具：

- get_weather()：返回模拟天气。
- get_time()：返回模拟时间。

为了方便观察，两个工具都使用固定字典数据，不会调用真实的天气或时间接口。


### 实例：使用 updates 追踪执行节点


## 实例


### 可能的执行过程

如果模型在同一轮请求两个工具，日志可能类似：

```text
=== Agent 执行过程 ===

--- 更新事件 1 ---
节点： model
[请求工具] get_weather {'city': '杭州'}
[请求工具] get_time {'city': '杭州'}

--- 更新事件 2 ---
节点： tools
[工具结果] get_weather 晴，25°C
[工具结果] get_time 14:30

--- 更新事件 3 ---
节点： model
[模型回复] 杭州的模拟天气为晴天、25°C，
模拟时间为14:30。
```

这里包含三次节点更新：

- Model：模型生成两个工具调用请求。
- Tools：工具执行，返回模拟天气和时间。
- Model：模型读取工具结果并生成回答。

但是，三次更新只是其中一种可能的执行路径。

模型也可能先调用天气工具，下一轮再调用时间工具，这样就会产生更多节点更新。

如果多个工具在同一轮执行，工具结果也不一定按照模型请求的顺序完成。


## 四、理解 Agent 的消息变化

除了观察节点，还可以查看执行过程中产生的消息。

一次典型的工具调用包含以下消息：

```text
HumanMessage
    ↓
AIMessage(tool_calls=[...])
    ↓
ToolMessage
    ↓
AIMessage(最终回答)
```

如果模型一次请求两个工具，消息可能为：

```text
HumanMessage
    ↓
AIMessage（两个 tool_calls）
    ↓
ToolMessage（天气）
ToolMessage（时间）
    ↓
AIMessage（最终回答）
```

其中：

注意，包含工具调用的 AIMessage，其普通文本内容可能为空，但 tool_calls 中仍然有工具请求。

因此，观察 Agent 工作流程时，应同时检查：

```text
message.content
message.tool_calls
message.type
```

不要简单根据 content 是否为空，判断模型是否调用了工具。


## 五、stream_mode 参数详解

agent.stream() 支持不同的流式模式，用于获取不同粒度的数据。

updates、messages 和 custom 是 LangChain Agent 官方入门文档重点介绍的模式；values 和 debug 等也可参考 LangGraph 流式文档。

使用 version="v2" 时，流事件采用统一结构：

```text
{
    "type": "updates",
    "ns": [],
    "data": {
        "model": {
            "messages": [...]
        }
    }
}
```

其中：

- type：当前流式模式。
- ns：事件所属的图或子图命名空间。
- data：具体事件内容。

不同 stream_mode 的 data 内容不同。


## 六、stream_mode="updates"：查看节点更新

updates 用于观察 Agent 的执行步骤。

每当相关节点产生状态更新时，就可以收到相应事件。


### 实例


## 实例

如果模型调用天气工具，可能观察到：

```text
节点： model
ai

节点： tools
tool 晴，25°C

节点： model
ai 杭州的模拟天气为晴天，气温25°C。
```

这种模式适合调试 Agent 工具调用，以及在后台展示当前执行到哪个节点。

注意：一个节点更新事件不一定等于一次工具调用。一个 Tools 节点更新中可能包含多条工具结果。


## 七、stream_mode="values"：查看完整状态

updates 主要显示节点产生的变化，而 values 用于观察运行过程中的完整状态。

例如，可以查看每次更新后的消息数量。


### 实例


## 实例

如果工具调用流程是：

```text
用户 → 模型请求工具 → 工具返回 → 模型回答
```

那么观察到的消息数量可能依次增长：

```text
状态快照 1：1 条消息
状态快照 2：2 条消息
状态快照 3：3 条消息
状态快照 4：4 条消息
```

但具体快照数量和消息数量会受到实际执行路径影响，不能将其视为固定结果。

注意：不要在尚未执行完成时，仅仅为了减少打印次数就随意 break 退出流式循环。

提前停止消费事件可能使执行过程、资源清理或后续结果处理变得不完整。教学示例建议消费完整个事件流。


## 八、stream_mode="messages"：流式生成文本

messages 用于获取语言模型生成过程中的消息片段。

它适合制作类似 ChatGPT 的流式打字效果。

需要注意，流式返回的并不一定是一个完整 Token，也不一定只包含普通文本。

模型可能产生：

- 文本消息片段。
- 工具调用参数片段。
- 推理内容块。
- 响应元数据。


### 实例：逐步输出模型文本


## 实例

代码中的 message_chunk 通常是 AIMessageChunk。

metadata 中可以包含当前节点名称等信息。

由于不同模型的流式响应格式可能不同，message_chunk.text 可能为空。

如果模型返回工具调用、思考内容等非普通文本块，还需要根据对应的数据结构进行处理。


### 流式工具调用

如果 Agent 注册了工具，模型在流式输出期间还可能逐步返回工具调用参数。

例如：

```text
工具名称：get_weather
参数片段：{"city":
参数片段："杭州"
参数片段：}
```

这些片段不一定是完整的 JSON。

需要等待必要的消息片段合并后，才能将工具调用作为完整请求理解。

因此，在展示 Agent 过程时，通常建议：

- 使用 messages 显示模型生成中的文本。
- 使用 updates 显示已经完成的工具调用和工具结果。


## 九、stream_mode="custom"：自定义进度事件

除了模型和图节点产生的事件，开发者还可以从工具内部发送自定义进度。

例如，一个需要处理大量文件的工具，可以持续报告当前处理数量。

LangChain 可以通过 get_stream_writer() 获取流式写入器。


### 实例：工具发送进度提示


## 实例

如果模型调用工具，可以观察到类似进度：

```text
{'task': '测试文档', 'current': 1, 'total': 3, 'message': '已处理 1/3 个文档'}
{'task': '测试文档', 'current': 2, 'total': 3, 'message': '已处理 2/3 个文档'}
{'task': '测试文档', 'current': 3, 'total': 3, 'message': '已处理 3/3 个文档'}
```

这里没有真正读取文件，只是通过循环模拟进度。

注意：get_stream_writer() 需要适当的 LangGraph 执行上下文。直接调用包含它的工具函数时，可能无法获得对应的流式写入器。

真实项目可以将自定义事件发送给前端，用于展示上传进度、数据处理进度或任务阶段。


## 十、同时使用多个 stream_mode

如果需要同时观察节点更新和模型文本，可以传入多个模式。

例如：

```text
stream_mode=["messages", "updates"]
```

在 v2 格式中，不同事件都使用同样的外层结构，可以通过 event["type"] 区分。


### 实例：同时观察工具调用与文本输出


## 后续章节

- 实例
- 十一、Agent 在什么情况下停止？
- 1、模型不再调用工具
- 2、return_direct=True
- 3、结构化输出完成
- 4、中间件控制结束
- 5、执行限制
- 6、中断与暂停
- 十二、实例：比较无工具与有工具的执行流程
- 实例
- 实例
- 十三、限制 Agent 的执行步数
- 实例
- 实例
- 十四、invoke() 与 stream() 的区别
- 实例：异步流式调用

## 记忆卡片

- 一句话定义：`LangChain Agent 工作流程` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
