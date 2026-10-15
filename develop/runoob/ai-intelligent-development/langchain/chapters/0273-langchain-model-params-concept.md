# LangChain：LangChain Chat Model 常用参数

- 来源：[LangChain 常用参数](https://www.runoob.com/langchain/langchain-model-params.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：概念卡
- 章节序号：0273

## 本章内容

上一节我们学习了 init_chat_model() 函数的基本用法。

使用 LangChain 调用大语言模型时，除了指定模型名称，还可以配置输出随机性、最大 Token 数、请求超时、失败重试和 API 地址等参数。

合理使用这些参数，可以更好地控制模型行为、接口响应时间和调用成本。

本章节将介绍 LangChain Chat Model 的常用参数，并使用 DeepSeek 模型进行演示。

注意：LangChain 提供统一的模型调用接口，但不同提供商、模型版本和思考模式支持的参数可能不同。某个参数可以成功传入，并不意味着它一定会影响模型输出。


## 一、安装与准备

本教程使用 LangChain 1.x 和 DeepSeek 官方模型接口。

首先安装依赖：

```text
pip install -U langchain langchain-deepseek python-dotenv
```

在项目目录创建 .env 文件：

```text
DEEPSEEK_API_KEY=your_deepseek_api_key
```

然后使用 load_dotenv() 加载环境变量：


## 实例

根据 DeepSeek 当前官方 API 文档，常用模型名称如下：

旧名称 deepseek-v4-flash 等可能仍作为兼容别名存在，新代码建议使用 deepseek-flash。


## 二、temperature：控制生成随机性

temperature 是聊天模型中常用的采样参数，用于调整模型生成内容时的随机程度。

通常情况下：

- 较低的 temperature：模型更倾向于选择概率较高的 Token。
- 较高的 temperature：模型可能产生更多样化的输出。

对于支持该参数的 DeepSeek Chat Completions 接口，temperature 的取值范围为 0～2。

例如：

```text
temperature=0.0
temperature=0.7
temperature=1.5
```

需要注意，这个范围不是 LangChain 对所有模型统一规定的范围。


### 实例：比较不同 temperature

下面通过相同问题，对比不同温度设置下的模型输出。

此示例仅适用于实际支持 temperature 调整的非思考模型或模式。


## 实例

如果当前模型处于非思考模式并实际支持 temperature 调整，可以观察其对输出的影响。

但模型每次生成的结果并不固定，较低温度也不能保证完全相同。


### temperature 的使用建议

这张表仅提供一般性的采样思路，并不是适用于所有模型的推荐配置。


### DeepSeek 思考模式的特殊规则

根据 DeepSeek 当前官方文档，思考模式不支持通过 temperature 调整采样行为。

为了兼容已有软件，即使请求中包含 temperature，接口也可能不报错，但该参数不会生效。

因此：

- 使用普通非思考模式时，应查看当前模型是否支持温度调整。
- 使用思考模式时，不应依赖 temperature 控制输出随机性。
- 不应通过两次输出是否相同来判断 temperature 一定生效。

建议：先确认当前模型模式和参数支持情况，再进行温度实验。如果希望比较采样参数的影响，应固定模型版本和其他请求设置。


## 三、max_tokens：限制输出 Token 数

max_tokens 用于设置模型单次请求允许生成的最大 Token 数量。

Token 是模型处理文本时使用的基本单位，但并不等同于字符或单词。

例如，下面几段文本的 Token 数可能不同：

```text
Hello, world!

你好，世界！

print("Hello, world!")
```

Token 数取决于具体模型使用的分词器，不能简单认为一个中文字一定等于两个 Token，或者一个 Token 一定对应固定数量的英文单词。


### 实例：设置最大输出长度

推荐在初始化模型时设置 max_tokens。


## 实例

如果模型和接口支持该参数，较低的上限通常会限制可生成的内容长度。

但 max_tokens=500 不代表模型一定会生成 500 个 Token。它设置的是上限，而不是目标输出数量。


### max_tokens 的注意事项

- 限制的是输出 Token，而不是输入内容长度。
- 达到上限时，模型回答可能不完整。
- 对于思考模型，输出预算可能同时涉及思考内容和最终回答。
- 实际计费可能包括输入、输出以及模型特定的其他 Token 类别。
- 参数名称和限制规则需要以具体模型 API 为准。

因此，max_tokens 可以帮助控制单次输出预算，但不能单独保证最终 API 费用。


### 使用 bind() 创建不同配置

如果已经创建了模型，可以使用 LangChain 的 bind() 方法生成带有额外调用参数的模型包装对象。


## 实例

bind() 不会修改原模型的初始化配置，而是返回一个带有绑定参数的新 Runnable。

这种方式适合在不同任务中复用同一个模型配置。

例如，分类任务可以使用较小的输出预算，而教程生成任务可以使用较大的输出预算。


## 四、查看实际 Token 使用量

相比简单计算输出文本的字符数，更可靠的做法是读取模型返回的 Token 使用统计。

LangChain 的 AIMessage 通常通过 usage_metadata 暴露标准化的 Token 统计信息。


### 实例


## 实例

对于提供使用量统计的模型，可能返回类似：

```text
{
    'input_tokens': 20,
    'output_tokens': 85,
    'total_tokens': 105
}
```

以上只是结构示例，不代表实际调用产生的固定 Token 数量。

不同模型还可能提供额外的 Token 明细，例如缓存命中或思考 Token 等。

如果 usage_metadata 为 None，表示该次响应没有提供标准化的使用量数据，不能直接认为实际消耗为零。


## 五、timeout：设置请求超时

timeout 用于控制模型请求的等待时间，避免网络请求长时间无法结束。

例如：

```text
timeout=30
```

通常表示按底层模型集成的定义设置 30 秒的请求超时。


### 实例


## 实例

设置超时时间可以避免部分网络请求无限等待，但具体超时行为可能涉及连接、读取和 SDK 的内部实现。

对于耗时较长的模型任务，不宜直接使用过短的超时时间，否则可能导致正常请求被提前中断。


### timeout 参考设置

以上只是工程配置参考值，不是 LangChain 或 DeepSeek 的强制规定。


## 六、max_retries：请求失败重试

max_retries 用于设置模型请求失败后的最大重试次数。

例如：

```text
max_retries=2
```

在集成支持相应重试策略的情况下，发生符合条件的临时错误时，可以重新发起请求。


### 实例


## 实例

max_retries 主要用于提高临时网络故障或部分服务端错误下的请求成功率。

但它不能修复所有错误。

例如：

- API Key 无效。
- 模型名称不存在。
- 请求参数不受支持。
- 账户没有模型调用权限。

这些错误一般需要修正配置，而不是通过增加重试次数解决。


### timeout 与 max_retries 的关系

假设设置：

```text
timeout=30
max_retries=3
```

如果当前模型集成允许初次请求之外再重试 3 次，那么在全部请求都失败时，可能进行最多 4 次尝试。

但不能简单地认为整个过程最多需要：

```text
4 × 30 = 120 秒
```

因为实际总耗时还可能包含：

- 重试前的等待和指数退避。
- 连接建立和网络延迟。
- 不同阶段的超时机制。
- SDK 或 HTTP 客户端的额外开销。

如果业务存在严格的整体请求时间预算，需要在应用层增加总超时控制，而不能只依赖模型初始化参数。


## 后续章节

- 七、base_url：自定义 API 地址
- 实例 1：通过 DeepSeek 原生集成
- 实例
- 实例 2：通过 OpenAI 兼容接口调用 DeepSeek
- 实例
- 实例 3：调用本地 vLLM 服务
- 实例
- base_url 安全注意事项
- 八、top_p：核采样参数
- 通用参数示例
- DeepSeek 的特殊规则
- 九、stop：设置停止序列
- 实例
- 实例
- 十、seed：控制可重复性
- 十一、rate_limiter：限制请求速率

## 记忆卡片

- 一句话定义：`LangChain 常用参数` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
