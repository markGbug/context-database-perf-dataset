# LangChain：LangChain Chat Model 高级用法

- 来源：[LangChain Chat Model 高级用法](https://www.runoob.com/langchain/langchain-model-advanced.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：练习笔记
- 章节序号：0274

## 本章内容

前面我们已经学习了如何通过 init_chat_model() 初始化模型，以及如何使用 invoke() 调用模型。

本章节介绍 LangChain Chat Model 的两个重要功能：

- bind_tools()：将工具定义绑定到模型，使模型能够根据任务生成工具调用请求。
- with_structured_output()：按照指定的数据结构（Schema）解析模型输出，方便程序直接使用。

这两个功能经常用于 Agent、数据提取、自动化任务和 AI 应用开发。

需要注意，bind_tools() 与 with_structured_output() 的用途不同，但底层实现可能都涉及模型的工具调用能力。


## 一、安装与环境准备

本教程使用 LangChain 1.x，并以 DeepSeek 官方推荐的 deepseek-flash 模型为主要示例。

首先安装依赖：

```text
pip install -U langchain langchain-deepseek pydantic python-dotenv
```

在项目目录创建 .env 文件：

```text
DEEPSEEK_API_KEY=your_deepseek_api_key
```

然后初始化模型：


## 实例

以下示例默认已经完成上述初始化，除非示例中重新创建模型。

需要注意，工具调用和结构化输出功能是否可用，以及具体支持的参数，取决于所使用的模型、API 和 LangChain 集成版本。


## 二、bind_tools()：为模型绑定工具

bind_tools() 用于向聊天模型提供工具定义，让模型知道当前有哪些工具可以使用，以及工具需要哪些参数。

例如，一个天气查询工具可以接收城市名称：

```text
get_weather(city="杭州")
```

当用户询问天气时，模型可以生成一个工具调用请求，指定工具名称和参数。

注意：bind_tools() 不负责真正执行 Python 函数。

它只是向模型提供工具定义，并允许模型在响应中返回 tool_calls。


### bind_tools() 基本语法

```text
model_with_tools = model.bind_tools(tools)
```

其中，tools 是工具定义列表。

LangChain 支持多种工具定义方式，包括：

- 使用 @tool 装饰器定义的 LangChain 工具。
- 普通 Python 函数（由集成转换其定义）。
- Pydantic 模型类。
- 符合要求的 OpenAI Tool Calling 格式字典。


### 实例 1：使用字典定义工具

下面通过 OpenAI Function Calling 风格的字典描述一个天气查询工具。


## 实例

如果模型选择调用工具，可能输出类似：

```text
工具名称： get_weather
工具参数： {'city': '杭州'}
调用 ID： call_xxxxx
```

其中，调用 ID 由模型服务生成，不同请求的值通常不同。

还需要注意，即使已经绑定工具，模型也不保证每次都会调用工具。是否调用由模型和相关配置共同决定。


### tool_calls 返回结构

LangChain 会将模型返回的工具调用请求标准化到 AIMessage.tool_calls 中。

典型结构如下：

```text
[
    {
        "name": "get_weather",
        "args": {
            "city": "杭州"
        },
        "id": "call_xxxxx",
        "type": "tool_call"
    }
]
```

如果模型返回了格式不正确的工具调用，还可能出现 invalid_tool_calls。因此，在实际开发中不能假设每一次工具调用都有效。


## 三、使用 @tool 定义工具

如果工具需要真正执行 Python 代码，通常推荐使用 @tool 装饰器定义工具。

例如：


## 实例

使用 @tool 时，LangChain 会利用函数名称、参数类型与文档字符串构建工具定义。

在这个示例中：

- 工具名称为 get_weather。
- 工具需要一个字符串参数 city。
- 文档字符串向模型解释工具用途。

模型可以根据这些信息生成工具调用请求。

但是，此时天气查询函数仍然没有被自动执行。


## 四、手动执行工具：完整 Tool Calling 流程

仅使用 bind_tools()，模型会告诉程序需要调用哪个工具，但不会自动执行。

如果不使用 Agent，就需要自己编写工具调度代码。

基本流程如下：

```text
用户提问
   ↓
模型生成工具调用请求
   ↓
程序检查 tool_calls
   ↓
调用对应 Python 工具
   ↓
将结果封装为 ToolMessage
   ↓
再次调用模型
   ↓
生成最终回答
```


### 完整实例

下面展示如何手动完成一次工具调用闭环。


## 实例

如果第一次模型调用产生了 get_weather 工具调用，程序会执行对应的 Python 函数。

工具返回模拟天气后，通过 ToolMessage 将结果传回模型。

模型就可以利用这个结果组织最终回答。

例如：

```text
杭州的模拟天气为晴天，气温25°C。
```

注意：这个例子演示一次工具执行与一次后续模型调用。如果第二次模型响应仍然包含工具调用请求，还需要继续循环处理。

如果需要完整的多轮工具调用、状态管理和执行控制，建议使用上一节介绍的 create_agent()，而不是自己实现复杂的调度逻辑。

另外，工具参数由模型生成，执行数据库修改、文件操作或网络请求等敏感工具前，还应进行参数校验和权限检查。


## 五、使用 Pydantic 模型描述工具参数

对于参数较多的工具，可以使用 Pydantic 定义参数结构。

Pydantic 可以提供类型声明、字段描述和数据校验，减少手写 JSON Schema 的工作量。


### 实例


## 实例

如果模型选择调用两个工具，可能返回：

```text
工具： GetWeather
参数： {'city': '北京', 'unit': 'celsius'}

工具： Calculate
参数： {'expression': '123 * 456'}
```

这里有一个重要区别：工具名称默认来自 Pydantic 类名。

因此：

- GetWeather 对应工具名称 GetWeather。
- Calculate 对应工具名称 Calculate。

如果希望工具名称为 get_weather 或 calculate，可以改用对应名称的 @tool 函数。

注意：这里的 Pydantic 类用于描述工具输入结构，不包含天气查询或数学计算的具体执行逻辑。模型返回工具调用请求后，仍需要应用程序提供对应的工具实现。

Pydantic 类的字段描述可以帮助模型生成符合要求的参数，但模型生成的参数并不一定始终有效。实际执行前仍需要进行校验。


## 六、with_structured_output()：结构化输出

with_structured_output() 用于将聊天模型的输出转换为指定的数据结构。

例如，普通模型可能返回以下文字：

```text
张三今年28岁，是一名全栈工程师，
掌握 Python、React 和 Docker。
```

如果程序需要提取姓名、年龄、职业和技能，就可以通过结构化输出得到：

```text
{
    "name": "张三",
    "age": 28,
    "occupation": "全栈工程师",
    "skills": ["Python", "React", "Docker"]
}
```

这样就不必自己从自然语言中解析字段。


### 基本语法

```text
structured_model = model.with_structured_output(
    schema
)

result = structured_model.invoke(text)
```

其中，schema 用于定义期望的输出结构。

常用的结构定义方式包括：

- Pydantic 模型。
- JSON Schema 字典。
- TypedDict 类型。

注意：with_structured_output() 并不保证底层一定使用独立的原生结构化输出 API。部分模型集成会使用 Tool Calling 或 JSON Mode 实现。


### 实例：通过 Pydantic 提取人物信息


## 实例

如果模型正确提取信息，输出可能为：

```html
姓名： 张三
年龄： 28
职业： 全栈工程师
技能： ['Python', 'React', 'Docker']

返回类型： <class '__main__.PersonInfo'>
```

使用 Pydantic Schema 且解析成功时，返回值通常是对应的 Pydantic 模型实例。

因此，可以通过：

```text
result.name
result.age
result.skills
```

直接读取字段。

还可以转换为字典：

```text
data = result.model_dump()

print(data)
```

Pydantic 会检查返回字段是否满足相应类型和验证规则。

但需要注意，类型校验不等于事实校验。即使返回结构合法，也需要根据业务需求检查模型提取的信息是否准确。


## 七、bind_tools() 与 with_structured_output() 的区别

这两个方法都可以利用模型的结构化响应能力，但用途不同。

可以这样理解：

- bind_tools()：让模型告诉程序下一步需要执行什么操作。
- with_structured_output()：让模型按照程序需要的数据格式返回内容。

例如：

```text
用户：查询杭州天气

bind_tools()
    ↓
模型请求调用 get_weather
    ↓
程序执行工具
    ↓
获得天气数据
```

而结构化输出更像：

```text
输入：张三今年28岁，职业是程序员

with_structured_output()
    ↓
{
    "name": "张三",
    "age": 28,
    "occupation": "程序员"
}
```

这两种能力可以在更复杂的 Agent 工作流中组合使用，但不能简单理解为完全相同的操作。


## 八、嵌套结构化输出

with_structured_output() 不仅可以提取简单字段，还可以描述嵌套对象和列表。

例如，可以从一段菜谱文字中提取：

- 菜名。
- 制作难度。
- 食材名称与用量。
- 烹饪步骤和预计时间。


### 实例：提取菜谱信息


## 实例

如果解析成功，可以得到类似结果：

```text
菜名： 番茄炒蛋
难度： 简单

食材：
番茄 2个
鸡蛋 3个
葱花 少许
盐 适量
糖 少许

步骤：
1 番茄切块，鸡蛋打散 5
2 将鸡蛋炒熟盛出 3
3 炒番茄至出汁，加盐和糖 5
4 加入鸡蛋翻炒，撒上葱花 2
```

这里的 Recipe 包含两个嵌套对象列表：

```text
ingredients: list[Ingredient]

steps: list[CookingStep]
```

模型可以根据 Schema 构建层级化的数据结构。

不过，嵌套结构越复杂，越需要关注模型的结构化输出能力、字段完整性和解析失败情况。


## 九、JSON Schema 结构化输出

如果不希望使用 Pydantic 类，也可以直接通过 JSON Schema 字典描述输出结构。

这对于需要与其他语言、前端应用或外部接口共享数据格式的项目非常有用。


## 后续章节

- 实例：情感分析
- 实例
- 十、include_raw：同时保留原始响应
- 实例
- 实例
- 十一、结构化输出的实现方式
- DeepSeek 的 JSON 输出能力
- 十二、结构化输出失败时如何处理？
- 实例：捕获结构化输出错误
- 实例
- 十三、ConfigurableModel 中使用 bind_tools()
- 实例：动态切换 DeepSeek Flash 和 Pro
- 实例
- 十四、ConfigurableModel 中使用结构化输出
- 实例
- 实例

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `LangChain Chat Model 高级用法` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
