# LangChain：LangChain Tools API 参考

- 来源：[LangChain Tools API](https://www.runoob.com/langchain/langchain-tools-api.html)
- 分类：AI / 智能开发
- 技术：LangChain
- 笔记类型：练习笔记
- 章节序号：0306

## 本章内容

在 LangChain 中，大语言模型主要负责理解问题和生成回答，而 Tools（工具） 则让模型具备执行具体操作的能力。

例如，Agent 可以通过工具查询数据库、搜索知识库、计算数学表达式，或者调用外部 API。

LangChain 1.x 提供了统一的 Tools API，最常用的是 @tool 装饰器和 BaseTool 工具抽象。

本章节系统整理 @tool 的参数、BaseTool 属性与方法、Pydantic 参数校验、ToolRuntime 依赖注入、工具返回值、异常处理以及 Agent 工具调用流程。


## 一、什么是 LangChain Tool？

Tool 是提供给模型调用的函数或操作接口。

一个 Tool 通常包含：

- name：工具名称，帮助模型识别功能。
- description：工具描述，告诉模型何时使用。
- args_schema：工具参数结构。
- 执行逻辑：真正执行查询、计算或其他操作的 Python 代码。

例如：

```text
用户：帮我计算 25 + 17
         ↓
      Agent
         ↓
   选择 add_numbers
         ↓
      执行工具
         ↓
      返回 42
         ↓
   模型生成回答
```

工具调用有两个重要步骤：

- 模型生成 ToolCall，提出调用哪个工具以及传入什么参数。
- Agent 或应用程序执行工具，并通过 ToolMessage 返回结果。

注意：单纯使用 model.bind_tools() 并不会自动执行 Python 函数。如果希望自动执行工具循环，通常使用 create_agent()。


## 二、@tool 装饰器

@tool 是创建 LangChain Tool 最简单的方法。

它可以将普通 Python 函数转换为 BaseTool 对象，并根据函数签名推断工具输入参数。


### 基本语法

```text
from langchain.tools import tool

@tool
def tool_name(param: str) -> str:
    """描述工具的用途。"""
    return f"结果：{param}"
```

函数的文档字符串非常重要，因为模型会根据工具名称、描述和参数 Schema 判断什么时候应该调用工具。


### 实例：创建第一个工具


## 实例

运行结果：

```text
greet
根据用户姓名生成一句问候语。
你好，小明！
```

这里的 greet 已经不再只是普通 Python 函数，而是一个具有名称、描述、参数 Schema 和调用接口的 LangChain Tool。


## 三、@tool 完整参数

当前 LangChain 的 @tool 装饰器支持以下主要参数：

常用形式包括：

```text
@tool

@tool("custom_name")

@tool(description="自定义工具描述")

@tool(args_schema=MyInput)

@tool(return_direct=True)
```

注意：自定义工具名称通常使用 @tool("custom_name")，而不是假定当前 @tool 装饰器具有独立的 name 关键字参数。


## 四、自定义工具名称

默认情况下，工具名称就是 Python 函数名称。

如果希望修改名称，可以给 @tool 传入字符串。


### 实例


## 实例

输出：

```text
search_python_docs
找到关于 装饰器 的参考资料
```

建议使用清晰的 snake_case 名称，例如：

```text
search_knowledge
get_weather
query_order
calculate_sum
send_email
```

避免使用包含空格、特殊符号或含义不明确的工具名称。


## 五、自定义工具描述

工具描述会影响模型的工具选择。

例如，如果只是写：

```text
"""查询数据"""
```

模型可能不知道应该在什么情况下使用它。

更好的描述应该说明用途、适用范围和返回内容。


### 实例：自定义 description


## 实例

description 显式指定时，优先使用这个描述，而不是函数文档字符串。

建议：工具描述应包含"工具能做什么"和"什么时候调用"，但不要把工具描述写成冗长的系统提示词。


## 六、infer_schema：自动生成参数 Schema

默认情况下：

```text
infer_schema=True
```

LangChain 会根据 Python 函数的类型注解和签名生成参数 Schema。


### 实例


## 实例

可能得到：

```text
{
    "a": {"title": "A", "type": "integer"},
    "b": {"title": "B", "type": "integer"}
}

35
```

参数结构由函数定义自动生成。

建议给工具函数添加明确的类型注解，否则模型可能难以准确理解参数要求。


## 七、args_schema：Pydantic 参数校验

当工具参数较复杂时，可以使用 Pydantic 定义输入结构。

例如，一个课程查询工具需要：

- 课程关键词不能为空。
- 查询数量为 1～20。
- 课程类别只能选择 Python、Java 或 JavaScript。

可以使用 BaseModel、Field 和 Literal 实现。


### 实例：参数校验


## 实例

运行结果：

```text
搜索 Python / 入门，最多 10 条
```

如果传入：

```text
{
    "keyword": "",
    "category": "PHP",
    "limit": 100
}
```

则可能触发 Pydantic 参数验证错误，因为这些值不符合 Schema。

注意：Pydantic 可以校验参数类型和取值范围，但不能代替用户权限检查或实际业务规则校验。


## 八、parse_docstring：解析参数说明

工具函数可以使用 Google 风格的 docstring 描述参数。

开启：

```text
parse_docstring=True
```

后，LangChain 会尝试将 Args 中的说明提取到工具 Schema。


### 实例


## 实例

需要注意，docstring 的格式必须符合解析要求。

如果格式不正确，并且：

```text
error_on_invalid_docstring=True
```

则可能在创建工具时抛出 ValueError。

对于输入较复杂的工具，推荐优先使用 Pydantic args_schema。


## 九、return_direct：直接返回工具结果

正常情况下，Agent 调用工具后，会把工具结果返回给模型，再由模型生成最终回复。

```text
模型请求工具
    ↓
执行工具
    ↓
工具返回结果
    ↓
再次调用模型
    ↓
最终回答
```

如果设置：

```text
return_direct=True
```

工具执行后，Agent 可以直接结束当前工具循环，不再进行下一次普通模型回复。


### 实例：直接返回


## 实例

如果模型调用了这个工具，Agent 可以在工具返回后结束执行。

注意：return_direct=True 并不代表 agent.invoke() 的返回值直接变成字符串。

create_agent() 通常仍然返回 Agent State，工具结果可以从其中的 messages 读取。

此外，对于并行工具调用和复杂 Middleware，最终执行行为还需要结合实际 Agent 配置判断。


## 后续章节

- 十、response_format：工具返回值格式
- 实例：content_and_artifact
- 实例
- 十一、BaseTool 主要属性
- 实例：查看工具属性
- 实例
- 十二、BaseTool 常用方法
- 实例：invoke()
- 实例
- 实例：ainvoke()
- 实例
- 十三、ToolRuntime：统一运行时依赖注入
- ToolRuntime 主要属性
- 十四、ToolRuntime.state：读取对话状态
- 实例：读取当前消息数量
- 实例

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `LangChain Tools API` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
