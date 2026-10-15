# LangChain：LangChain 模型调用 -- init_chat_model() 函数

- 来源：[LangChain 模型调用](https://www.runoob.com/langchain/langchain-init_chat_mode.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：概念卡
- 章节序号：0272

## 本章内容

init_chat_model() 是 LangChain 提供的统一聊天模型初始化函数，可以通过相同的接口连接不同模型提供商。

例如，使用 DeepSeek、OpenAI、Anthropic、Google Gemini 或 Ollama 时，开发者不必分别记忆所有模型集成类的名称，只需要指定模型提供商和模型名称。

init_chat_model() 主要提供两种使用模式：

- 固定模型：创建模型时指定名称，后续直接调用。
- 可配置模型：允许运行时动态切换模型，或者修改指定的模型初始化参数。

此外，初始化后的聊天模型还可以通过统一接口实现同步调用、异步调用、流式输出等功能。

本章节将以 DeepSeek 为主要示例，同时介绍其他模型提供商的接入方法。

注意：LangChain 统一的是模型初始化和调用接口，不代表不同模型支持完全相同的功能、参数或上下文长度。


## 一、安装 LangChain

首先安装 LangChain：

```text
pip install -U langchain
```

init_chat_model() 不会自动安装所有模型提供商的集成包，因此还需要安装对应的依赖。

例如，使用 DeepSeek：

```text
pip install -U langchain-deepseek
```

使用 OpenAI：

```text
pip install -U langchain-openai
```

使用 Anthropic：

```text
pip install -U langchain-anthropic
```

使用 Ollama 本地模型：

```text
pip install -U langchain-ollama
```

如果需要通过 .env 文件加载 API Key，还可以安装：

```text
pip install -U python-dotenv
```


### 配置 API Key

调用 DeepSeek API 需要设置 DEEPSEEK_API_KEY 环境变量。

可以在项目目录创建 .env 文件：

```text
DEEPSEEK_API_KEY=your_deepseek_api_key
```

在 Python 程序中加载该文件：

```text
from dotenv import load_dotenv

load_dotenv()
```

如果使用其他提供商，可以配置对应的环境变量：

```text
OPENAI_API_KEY=your_openai_api_key
ANTHROPIC_API_KEY=your_anthropic_api_key
```

注意：这里只需要配置实际使用的提供商对应的密钥。不要将包含真实 API Key 的 .env 文件提交到公开代码仓库。


## 二、init_chat_model() 函数语法

函数的基本语法如下：

```text
from langchain.chat_models import init_chat_model

model = init_chat_model(
    model=None,
    *,
    model_provider=None,
    configurable_fields=None,
    config_prefix=None,
    **kwargs
)
```

参数说明：

init_chat_model() 通常有两种返回结果：

- 固定模型模式：返回实现 BaseChatModel 接口的聊天模型实例。
- 可配置模型模式：返回支持通过运行时配置选择模型或修改字段的包装对象。

下面分别介绍各参数的使用方式。


## 三、model 参数详解

model 用于指定需要调用的模型。

LangChain 推荐使用 provider:model 格式，明确指定提供商。


### 1、provider:model 格式

基本格式为：

```text
提供商名称:模型名称
```

例如：


## 实例

上述代码用于展示初始化方式，不会因为创建模型对象就自动完成一次聊天请求。

实际使用时，需要提前安装对应的 LangChain 集成包，并确认所指定的模型 ID 当前可用。

推荐：新项目优先使用 provider:model 格式，以减少模型提供商自动推断错误。


### 2、DeepSeek 当前推荐模型

根据 DeepSeek 官方 API 文档，目前推荐使用以下两个模型名称：

其中，deepseek-flash 是当前官方推荐的 Flash 模型名称。

旧的 deepseek-v4-flash 和 deepseek-v4-flash-vision-exp 名称仍保留兼容调用，但对应的旧模型已经下线，请求实际由 DeepSeek-V4.1-Flash 提供服务。

因此，新项目应优先使用：

```text
model = init_chat_model("deepseek:deepseek-flash")
```

需要使用 Pro 模型时：

```text
model = init_chat_model("deepseek:deepseek-v4-pro")
```

模型的功能、思考模式、价格和上下文长度可能随服务商调整，建议以 DeepSeek 官方模型文档 为准。


### 3、自动推断模型提供商

如果省略提供商前缀，LangChain 会尝试根据模型名称自动推断。


## 实例

常见的模型名称推断规则如下：

注意：自动推断不是通用的模型识别服务，只是根据预设的名称规则判断提供商。

例如，deepseek-flash 会被推断为 deepseek，而不是 openai。

Google Gemini 的默认推断规则也可能随 LangChain 版本变化，建议显式指定 google_genai 或 google_vertexai。


### 4、model_provider 参数

如果需要分别传递模型名称和提供商，可以使用 model_provider。

例如，下面两种写法在提供商和模型选择上等价：


## 实例

当模型配置从文件、数据库或环境变量中读取时，可以使用这种方式：

```text
provider = "deepseek"
model_name = "deepseek-flash"

model = init_chat_model(
    model_name,
    model_provider=provider
)
```

这种方式比较适合需要动态读取配置的应用。


## 四、固定模型模式

固定模型是 init_chat_model() 最常见的使用方式。

创建模型时指定名称和参数，然后使用 invoke() 调用。


### 实例：调用 DeepSeek Flash


## 实例

调用时，LangChain 会通过对应的 DeepSeek 集成向 API 发送请求。

invoke() 通常返回一个 AIMessage 对象，其中 content 保存响应内容。

由于模型是动态生成内容，每次调用的实际输出可能不同。


### 实例：调用 DeepSeek V4 Pro

如果需要使用 Pro 模型，只需要修改模型名称：


## 实例

这种方式不需要手动创建不同的模型集成类，直接替换模型 ID 即可。

注意：以上示例需要真实 API Key 和可用的模型服务，实际调用会产生相应的 API 费用。


## 五、通过 OpenAI 兼容接口调用 DeepSeek

DeepSeek 官方除了提供自己的 API，还提供与 OpenAI、Anthropic 格式兼容的接口。

官方地址如下：

因此，在 LangChain 中可以选择使用 DeepSeek 原生集成，也可以使用 OpenAI 兼容集成。


### 方式一：使用 DeepSeek 原生集成

需要安装：

```text
pip install -U langchain-deepseek
```

代码如下：

```text
model = init_chat_model(
    "deepseek:deepseek-flash"
)
```

这是使用 LangChain 接入 DeepSeek 时推荐的方式。


### 方式二：使用 OpenAI 兼容接口

如果希望通过 langchain-openai 调用 DeepSeek，可以单独指定模型提供商、API 地址和密钥。


## 实例

上述代码需要安装：

```text
pip install -U langchain-openai
```

这里虽然使用的是 openai 提供商，但实际请求发送到 DeepSeek API，而不是 OpenAI API。

这是通过自定义 base_url 实现的。

两种调用方式对比如下：

注意：兼容 OpenAI API 不代表第三方模型的所有特殊响应字段都会被通用集成完整处理。如果需要 DeepSeek 特定功能，应优先查看对应的 LangChain DeepSeek 集成是否支持。

此外，DeepSeek 的 Anthropic 兼容接口是另一套请求格式，不应简单地把该地址直接当成 OpenAI 格式的 base_url 使用。


## 六、可配置模型模式

如果希望在运行时切换模型，而不是每次创建新的模型变量，可以使用可配置模型。

这在模型对比、A/B 测试、成本管理和多模型应用中比较常见。


### 1、不指定 model

如果调用 init_chat_model() 时没有指定模型，LangChain 会返回可配置模型。

这种情况下，默认允许在运行时配置 model 和 model_provider。


## 实例

可以看到，同一个可配置模型对象，可以通过 config 指定不同的模型。

切换模型时不需要重新创建应用程序，但调用过程仍需要加载目标模型的集成并访问对应服务。


### 2、configurable_fields 参数

configurable_fields 用于控制允许运行时修改哪些字段。

常见取值如下：

例如，只允许修改模型名称：


## 后续章节

- 实例
- 七、config_prefix 参数
- 实例
- 实例
- 八、configurable_fields="any"
- 实例
- 九、支持的模型提供商
- 十、常用 kwargs 参数
- 实例
- 十一、常见模型调用方法
- 1、invoke() 同步调用
- 实例
- 2、stream() 流式输出
- 实例
- 3、ainvoke() 异步调用
- 实例

## 记忆卡片

- 一句话定义：`LangChain 模型调用` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
