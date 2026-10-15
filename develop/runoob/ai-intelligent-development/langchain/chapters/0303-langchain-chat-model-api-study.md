# LangChain：LangChain Chat Model API 参考

- 来源：[LangChain Chat Model API](https://www.runoob.com/langchain/langchain-chat-model-api.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：学习笔记
- 章节序号：0303

## 本章内容

LangChain 提供统一的 Chat Model 接口，让开发者可以使用相似的代码调用 OpenAI、Anthropic、DeepSeek、Google Gemini、Ollama 等不同模型。

其中，init_chat_model() 用于初始化聊天模型，BaseChatModel 则定义了模型调用、流式输出、批量执行、工具绑定和结构化输出等常用接口。

本章节基于 LangChain 1.x，系统整理模型初始化参数、BaseChatModel 常用方法、模型提供商、动态切换、AIMessage 数据结构及常见问题。


## 一、init_chat_model() 是什么？

init_chat_model() 是 LangChain 提供的统一聊天模型初始化函数。

例如，使用 DeepSeek：

```text
from langchain.chat_models import init_chat_model

model = init_chat_model("deepseek:deepseek-chat")
response = model.invoke("你好")
print(response.content)
```

如果改用其他服务商，通常只需要修改模型标识，并安装对应集成包。

模型名称建议使用：

```text
provider:model_name
```

例如：

```text
deepseek:deepseek-chat
openai:gpt-4o
anthropic:claude-sonnet-4-5-20250929
google_genai:gemini-2.5-flash
ollama:llama3.2
```

以上为模型标识格式示例，具体模型是否仍可调用，应以对应服务商的模型列表和账号权限为准。

如果不提供 provider，LangChain 会尝试从模型名称推断服务商，但这种推断并非适用于所有模型。

建议：在正式项目中明确指定 provider，避免模型名称相似时被错误识别。


## 二、init_chat_model() 函数签名

当前 API 的核心函数签名如下：

```text
init_chat_model(
    model: str | None = None,
    *,
    model_provider: str | None = None,
    configurable_fields: Literal["any"] | list[str] | tuple[str, ...] | None = None,
    config_prefix: str | None = None,
    **kwargs
)
```

它主要包含四个显式参数，以及用于传递具体模型配置的 **kwargs。

函数通常返回一个 BaseChatModel 实例；如果启用动态配置，则返回支持运行时选择模型参数的包装对象。


## 三、常用模型配置参数

除了核心参数，init_chat_model() 还可以通过 **kwargs 传递模型配置。

需要注意：这些并非所有服务商都统一支持的固定参数。

例如：


## 实例：配置模型

这个示例设置了输出长度、超时和重试等参数。

注意：temperature=0 不保证每次生成结果都完全相同。部分推理模型还可能限制或忽略 temperature 等采样参数。


## 四、固定模型与动态模型

init_chat_model() 支持两种常见模式：

- 固定模型：创建时确定模型，后续正常调用。
- 动态模型：运行时通过 config 选择模型或修改允许的参数。


### 方式一：固定模型


## 实例

没有配置 configurable_fields 时，显式指定的模型默认是固定模型。


### 方式二：动态调整参数

如果希望不同请求使用不同的 temperature，可以明确配置：


## 实例

这里允许每次调用通过 config 修改 temperature，其他模型配置仍使用默认值。


### 方式三：动态切换模型

可以允许模型名称在运行时变化：


## 实例

如果要在不同提供商之间切换，需要安装对应集成包，并配置所需的 API Key。

例如切换到 OpenAI 时，还需要 langchain-openai 和有效的 OpenAI API Key。


## 五、model=None 的特殊行为

如果创建模型时没有指定 model：

```text
model = init_chat_model()
```

LangChain 会创建一个可以在运行时指定模型的配置对象。

这时默认允许配置：

```text
model
model_provider
```


### 实例：运行时确定模型


## 实例

注意：如果创建时没有默认模型，调用时又没有在 config 中指定模型，通常会出现配置错误。


## 六、config_prefix：动态配置前缀

当同一个应用包含多个可配置模型时，可以通过 config_prefix 区分它们。

例如：

```text
chat_model
summary_model
```

这适用于一个模型负责普通对话，另一个模型负责摘要的场景。


### 实例：使用配置前缀


## 实例

这里的动态配置键变成：

```text
chat_temperature
```

如果没有 config_prefix，则直接使用：

```text
temperature
```

安全提醒：不要在接受用户输入的服务中随意设置 configurable_fields="any"。因为它可能允许在运行时修改 api_key、base_url 等敏感配置，带来请求重定向或凭据泄露风险。


## 七、BaseChatModel 是什么？

BaseChatModel 是 LangChain 聊天模型的核心抽象类。

不同服务商的模型虽然 API 地址、参数和返回格式存在差异，但通过 BaseChatModel 提供了统一的调用方式。

例如：

```text
model.invoke()
model.ainvoke()
model.stream()
model.astream()
model.batch()
model.bind_tools()
model.with_structured_output()
```

因此，可以在不同模型之间复用大量应用代码。


## 八、BaseChatModel 常用方法速查

这里的返回值是常见类型。使用 bind_tools、with_structured_output 等包装方法后，具体返回结构会受到模型和配置影响。


## 九、invoke()：同步调用模型

invoke() 是最常见的模型调用方法。

它支持普通字符串，也支持消息列表。


### 实例：字符串输入


## 实例

典型返回对象为 AIMessage。


### 实例：消息列表


## 实例

与单个字符串相比，消息列表可以明确区分系统指令和用户输入。


## 后续章节

- 十、ainvoke()：异步调用
- 实例
- 实例
- 十一、stream()：流式输出
- 实例：逐步打印回答
- 实例
- 十二、astream()：异步流式输出
- 实例
- 十三、batch()：批量调用模型
- 实例：批量处理问题
- 实例
- 十四、AIMessage：模型返回对象
- 常用字段
- 实例：查看响应详情
- 实例
- 十五、bind_tools()：绑定工具

## 复习重点

- 能说明 `LangChain Chat Model API` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
