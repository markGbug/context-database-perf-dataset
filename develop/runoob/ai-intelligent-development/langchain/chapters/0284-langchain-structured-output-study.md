# LangChain：LangChain 结构化输出 Structured Output

- 来源：[LangChain 结构化输出](https://www.runoob.com/langchain/langchain-structured-output.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：学习笔记
- 章节序号：0284

## 本章内容

大多数时候，我们需要的并不是一段自由文本，而是程序能够直接处理的数据，例如 JSON 对象、用户信息、商品数据或课程推荐结果。

LangChain 提供 Structured Output（结构化输出） 功能，可以让模型按照指定的数据结构返回结果，减少手动解析文本的工作。

在 LangChain 1.x 中，可以通过 create_agent(response_format=...) 配置 Agent 的结构化输出，也可以直接使用模型的 with_structured_output() 方法。

本章节介绍 Pydantic、TypedDict、ProviderStrategy、ToolStrategy、嵌套结构以及错误处理。


## 一、为什么需要结构化输出？

假设用户提供了一段描述：

```text
张三今年 28 岁，是一名 Python 工程师。
```

普通模型可能返回：

```text
张三今年 28 岁，职业是 Python 工程师。
```

如果需要将这些信息写入数据库，还需要从自然语言中提取姓名、年龄和职业。

而结构化输出可以直接返回：

```text
{
    "name": "张三",
    "age": 28,
    "job": "Python 工程师"
}
```

结构化输出的优势在于：

- 明确字段名称和数据类型。
- 减少对正则表达式和文本解析的依赖。
- 支持字段范围、枚举及其他约束。
- 便于与数据库、API 和前端组件集成。

注意：结构化输出可以检查数据格式，但不能保证数据内容一定真实。例如，模型可以生成符合 Schema 的错误日期或不存在的课程名称。


## 二、安装与环境准备

安装 LangChain 及 DeepSeek 集成：

```text
pip install -U langchain langchain-deepseek python-dotenv pydantic
```

项目目录创建 .env 文件：

```text
DEEPSEEK_API_KEY=your_deepseek_api_key
```

使用以下代码加载环境变量：

```text
from dotenv import load_dotenv
load_dotenv()
```

本教程使用 deepseek:deepseek-flash 作为示例模型。不同模型对原生结构化输出、Tool Calling 和 JSON Schema 的支持可能不同，需要以实际集成能力为准。


## 三、最简单的用法：Pydantic 模型

使用 Pydantic 定义需要的输出结构，然后通过 response_format 传给 create_agent()。

例如，从一段用户描述中提取课程名称、难度、学习时长和是否免费。


### 实例：提取课程信息


## 实例

如果模型成功提取，输出类似：

```text
课程名： Python3 基础教程
难度： 入门
时长： 20 小时
免费： True
对象类型： CourseInfo
```

其中：

- BaseModel：定义数据结构。
- Field：配置字段说明及约束。
- Literal：限制允许的字段值。
- response_format：指定 Agent 输出结构。
- structured_response：获取最终结构化结果。

使用 Pydantic Schema 且解析成功后，structured_response 是 Pydantic 模型实例，可以通过属性直接访问。


### 转换为 JSON

如果需要发送给前端，可以使用：

```text
print(course.model_dump())
print(course.model_dump_json(indent=2))
```

model_dump() 返回 Python 字典，model_dump_json() 返回 JSON 字符串。

注意：如果原文没有提供某个字段，不应该让模型随意猜测。可以使用可选字段或要求补充信息。


## 四、ProviderStrategy 与 ToolStrategy

LangChain 1.x 提供两种主要的 Agent 结构化输出策略：


### 1、自动选择策略

最简单的写法：

```text
agent = create_agent(
    model="deepseek:deepseek-flash",
    response_format=CourseInfo
)
```

LangChain 会根据当前模型的能力信息，选择支持的结构化输出方式。

如果模型支持原生结构化输出，可能使用 ProviderStrategy；否则可采用 ToolStrategy。

自动选择依赖模型能力信息，并不保证所有模型都能完成结构化输出。


### 2、显式使用 ToolStrategy

对于使用 Tool Calling 完成结构化输出的模型，可以显式配置：


## 实例

ToolStrategy 会通过模型的工具调用机制传递结构化数据，再由 LangChain 进行解析和校验。

这里的结构化输出工具主要用于传递数据 Schema，不等于执行了一个真实的课程查询 Python 函数。


### 3、显式使用 ProviderStrategy

如果模型及服务商明确支持原生结构化输出，可以使用：

```text
from langchain.agents.structured_output import ProviderStrategy

agent = create_agent(
    model=model,
    response_format=ProviderStrategy(CourseInfo)
)
```

这种方式要求实际使用的模型及提供商支持相应结构化输出能力。

注意：不要仅因为模型支持 JSON 文本输出，就认定它完全支持原生 JSON Schema 约束。具体能力应参考对应模型集成文档。


## 五、与工具共存的 Structured Output

结构化输出和普通工具可以组合使用。

例如，课程推荐 Agent 可以先搜索课程，再将最终结果整理成指定的结构。

需要注意，模型必须支持当前结构化输出策略及普通工具调用的组合。


### 实例：搜索课程并生成推荐


## 实例

如果模型正确调用查询工具，可能得到：

```text
课程： Python3 基础教程
理由： 适合没有编程基础的学习者
难度： 入门
```

工具消息中可能包含课程搜索结果。

但需要注意，result["messages"] 中可能还有结构化输出策略产生的 ToolMessage，因此不应将每条 ToolMessage 都当作实际业务数据库查询。

注意：模型不一定严格按照预期调用普通工具。如果必须查询真实数据库并保证数据来源，应在业务工作流中强制执行查询。


## 六、复杂嵌套结构

Pydantic 支持列表、嵌套模型、枚举和字段限制，适合用于学习计划、订单信息等复杂数据结构。


### 实例：生成 Python 学习计划


## 实例

成功执行后，可能得到：

```text
目标：掌握 Python 基础语法
难度：入门
总时长：6.0 小时

1. Python 环境与变量（60分钟）
2. 数据类型（60分钟）
3. 条件判断（60分钟）
4. 循环（60分钟）
5. 函数（60分钟）
6. 综合练习（60分钟）
```

这里不仅验证 total_hours 不超过 10 小时，还通过 model_validator 校验总时长与各主题分钟数是否一致。

如果模型返回不符合约束的数据，Pydantic 会产生验证错误。使用 ToolStrategy 时，LangChain 可以根据错误处理策略要求模型重新生成。

但不能保证模型一定能够在有限次数内生成有效结果。


## 七、使用 TypedDict 返回字典

除了 Pydantic，LangChain 也支持使用 TypedDict 定义结构化输出。

与 Pydantic 模型不同，TypedDict 方案通常返回普通 Python 字典。


### 实例：提取人员信息


## 实例

可能输出：

```text
张三
28
Python工程师
dict
```

两种方式的区别：

如果涉及复杂业务校验，通常优先选择 Pydantic。


## 八、可选字段与缺失数据

实际文本中经常存在信息不完整的情况。

例如：

```text
我正在学习 Python 基础教程，属于入门级别。
```

用户没有提供预计学习时长，也没有说明是否收费。

此时不应该让模型自行编造这两个字段。

可以将字段定义为可选：


## 实例

未提供的数据可以使用 None 表示。

例如：

```text
{
    "course_name": "Python 基础教程",
    "difficulty": "入门",
    "estimated_hours": null,
    "is_free": null
}
```

注意：声明可选字段只是允许缺失值，并不能彻底防止模型猜测。因此仍需在 System Prompt 中说明只提取明确提供的信息。


## 九、直接使用 with_structured_output()

如果任务只是从文本中提取信息，不需要 Agent 调用工具，可以直接使用聊天模型的 with_structured_output()。

这通常比创建 Agent 更简单。


### 实例：情感分析


## 后续章节

- 实例
- 与 Agent 的区别
- 十、include_raw：查看原始模型响应
- 实例
- 实例
- 十一、结构化输出的错误处理
- 实例：自定义错误提示
- 实例
- 十二、完整实例：从用户描述中提取课程信息
- 完整实例
- 十三、常见问题
- 1、structured_response 是字符串还是对象？
- 2、为什么 structured_response 不存在？
- 3、Pydantic 和 TypedDict 应该选哪个？
- 4、ProviderStrategy 和 ToolStrategy 有什么区别？
- 5、所有模型都支持结构化输出吗？

## 复习重点

- 能说明 `LangChain 结构化输出` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
