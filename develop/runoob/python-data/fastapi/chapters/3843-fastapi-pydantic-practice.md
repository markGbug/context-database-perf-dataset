# FastAPI：FastAPI Pydantic 模型

- 来源：[FastAPI Pydantic 模型](https://www.runoob.com/fastapi/fastapi-pydantic.html)
- 分类：Python / 数据科学
- 技术：FastAPI
- 笔记类型：练习笔记
- 章节序号：3843

## 本章内容

Pydantic 是 FastAPI 的核心依赖，用于数据校验和序列化。它让你使用标准的 Python 类型注解来定义数据模型，自动完成数据校验、类型转换和文档生成。


## Pydantic 是什么

Pydantic 是一个 Python 数据校验库，它的核心思想是：用 Python 类型注解定义数据结构，Pydantic 自动负责校验和转换。在 FastAPI 中，Pydantic 主要用于：


## 定义 Pydantic 模型

创建一个继承 BaseModel 的类，使用 Python 标准类型声明字段：


## 实例

字段是否必填取决于是否有默认值：


## 使用 Pydantic 模型


### 作为请求体

最常见的用法是将模型声明为路径操作函数的参数：


## 实例


### 访问和操作模型数据


## 实例

Pydantic v2 使用 model_dump() 和 model_dump_json() 替代了 v1 的 dict() 和 json() 方法。新方法性能更好（底层使用 Rust 实现）。


## 模型校验示例

当客户端发送的数据不符合模型定义时，FastAPI 会返回详细的校验错误：


## 实例

如果发送了类型错误的数据：

```text
// price 应该是数字，但传了字符串
{
    "name": "Foo",
    "price": "not a number"
}

// FastAPI 返回的错误
{
    "detail": [
        {
            "type": "float_parsing",
            "loc": ["body", "price"],
            "msg": "Input should be a valid number, unable to parse string as a number",
            "input": "not a number"
        }
    ]
}
```


## Pydantic v2 常用方法


## 模型配置（model_config）

Pydantic v2 使用 model_config 替代了 v1 的 Config 内部类：


## 实例

Pydantic v2 中，orm_mode = True 已改为 from_attributes = True，schema_extra 已改为 json_schema_extra，allow_population_by_field_name 已改为 populate_by_name。


## 模型继承

Pydantic 模型支持继承，可以方便地创建输入模型和输出模型：


## 实例

使用不同的输入和输出模型是保护敏感数据的重要手段。永远不要在 API 响应中返回密码等敏感字段。


## 小结

Pydantic 模型的核心要点：

- 使用 BaseModel 定义数据模型，标准 Python 类型声明字段
- 有默认值的字段可选，没有默认值的字段必填
- v2 使用 model_dump()、model_validate() 等新方法
- 通过模型继承创建不同的输入/输出模型，保护敏感数据
- 所有校验和文档都是自动的，只需声明一次类型


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `FastAPI Pydantic 模型` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
