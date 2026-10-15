# FastAPI：Pydantic Schema — 数据验证与序列化

- 来源：[Pydantic Schema](https://www.runoob.com/fastapi/fastapi-blog-pydantic-schema.html)
- 分类：Python / 数据科学
- 技术：FastAPI
- 笔记类型：练习笔记
- 章节序号：3867

## 本章内容

本章你将学会 Pydantic Schema，理解它与 ORM 模型的职责分离，这是 FastAPI 最核心的特性。


## 为什么需要 Schema？

ORM 模型（models.py）定义数据库结构，但不能直接用于 API 的请求/响应校验。

原因：ORM 模型包含数据库专用逻辑（如 relationship），且不希望将所有字段暴露给 API。

Pydantic Schema 是纯数据类，专门负责 API 的输入输出校验和序列化。

这三者的关系：

```text
客户端 → [Pydantic Schema 校验] → 路由函数 → [ORM 模型] → 数据库
客户端 ← [Pydantic Schema 序列化] ← 路由函数 ← [ORM 模型] ← 数据库
```


## Pydantic Schema 基础

Pydantic V2 是 FastAPI 的数据引擎，通过类型提示定义数据结构。


## 实例


## 定义博客的 Schema


## 实例

Pydantic V2 中，model_config = ConfigDict(from_attributes=True) 替代了 V1 中的 class Config: orm_mode = True。这个配置允许你直接从 SQLAlchemy ORM 对象构建 Pydantic Schema：PostResponse.model_validate(post_orm_obj)。


## 在路由中使用 Schema


## 实例

response_model 是 FastAPI 最强的特性之一。声明后，FastAPI 会：1. 自动过滤 ORM 对象中不在 Schema 中声明的字段；2. 自动将 datetime 等类型转为 JSON 字符串；3. 生成精确的 OpenAPI 文档。


## ORM 模型 vs Pydantic Schema 对照


## 本章小结

本章你掌握了 FastAPI 最核心的 Pydantic Schema：BaseModel 定义请求/响应 Schema、from_attributes=True 开启 ORM 模式、response_model 自动序列化 ORM 对象、Schema 与 ORM 模型的职责分离原则。

这就是 FastAPI 类型驱动架构的精髓——先定义数据形状，路由和文档自动生成。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Pydantic Schema` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
