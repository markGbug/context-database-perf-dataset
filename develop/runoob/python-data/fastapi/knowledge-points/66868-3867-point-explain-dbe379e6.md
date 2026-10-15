# 知识点 66868：FastAPI：Pydantic Schema - 实例

- 来源：[Pydantic Schema](https://www.runoob.com/fastapi/fastapi-blog-pydantic-schema.html)
- 来源章节：[3867-fastapi-blog-pydantic-schema-study.md](../chapters/3867-fastapi-blog-pydantic-schema-study.md)
- 分类：Python / 数据科学
- 技术：FastAPI
- 所在小节：实例
- 知识类型：解释
- 原章节序号：3867

## 原文片段

Pydantic V2 中，model_config = ConfigDict(from_attributes=True) 替代了 V1 中的 class Config: orm_mode = True。这个配置允许你直接从 SQLAlchemy ORM 对象构建 Pydantic Schema：PostResponse.model_validate(post_orm_obj)。

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `实例` 这一小节和 `Pydantic Schema` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
