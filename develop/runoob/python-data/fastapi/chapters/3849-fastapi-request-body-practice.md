# FastAPI：FastAPI 请求体

- 来源：[FastAPI 请求体](https://www.runoob.com/fastapi/fastapi-request-body.html)
- 分类：Python / 数据科学
- 技术：FastAPI
- 笔记类型：练习笔记
- 章节序号：3849

## 本章内容

请求体是客户端发送给 API 的数据。当你需要从客户端接收 JSON 数据时，使用请求体来传递。FastAPI 使用 Pydantic 模型来声明请求体的结构，自动完成数据校验、转换和文档生成。


## 请求体与查询参数的区别

发送数据应使用 POST（最常见）、PUT、DELETE 或 PATCH。虽然 FastAPI 技术上支持 GET 请求携带请求体，但这不符合 HTTP 规范，Swagger UI 也不会为 GET 请求显示请求体文档。


## 使用 Pydantic 模型声明请求体


### 1. 导入 BaseModel

```text
from pydantic import BaseModel
```


### 2. 创建数据模型

定义一个继承 BaseModel 的类，使用 Python 标准类型声明所有属性：


## 实例

属性是否必填的规则与查询参数相同：

- 有默认值的属性是可选的（如 description、tax）
- 没有默认值的属性是必填的（如 name、price）

以下 JSON 都是有效的请求体：

```text
// 包含所有字段
{
    "name": "Foo",
    "description": "可选描述",
    "price": 45.2,
    "tax": 3.5
}

// 省略可选字段
{
    "name": "Foo",
    "price": 45.2
}
```


## FastAPI 对请求体的处理

仅通过 Python 类型声明，FastAPI 就能自动完成以下工作：


## 使用模型属性

在路径操作函数内部，你可以像操作普通 Python 对象一样访问模型的所有属性：


## 实例

Pydantic v2 使用 model_dump() 替代了 v1 的 dict() 方法来序列化模型数据。model_dump() 返回一个包含模型所有字段的字典。


## 请求体 + 路径参数

可以同时声明路径参数和请求体，FastAPI 会自动从正确的位置获取数据：


## 实例

FastAPI 识别规则：

- item_id 在路径 {item_id} 中出现 -> 路径参数
- item 的类型是 Pydantic 模型 -> 请求体


## 请求体 + 路径参数 + 查询参数

三者可以同时使用：


## 实例

FastAPI 的完整参数识别规则：


## 小结

请求体的核心要点：

- 使用 Pydantic 的 BaseModel 定义请求体结构
- 有默认值的字段可选，没有默认值的字段必填
- 请求体可以与路径参数和查询参数同时使用
- FastAPI 自动完成数据校验、类型转换和文档生成
- Pydantic v2 使用 model_dump() 进行序列化


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `FastAPI 请求体` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
