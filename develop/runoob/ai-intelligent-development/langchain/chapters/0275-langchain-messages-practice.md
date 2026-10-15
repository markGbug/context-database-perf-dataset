# LangChain：LangChain 消息类型

- 来源：[LangChain 消息类型](https://www.runoob.com/langchain/langchain-messages.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：练习笔记
- 章节序号：0275

## 本章内容

在 LangChain 中，聊天模型和 Agent 主要通过消息（Message）进行交互。

消息不仅可以包含普通文本，还可以包含系统指令、工具调用、工具执行结果，以及图片等多模态内容。

理解 LangChain 的消息类型，有助于开发多轮对话、Agent、工具调用和多模态 AI 应用。

本章节基于 LangChain 1.x 的消息 API，介绍常用消息类型、消息属性、流式消息以及消息历史管理。


## 一、LangChain 的核心消息类型

LangChain 常用的四种消息类型分别是：

一个简单的对话可以表示为：

```text
SystemMessage：你是一名 Python 编程助手。

HumanMessage：什么是 Python？

AIMessage：Python 是一种通用编程语言。
```

如果使用工具，消息流程可能变成：

```text
HumanMessage
    ↓
AIMessage（包含 tool_calls）
    ↓
ToolMessage（工具执行结果）
    ↓
AIMessage（最终回答）
```

这些消息会组成消息列表，用于向聊天模型提供对话上下文。


## 二、HumanMessage：用户消息

HumanMessage 用于表示用户发送给聊天模型的内容。

例如：


## 实例

可能输出：

```text
消息类型： human
消息内容： 菜鸟教程 RUNOOB 是什么？
消息 ID： None
```

其中：

- content：消息内容。
- type：LangChain 消息类型，HumanMessage 为 human。
- id：消息标识，可能为 None，也可能由调用方或模型提供商设置。

注意：不能直接假设 HumanMessage 对象存在 role 属性。LangChain 消息对象通常使用 type 标识消息类型，而 OpenAI 风格的消息字典使用 role 字段。


### 使用 HumanMessage 调用模型


## 实例

模型通常返回一个 AIMessage 对象，其中包含生成的回复。

本例需要提前安装 langchain、langchain-deepseek 和 python-dotenv，并配置 DEEPSEEK_API_KEY。


### HumanMessage 的快捷写法

除了直接创建消息对象，LangChain 还支持通过元组和字典描述消息。


## 实例

需要注意，元组和字典本身不会立即变成 HumanMessage 对象。

只有在传入接受 MessageLike 格式的 LangChain API 时，框架才会按需进行消息转换。

例如：

```text
messages = [
    ("system", "你是一名编程助手"),
    ("user", "介绍 Python")
]

response = model.invoke(messages)
```

这种写法可以减少重复创建消息对象的代码。


## 三、AIMessage：AI 回复

AIMessage 表示语言模型生成的消息。

除了普通文本，AIMessage 还可以包含工具调用信息、Token 使用统计和响应元数据。


### 创建普通 AIMessage


## 实例

执行结果：

```text
类型： ai
内容： 菜鸟教程是一个在线编程学习平台。
工具调用： []
```

这里的 tool_calls 是空列表，说明这条消息没有提供标准化的工具调用请求。


### 包含工具调用的 AIMessage

当模型需要调用工具时，可以通过 tool_calls 返回工具名称与参数。


## 实例

执行结果：

```text
消息内容：
工具名称： get_weather
工具参数： {'city': '杭州'}
调用 ID： call_001
```

这里手动构造了一条带有工具调用请求的消息，仅用于展示数据结构。

实际调用时，工具调用 ID 通常由模型服务生成。

需要特别注意：AIMessage 中出现 tool_calls，并不表示工具已经执行。

工具需要由应用程序或 Agent 执行。


### AIMessage 的附加信息

模型返回的 AIMessage 还可能提供以下信息：


### 实例：查看模型响应信息


## 实例

不同模型提供商返回的 response_metadata 字段可能不同。

例如，模型名称、结束原因等字段的名称并不保证完全一致，因此不应依赖固定的元数据结构。

usage_metadata 是 LangChain 提供的标准化使用量字段，但也取决于服务商是否返回相关数据。


## 四、SystemMessage：系统指令

SystemMessage 通常用于向模型提供系统级指令，例如角色设定、回答风格和任务要求。

它一般放在消息列表的开头。


### 实例：设置回答风格


## 实例

模型会参考系统指令来组织回答。

例如，可以通过 SystemMessage 要求：

- 使用中文回答。
- 限制回答长度。
- 采用指定的解释风格。
- 优先使用提供的资料。
- 对未知信息明确说明。

注意：系统指令能够影响模型行为，但不能保证模型严格遵守所有要求。

对于必须执行的业务规则，例如用户权限、文件访问范围和支付校验，仍应在应用程序中实现，不能只依赖 SystemMessage。


## 五、ToolMessage：工具执行结果

ToolMessage 用于保存工具执行后返回的信息。

每个工具结果需要通过 tool_call_id 与先前的工具调用请求关联。


### 实例：完整的工具调用消息


## 实例

模型可以基于工具结果生成类似回答：

```text
根据提供的模拟数据，杭州天气晴，
气温25°C，湿度60%。
```

这里需要注意：

- AIMessage.tool_calls[0]["id"] 是工具调用 ID。
- ToolMessage.tool_call_id 必须与对应的调用 ID 匹配。
- 如果一条 AIMessage 包含多个工具调用，就需要提供对应的工具结果。
- 工具消息通常不能作为与上下文无关的独立用户输入。

不匹配或缺失的工具结果可能导致模型 API 拒绝请求，具体行为取决于提供商。

注意：本例中的天气数据是模拟数据，不是实时查询结果。


### ToolMessage 的其他属性

除了 content 和 tool_call_id，ToolMessage 还支持一些附加字段。

例如，部分场景可以使用 artifact 保存不需要直接发送给模型的完整工具结果：


## 实例

content 可以保存供模型使用的简要结果，artifact 则可以保存应用需要的补充数据。

不过，artifact 不是模型自动理解或使用的内容，具体处理方式取决于应用程序。


## 六、AIMessageChunk：流式消息片段

使用 stream() 时，模型可以逐步返回消息片段。

对于常见聊天模型，流式响应通常包含 AIMessageChunk。

与完整的 AIMessage 不同，消息片段可能只包含部分文本或部分工具调用信息。


## 后续章节

- 实例：流式输出
- 实例
- 合并消息片段
- 实例
- 七、LangChain 消息属性速查表
- 八、ContentBlock：结构化消息内容
- 常见 ContentBlock 类型
- 实例：构建文本内容块
- 实例
- 九、多模态消息：文本与图片
- 实例：通过图片 URL 提问
- 实例
- 实例：标准化图片内容块
- 实例
- 实例：读取本地图片
- 实例

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `LangChain 消息类型` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
