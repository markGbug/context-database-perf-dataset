# LangChain：LangChain Messages API 参考

- 来源：[LangChain Messages API](https://www.runoob.com/langchain/langchain-messages-api.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：练习笔记
- 章节序号：0305

## 本章内容

在 LangChain 中，无论是普通聊天、Agent 工具调用、多轮对话，还是图片、音频等多模态输入，都离不开 Messages（消息）。

Messages 是 LangChain 与聊天模型交互的基础数据结构，用于区分系统指令、用户输入、AI 回复和工具执行结果。

例如：

```text
SystemMessage → 告诉模型应该如何回答
HumanMessage  → 用户提出问题
AIMessage     → 模型生成回答或工具调用
ToolMessage   → 工具返回执行结果
```

本章节基于 LangChain 1.x，整理常用消息类型、ContentBlock 多模态结构、ToolCall、消息转换、历史裁剪以及在 Agent 中的实际用法。


## 一、LangChain 消息类型速查

LangChain 的消息对象通常继承自 BaseMessage。

常用消息如下：

这里需要区分两个概念：

- role：模型 API 通常使用的角色，例如 user、assistant、system、tool。
- type：LangChain 消息对象自身的类型标识，例如 human、ai、tool。

因此，HumanMessage 的 type 是 human，而不等于模型 API 中的 user。

另外，AIMessageChunk 虽然代表助手的流式回复，但其 Python 对象的 type 是 AIMessageChunk。


## 二、创建基本消息

可以从 langchain.messages 导入常见消息类。


### 实例：创建消息对象


## 实例

输出：

```text
system 你是 Python 编程助手。
human 什么是 Python？
ai Python 是一种通用编程语言。
tool 计算结果：42
```

注意，这里的 ToolMessage 是一个单独创建的示例对象。

真正发送给模型时，ToolMessage 应当与此前 AIMessage 中对应的工具调用请求配对，不能随意插入一个没有上下文的工具结果。


## 三、消息对象的常用属性

BaseMessage 提供了一些通用属性。


### 实例：读取消息属性


## 实例

如果 content 是普通字符串，LangChain 也可以将其表示为标准文本内容块。

注意：消息 ID 不一定由模型服务商返回。实际需要稳定标识时，可以在应用层为消息分配 ID。


## 四、HumanMessage：用户消息

HumanMessage 用于表示用户输入。

既可以包含普通文字，也可以在模型支持的情况下包含图片、文件等多模态内容。


### 实例：普通用户消息


## 实例

输出：

```text
human
Python 字典是什么？
```

在调用 Chat Model 或 Agent 时，通常不需要手动创建 HumanMessage，也可以直接使用 role 字典。


## 五、SystemMessage：系统指令

SystemMessage 用于向模型提供角色设定、行为规则和其他高优先级指令。


### 实例


## 实例

消息通常按照对话顺序排列。

如果使用 create_agent()，更常见的方式是通过 system_prompt 设置系统指令。

```text
agent = create_agent(
    model="deepseek:deepseek-chat",
    tools=[],
    system_prompt="你是 Python 编程老师。"
)
```

不建议把不可信文档内容直接转换为 SystemMessage，因为这会提高外部数据在提示词中的权限。


## 六、AIMessage：模型回复

AIMessage 表示模型生成的响应。

除了文字，还可能包含工具调用、Token 使用量和模型元数据。


### 主要属性


### 实例：查看 AIMessage


## 实例

如果服务商返回 Token 数据，usage_metadata 可能包含：

```text
{
    "input_tokens": 12,
    "output_tokens": 20,
    "total_tokens": 32
}
```

这里是示例格式，并非真实调用结果。

不同提供商对 Token 用量、额外元数据和内容块的支持可能有所不同。


## 七、ToolCall：模型请求调用工具

ToolCall 用于表示模型希望调用某个工具。

通常可以通过：

```text
AIMessage.tool_calls
```

读取。

一个工具调用常见的字段包括：


### 实例：创建工具调用消息


## 实例

重要：创建 AIMessage.tool_calls 不会自动执行工具。

如果直接使用 Chat Model，需要应用程序执行工具，再将结果作为 ToolMessage 返回给模型。

而使用 create_agent() 时，LangChain 可以自动管理常见的工具调用循环。


## 八、ToolMessage：工具执行结果

ToolMessage 用于表示工具执行后返回的结果。

其中最重要的属性是：

```text
tool_call_id
```

它必须对应先前 AIMessage 中某个 ToolCall 的 ID。


### 常用属性


### 实例：工具请求和结果配对


## 实例

两个 ID 必须一致：

```text
call_001
call_001
```

如果模型一次提出多个工具调用，就需要根据提供商的协议为每个调用提供正确的工具响应。

不要在一个尚未响应完所有工具调用的消息序列中，随意插入无关用户消息。


## 后续章节

- 九、完整工具调用消息序列
- 实例：手动执行工具
- 完整实例
- 十、AIMessageChunk：流式消息
- 实例：读取流式消息
- 实例
- 十一、合并流式消息 Chunk
- 实例：合并消息增量
- 实例
- 十二、ContentBlock：标准化多模态内容
- 十三、TextContentBlock 与 PlainTextContentBlock 的区别
- TextContentBlock
- PlainTextContentBlock
- 实例：创建标准文本内容块
- 实例
- 十四、图片输入 ImageContentBlock

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `LangChain Messages API` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
