# FastAPI：FastAPI 请求体字段与嵌套模型

- 来源：[FastAPI 请求体字段与嵌套模型](https://www.runoob.com/fastapi/fastapi-body-fields.html)
- 分类：Python / 数据科学
- 技术：FastAPI
- 笔记类型：练习笔记
- 章节序号：3852

## 本章内容

在 Pydantic 模型内部，你可以使用 Field 为字段声明校验规则和元数据，也可以将模型嵌套使用来处理复杂的 JSON 数据结构。


## 使用 Field 声明字段校验

与路径操作函数中使用 Query、Path 声明校验的方式一样，Pydantic 模型内部使用 Field 声明字段校验：


## 实例

Field 支持的校验参数：

注意 Field 从 pydantic 导入，而不是从 fastapi 导入。这与 Query、Path 等从 fastapi 导入不同。


## 列表类型字段

你可以将字段声明为列表，并指定元素类型：


## 实例

请求体示例：

```text
{
    "name": "Foo",
    "price": 42.0,
    "tags": ["rock", "metal", "bar"]
}
```


### 使用 Set 去重

如果标签不应重复，使用 set 类型：


## 实例

即使请求中包含重复的标签，响应中也会自动去重。


## 嵌套模型

Pydantic 模型的字段类型可以是另一个 Pydantic 模型，支持任意深度的嵌套：


## 实例

对应的请求体结构：

```text
{
    "name": "Foo",
    "description": "The pretender",
    "price": 42.0,
    "tax": 3.2,
    "tags": ["rock", "metal", "bar"],
    "image": {
        "url": "http://example.com/baz.jpg",
        "name": "The Foo live"
    }
}
```


## 列表中的子模型

可以将子模型放在列表中：


## 实例

对应的请求体：

```text
{
    "name": "Foo",
    "price": 42.0,
    "images": [
        {"url": "http://example.com/baz.jpg", "name": "The Foo live"},
        {"url": "http://example.com/dave.jpg", "name": "The Baz"}
    ]
}
```


## 深度嵌套模型

你可以定义任意深度的嵌套结构：


## 实例


## 纯列表请求体

如果请求体的最外层就是一个 JSON 数组，可以直接在函数参数中声明列表类型：


## 实例


## 任意 dict 构成的请求体

当你需要接收键名不确定的字典数据时，可以声明 dict 类型的请求体：


## 实例

请求体示例：

```text
{
    "1": 0.5,
    "2": 1.5,
    "3": 2.0
}
```

JSON 只支持字符串类型的键，但 Pydantic 会自动将字符串键转换为声明的类型（如本例中的 int）。


## 小结

- 使用 Pydantic 的 Field 为模型字段添加校验和元数据
- list[str]、set[str] 等集合类型可以声明列表/集合字段
- 模型可以嵌套使用，支持任意深度的 JSON 结构
- HttpUrl 等特殊类型自动校验格式
- 纯列表和任意字典也可以作为请求体类型


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `FastAPI 请求体字段与嵌套模型` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
