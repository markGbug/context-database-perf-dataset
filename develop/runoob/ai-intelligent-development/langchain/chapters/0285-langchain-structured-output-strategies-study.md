# LangChain：LangChain 输出策略——ToolStrategy、ProviderStrategy 与 AutoStrategy

- 来源：[LangChain 输出策略](https://www.runoob.com/langchain/langchain-structured-output-strategies.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：学习笔记
- 章节序号：0285

## 本章内容

上一节我们学习了 LangChain 的 结构化输出（Structured Output）。

结构化输出可以让 Agent 按照 Pydantic、TypedDict 或 JSON Schema 定义的数据结构返回结果，方便程序直接处理。

在 LangChain 1.x 中，结构化输出主要有三种策略：ToolStrategy、ProviderStrategy 和 AutoStrategy。

本章节介绍它们的工作原理、参数配置、兼容性、错误处理和选择方法。


## 一、三种结构化输出策略

三种策略的主要区别在于：结构化数据通过哪种机制生成，以及由谁负责保证输出符合 Schema。

基本写法：

```text
# 使用 ToolStrategy
response_format=ToolStrategy(CourseInfo)

# 使用 ProviderStrategy
response_format=ProviderStrategy(CourseInfo)

# 自动选择
response_format=CourseInfo
```

通常推荐先直接传入 Schema。如果需要明确控制结构化输出机制，再手动指定 ToolStrategy 或 ProviderStrategy。

注意：三种策略并不是固定的性能排行榜。实际请求耗时、Token 消耗和稳定性取决于模型、Schema、API 及是否发生重试。


## 二、安装与环境准备

安装 LangChain 及相关依赖：

```text
pip install -U langchain langchain-deepseek python-dotenv pydantic
```

在项目目录创建 .env：

```text
DEEPSEEK_API_KEY=your_deepseek_api_key
```

加载环境变量：

```text
from dotenv import load_dotenv
load_dotenv()
```

本教程中 ToolStrategy 和自动策略主要使用 DeepSeek Flash 演示。

需要注意，DeepSeek 模型是否支持原生 Schema 约束，应以实际服务能力为准，不能直接假设它支持 ProviderStrategy。


## 三、ToolStrategy：通过工具调用输出数据

ToolStrategy 使用模型的 Tool Calling 能力实现结构化输出。

LangChain 会将 Schema 转换成用于结构化响应的工具定义，让模型生成符合工具参数要求的数据。

这里的工具主要负责表达输出结构，不代表真正执行了一个外部 API 或 Python 业务函数。

执行过程可以理解为：

```text
用户输入
    ↓
模型接收结构化输出 Schema
    ↓
模型生成 Tool Call
    ↓
LangChain 解析并验证参数
    ↓
structured_response
```


### 实例：提取天气描述

下面从用户提供的天气描述中提取城市、温度、天气状况和湿度。

所有信息来自输入文本，不会调用真实天气服务。


## 实例

成功执行时，结果可能为：

```text
{
    'city': '杭州',
    'temperature': 25.0,
    'condition': '晴天',
    'humidity': 60
}
```

由于传入的是 Pydantic 模型，解析成功后可以通过属性访问字段：

```text
print(report.city)
print(report.temperature)
print(report.humidity)
```

其中，humidity 使用 ge=0 和 le=100 约束湿度范围。


## 四、查看 ToolStrategy 的消息过程

使用 ToolStrategy 时，模型通常会生成一条结构化输出 Tool Call。

可以通过消息历史检查实际执行情况。


## 实例

如果模型第一次就生成了正确的结构化数据，可能看到：

```text
消息类型： human
结构化调用： [('WeatherReport', {...})]
工具消息： Returning structured response: ...
消息总数： 3
```

注意：不能将消息数量固定写成 4 条。

对于一次成功的 ToolStrategy 结构化响应，可能只包含用户消息、带 Tool Call 的 AIMessage，以及对应的 ToolMessage。

如果模型生成了无效数据，LangChain 可能反馈错误并再次请求模型，消息数量就会增加。

同样，ToolStrategy 也不代表每次一定额外调用一次模型 API。工具调用请求本身可以由一次模型响应生成。


## 五、ToolStrategy 的 handle_errors 参数

ToolStrategy 支持处理结构化输出错误，例如字段缺失、数值越界、Schema 验证失败，以及模型错误地产生多个结构化输出。

handle_errors 默认值为 True。

也就是说，默认情况下，LangChain 会尝试将受支持的结构化输出错误反馈给模型，让它重新生成符合要求的数据。


### 实例：使用默认错误处理


## 实例

如果模型输出 rating=10，校验会失败，LangChain 可以向模型反馈错误，让它尝试修改。

但模型不一定每次都能修正成功。


### 实例：自定义错误提示


## 实例

这里的字符串会作为固定错误提示。

注意：不要写成：

```text
handle_errors="格式有误：{error}"
```

然后假设 LangChain 会自动把 {error} 替换成具体异常。

如果需要根据错误内容生成提示，应传入 Callable。


### 实例：自定义错误处理函数


## 实例

实际使用时，可以把 strategy 传给 create_agent(response_format=strategy)。

需要注意，结构化输出重试不等于普通工具执行失败后的重试，也不等于网络请求失败后的 API 自动重试。


## 六、tool_message_content：自定义工具消息

ToolStrategy 还有一个有用的参数：

```text
tool_message_content
```

它可以设置结构化输出成功后，添加到消息历史中的 ToolMessage 内容。


### 实例


## 实例

这样结构化输出成功后，对应的工具消息可以显示为：

```text
天气描述已成功提取。
```

该参数只改变工具消息的文本，不会替代或修改最终的 structured_response 数据。


## 七、ProviderStrategy：使用原生结构化输出

ProviderStrategy 使用模型服务商提供的原生结构化输出接口。

例如，部分 OpenAI、Anthropic、Google 和 xAI 模型支持通过服务商能力约束输出结构。

这种方式通常能够利用提供商自己的 Schema 约束机制。

但不能简单认为某个模型系列的所有版本都支持，也不能保证 ProviderStrategy 在所有情况下都比 ToolStrategy 更快。


### 实例：使用支持原生结构化输出的模型

下面采用 OpenAI 兼容示例。运行前需要安装 langchain-openai 并配置相应 API Key。


## 实例

成功执行时，结果可能为：

```text
{
    'name': 'Python3 基础教程',
    'level': '入门',
    'price': '免费'
}
```

这里使用的是明确支持相应原生结构化输出功能时的调用方式。

注意：如果你使用其他提供商或模型，应先核对该模型的原生结构化输出支持情况。


### strict 参数

ProviderStrategy 支持可选的 strict 参数：

```text
response_format=ProviderStrategy(
    CourseInfo,
    strict=True
)
```

但 strict=True 需要对应模型提供商支持严格 Schema 约束，并不是所有模型都支持。

如果服务端不接受相应设置，可能直接返回 API 错误。


## 八、ProviderStrategy 是否一定比 ToolStrategy 快？

不一定。

ProviderStrategy 不需要将结构化输出表示为 Tool Calling 请求，但这不代表它一定能减少网络请求或获得更低延迟。

ToolStrategy 在一次成功调用中，也可以通过一次模型响应生成完整的结构化数据。

实际性能取决于：

- 模型生成速度与响应延迟。
- Schema 的复杂度。
- 是否需要多轮工具调用。
- 结构化输出失败后的重试次数。
- 模型提供商和网络环境。

因此，应通过真实请求测量，而不是仅根据消息数量判断。


### 性能比较应该看哪些指标？

如果业务非常关注成本与时延，建议使用相同的模型、Schema 和测试数据，对不同策略做多次对比。


## 九、AutoStrategy：自动选择结构化输出策略

LangChain 提供 AutoStrategy，用于根据模型能力自动选择结构化输出方式。

但在常规开发中，不需要显式创建 AutoStrategy。

只需要将 Pydantic 模型直接传给 response_format 即可。


## 后续章节

- 实例：课程评价分析
- 实例
- 自动策略如何选择？
- 十、通过 model.profile 检查模型能力
- 实例
- 十一、ToolStrategy 与 ProviderStrategy 的选择
- 十二、JSON Schema 与策略的注意事项
- 实例
- 十三、完整实例：动态选择输出策略
- 完整实例
- 十四、常见问题
- 1、AutoStrategy 需要手动创建吗？
- 2、ToolStrategy 是否所有模型都支持？
- 3、ToolStrategy 一定多调用一次模型吗？
- 4、handle_errors 的默认值是什么？
- 5、ProviderStrategy 一定比 ToolStrategy 快吗？

## 复习重点

- 能说明 `LangChain 输出策略` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
