# LangChain：LangChain 流式输出 Streaming

- 来源：[LangChain 流式输出](https://www.runoob.com/langchain/langchain-streaming.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：学习笔记
- 章节序号：0283

## 本章内容

流式输出（Streaming）可以让 AI 在生成回复的过程中逐步返回内容，而不是等整个任务完成后才一次性显示结果。

例如，ChatGPT 的打字效果就是常见的流式交互形式。

在 LangChain 中，不仅可以流式获取模型文本，还可以实时观察 Agent 的工具调用、节点更新和自定义任务进度。

本章节介绍 LangChain 1.x 的 stream()、astream() 和各种 stream_mode，最后使用 FastAPI 实现一个可供前端调用的 SSE 流式接口。


## 一、为什么需要流式输出？

使用 invoke() 时，程序通常需要等待模型或 Agent 完成执行后，才能获取完整结果。

如果 Agent 需要调用多个工具，用户在等待期间可能看不到任何进展。

流式输出可以在任务执行过程中持续发送事件，让用户更早看到模型文本、工具调用或任务状态。

注意：流式输出主要改善响应内容的可见性，不保证整个任务的总执行时间更短。

另外，Streaming 不一定每次返回一个 Token，实际返回的是消息片段或执行事件。


## 二、安装与环境准备

本教程使用 LangChain 1.x、LangGraph 1.1 或更新版本，并以 DeepSeek Flash 作为演示模型。

安装依赖：

```text
pip install -U langchain langgraph langchain-deepseek python-dotenv
```

在项目目录创建 .env 文件：

```text
DEEPSEEK_API_KEY=your_deepseek_api_key
```

初始化模型及 Agent：


## 实例

接下来的示例统一使用 version="v2"。

与旧版流式格式不同，v2 事件采用统一结构：

```text
{
    "type": "messages",
    "ns": [],
    "data": (...)
}
```

其中：

- type：事件对应的流模式。
- ns：事件所属图或子图的命名空间。
- data：具体事件内容。


## 三、stream_mode="messages"：实时输出模型文本

stream_mode="messages" 用于获取语言模型生成过程中的消息片段。

它非常适合实现 AI 聊天的打字效果。

在 v2 格式中，事件的 data 通常包含：

```text
(message_chunk, metadata)
```

message_chunk 是消息片段，metadata 则包含节点来源等相关信息。


### 实例：终端流式输出


## 实例

如果模型正常返回内容，终端会逐步显示类似文本：

```text
实时流式输出：
菜鸟教程 RUNOOB 是一个提供编程语言、开发工具和相关技术教程的在线学习网站。
```

与 invoke() 不同，这里通过 for 循环逐步接收消息。

chunk.text 用于提取消息片段中的文本，而不是直接打印整个 content。

注意：流式响应可能包含工具调用片段、推理内容或其他结构化内容，不能假设所有片段都是普通字符串。


## 四、理解 message_chunk 和 metadata

除了显示文本，开发者还可以查看流式消息的类型和来源。

例如：

- 当前消息来自哪个节点。
- 消息片段属于哪种 Python 类型。
- 模型是否正在生成工具调用。


### 实例：查看消息元数据


## 实例

可能输出：

```text
文本片段： 你好
来源节点： model
消息类型： AIMessageChunk
```

这里先完整消费事件流，再打印收集到的第一个非空文本片段。

不建议为了查看一个片段，就直接在流式循环中随意 break，因为这可能导致当前流没有被完整消费。


### AIMessageChunk 不等于一个 Token

AIMessageChunk 表示流式模型消息的一部分。

一次返回可能包含几个字符、一个词、一段文本，甚至包含工具调用参数片段。

因此，不应该按照"一个 Chunk 等于一个 Token"计算 Token 消耗。


## 五、stream_mode="updates"：查看 Agent 执行过程

updates 模式用于查看 Agent 执行图中各节点产生的状态更新。

例如，一个课程查询 Agent 可能按照以下顺序运行：

```text
用户提问
   ↓
model：请求调用 search_course
   ↓
tools：执行搜索
   ↓
model：生成最终回答
```

这非常适合在开发阶段观察 Agent 的工具执行过程。

注意：节点更新展示的是执行步骤，不等于模型内部的私有推理过程。


### 实例：追踪工具调用


## 实例

如果模型选择调用工具，执行日志可能类似：

```text
节点： model
工具请求： [('search_course', {'keyword': 'python'})]

节点： tools
工具结果： search_course Python3 基础教程

节点： model
AI 回答：可以先学习 Python3 基础教程。
```

实际工具调用次数和输出顺序由模型决定，并不是固定执行三步。

此外，一个 tools 节点更新可能包含多个工具执行结果。


## 六、stream_mode="values"：查看完整状态

updates 返回节点更新，而 values 用于观察运行过程中的完整 State。

例如，可以查看消息历史如何逐步增加。


### 实例


## 实例

如果模型进行了一次工具调用，消息历史可能依次包含：

```text
['human']
['human', 'ai']
['human', 'ai', 'tool']
['human', 'ai', 'tool', 'ai']
```

但状态快照数量和消息数量并不保证固定。

对于需要观察全部对话内容或调试自定义 State 的应用，values 比 updates 更方便。

不过，完整 State 可能包含较多数据，因此生产环境不建议无条件将所有状态返回前端。


## 七、stream_mode="custom"：自定义进度事件

除了模型文本和节点更新，LangChain 还允许开发者发送自定义事件。

例如，处理多个文件时，可以实时报告当前进度：

```text
正在处理文件 1/3
正在处理文件 2/3
正在处理文件 3/3
```

可以通过 get_stream_writer() 在支持的图节点或工具执行上下文中发送自定义数据。


### 实例：工具发送模拟进度


## 实例

如果模型调用了该工具，可能收到：

```text
{'task': '测试文件', 'current': 1, 'total': 3, 'message': '已处理 1/3'}
{'task': '测试文件', 'current': 2, 'total': 3, 'message': '已处理 2/3'}
{'task': '测试文件', 'current': 3, 'total': 3, 'message': '已处理 3/3'}
```

这里没有处理真实文件，只是模拟进度。

自定义事件不仅可以从 Middleware 发送，工具和 LangGraph 节点也可以发送。

注意：get_stream_writer() 需要在受支持的运行时上下文中使用，不能假设直接调用普通 Python 函数时也存在流式写入器。


## 八、组合多个 stream_mode

在实际 Agent 应用中，通常需要同时展示：

- 模型正在生成的文本。
- 当前执行到哪个节点。
- 调用了哪个工具。
- 工具是否完成。

可以组合多个流模式：

```text
stream_mode=["messages", "updates", "custom"]
```

使用 v2 格式时，可以根据 event["type"] 区分不同事件。


### 实例：同时展示模型文本与工具结果


## 实例

这个例子复用了上一节的 process_files 工具及其 Agent。

可能观察到：

```text
[节点] model
[进度] 已处理 1/3
[进度] 已处理 2/3
[进度] 已处理 3/3
[节点] tools
三个模拟文件处理完成
[节点] model
```

实际事件的数量、顺序和模型文本可能有所不同。

组合模式适合用于完整的 Agent 前端界面，但如果事件过多，也需要考虑前端渲染和网络传输成本。


## 九、异步流式输出 astream()

对于 FastAPI、WebSocket 等异步应用，可以使用 astream()。

它通过 async for 逐步接收事件，不需要阻塞等待全部结果。


### 实例：异步流式聊天


## 后续章节

- 实例
- 十、FastAPI 集成：实现 SSE 流式接口
- 安装依赖
- 完整服务端代码
- 实例
- 浏览器接收 SSE
- 实例
- 十一、stream_mode 速查表
- 十二、常见问题
- 1、Streaming 是否意味着模型生成得更快？
- 2、为什么 messages 返回的不是完整句子？
- 3、AIMessageChunk 是否等于一个 Token？
- 4、为什么 chunk.content 不是字符串？
- 5、updates 与 messages 有什么区别？
- 6、如何同时显示工具调用和 AI 打字效果？
- 7、custom 是否只能在 Middleware 中使用？

## 复习重点

- 能说明 `LangChain 流式输出` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
