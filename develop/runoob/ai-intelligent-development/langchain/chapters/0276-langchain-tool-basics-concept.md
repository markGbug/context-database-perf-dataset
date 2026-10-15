# LangChain：LangChain @tool 装饰器——定义工具

- 来源：[LangChain @tool](https://www.runoob.com/langchain/langchain-tool-basics.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：概念卡
- 章节序号：0276

## 本章内容

工具（Tool）是 LangChain Agent 与外部系统交互的重要桥梁。

通过工具，Agent 可以查询数据库、调用 API、执行计算、读取文件，或者完成其他由程序提供的操作。

LangChain 提供 @tool 装饰器，可以将 Python 函数快速转换为 Agent 能够识别和调用的工具。

本章节将介绍 @tool 的基本用法、参数定义、Pydantic 校验、工具注册，以及多个工具协作的方法。


## 一、@tool 基本语法

@tool 是 LangChain 提供的工具定义装饰器。

只需要在普通 Python 函数前添加 @tool，LangChain 就可以根据函数名称、参数类型和描述信息创建工具。

基本语法：

```text
from langchain.tools import tool

@tool
def tool_name(parameter: str) -> str:
    """工具的功能描述。"""
    return "工具执行结果"
```

使用 @tool 后，函数会被包装为 LangChain 的工具对象。

它不再只是原来的普通 Python 函数，而是具有名称、描述、参数 Schema 和执行接口的对象。


### 实例：第一个工具


## 实例

执行结果中的主要内容：

```text
你好，小明！欢迎来到菜鸟教程 RUNOOB。

工具名称： hello_tool
```

还可以通过 description 和 args 查看工具的描述与参数结构。

注意：普通工具输入通常使用 invoke()：

```text
hello_tool.invoke({"name": "小明"})
```

不要把经过装饰的工具对象直接当作原始 Python 函数调用。


### @tool 转换后有什么变化？

LangChain 工具通常具有以下属性和方法：

其中，工具名称、描述和参数结构会帮助模型理解工具的用途。

执行接口则负责真正运行对应的 Python 代码。


## 二、工具描述与文档字符串

工具的文档字符串（docstring）非常重要。

模型需要通过工具描述判断：

- 工具能够完成什么任务。
- 什么情况下适合调用它。
- 工具需要哪些参数。
- 参数分别代表什么。

例如：

```text
@tool
def get_weather(city: str) -> str:
    """查询指定城市的天气信息。"""
    ...
```

这个描述虽然简短，但已经明确了工具的基本用途。

如果工具比较复杂，还可以使用 Google 风格文档字符串描述参数。


### 使用 parse_docstring

默认情况下，@tool 不会自动将 Google 风格文档字符串中的 Args 内容解析为单独的参数描述。

如果需要解析，可以设置：

```text
@tool(parse_docstring=True)
```


### 实例


## 实例

这里通过 parse_docstring=True，让 LangChain 尝试从文档字符串中提取参数描述。

注意：开启该选项后，文档字符串应符合支持的 Google 风格格式。如果格式不正确，可能抛出 ValueError。

对于简单工具，使用清晰的函数描述和类型注解通常已经足够；对于参数较多的工具，推荐结合 parse_docstring 或 Pydantic 的 Field 提供描述信息。


## 三、使用不同的参数类型

@tool 支持根据 Python 类型注解生成参数 Schema。

常见类型包括：

- str：字符串。
- int：整数。
- float：浮点数。
- bool：布尔值。
- Literal：限定允许的参数值。
- list：列表。


### 实例：模拟课程搜索

下面定义一个课程搜索工具，支持关键词、难度、最大结果数和是否只显示免费课程。

为避免与真实网站数据混淆，以下课程列表均为教学模拟数据。


## 实例

执行结果：

```text
搜索结果：Python 基础、Python 入门练习
搜索结果：Python 高级实战
```

其中：

- keyword 和 level 没有默认值，属于必填参数。
- max_results 默认值为 5。
- free_only 默认值为 True。
- Literal 用于限制课程难度的允许值。

上面的搜索只在 Python 列表中执行，不会连接真实网站或数据库。


## 四、注册工具到 Agent

工具定义完成后，可以通过 create_agent() 的 tools 参数将其注册到 Agent。

例如，一个学习顾问 Agent 可以拥有两个工具：

- search_courses：搜索课程。
- get_course_detail：查询课程详情。


### 实例：创建课程推荐 Agent


## 实例

运行时，Agent 可以根据问题选择合适的工具。

例如，查询课程列表时，模型可能调用：

```text
search_courses(keyword="python")
```

查询课程详情时，可能调用：

```text
get_course_detail(
    course_name="Python3 基础教程"
)
```

工具返回结果后，Agent 会再次调用模型生成回答。

注意：工具选择并不是固定的。模型可能调用一个工具、多个工具，也可能直接回答。

如果某个工具必须执行，应该通过程序流程或工作流明确控制，而不是只依靠提示词。


## 五、多个工具协作

Agent 可以组合不同工具完成任务。

例如，用户希望知道某只股票的模拟价格，并将金额转换成人民币。

这个过程可能涉及：

- 调用股票价格查询工具。
- 获取股票价格。
- 调用货币换算工具。
- 生成最终回答。

下面仍然使用模拟数据，演示多个工具如何协作。


### 实例：模拟股票价格与货币换算


## 实例

如果 Agent 依次调用两个工具，可能得到：

```text
[工具 get_stock_price] AAPL 的模拟价格为 185.50 USD
[工具 convert_currency] 185.50 USD = 1344.88 CNY（模拟汇率 7.25）
```

这里的价格与汇率都是固定的教学数据，不代表真实市场行情。

注意：模型可能先获取价格，再根据返回值调用换算工具，也可能采用其他路径。不要将示例中的工具调用次数和顺序视为固定结果。


## 六、工具的可选参数与默认值

Python 函数可以为参数设置默认值，LangChain 工具同样支持。

没有默认值的参数通常是必填参数；有默认值的参数通常可以省略。


### 实例


## 实例

可能输出：

```text
Python（入门）推荐：Python 基础、Python 面向对象、Python 数据分析
Java（进阶）推荐：Java 基础、Java 面向对象
```

这里的 level 只用于标记请求的学习级别，并没有真正筛选课程难度。

在实际项目中，如果需要精确按照课程难度推荐，还应在数据中定义对应的难度字段并执行筛选。

默认参数能减少工具调用时需要传入的字段，但不应该为用户身份、权限、支付金额等关键参数随意设置默认值。


## 七、args_schema：使用 Pydantic 校验参数

对于参数较多、需要严格验证输入的工具，可以通过 args_schema 指定 Pydantic 模型。

例如，可以限制：

- 字符串最短和最长长度。
- 整数允许的范围。
- 参数必须属于某几个指定值。
- 字段是否必须提供。


### 实例：自定义搜索参数


## 实例

正常调用返回：

```text
搜索关键词：Python；分类：backend；页码：1
```

第二次调用中，category="invalid" 不在允许的值列表中，会触发参数校验错误。

这样可以在工具函数执行前，拦截部分不符合要求的输入。

注意：即使使用 Pydantic 校验，也不能代替业务权限检查、SQL 参数化查询、文件路径限制等安全措施。


### 查看 JSON Schema

可以通过工具的参数 Schema 了解它接收哪些参数。

```text
print(search_course.args)
```

如果使用 Pydantic 模型，也可以直接获取其 JSON Schema：

```text
print(
    CourseSearchInput.model_json_schema()
)
```

这对于工具调试、前端参数表单生成和 API 文档编写很有帮助。


## 后续章节

- 八、@tool 的其他常用参数
- 指定自定义名称和描述
- 实例
- return_direct 参数
- 九、工具返回内容与 artifact
- 实例
- 实例
- 十、同步工具与异步工具
- 实例：异步工具
- 实例
- 十一、工具调用中的错误处理
- 实例
- 实例
- 十二、工具定义方式对比
- 十三、完整实例：模拟课程查询助手
- 完整实例

## 记忆卡片

- 一句话定义：`LangChain @tool` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
