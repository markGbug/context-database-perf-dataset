# FastAPI：关键词搜索与分页

- 来源：[关键词搜索与分页](https://www.runoob.com/fastapi/fastapi-blog-search-pagination.html)
- 分类：Python / 数据科学
- 技术：FastAPI
- 笔记类型：学习笔记
- 章节序号：3870

## 本章内容

本章你将学会用 SQLAlchemy 实现联合搜索，并用 offset/limit 实现分页。


## ilike 大小写不敏感搜索


## 实例


## offset/limit 分页

Flask-SQLAlchemy 提供了便捷的 .paginate() 方法。

FastAPI 使用的是原生 SQLAlchemy，需要用 offset + limit 手动实现分页。


### 分页计算公式


## 实例


## 完整的搜索 + 分页视图


## 实例

Query(1, ge=1) 中的 ge 是 greater than or equal 的缩写。FastAPI 的查询参数支持完整的数值约束：ge、le、gt、lt。如果用户传入 page=0，FastAPI 会自动返回 422 错误。


## 模板中的分页导航


## 实例


## 本章小结

本章你实现了列表页的实用功能：ilike 大小写不敏感搜索、or_() 多字段联合搜索、offset/limit 手动分页（替代 Flask 的 paginate）、查询参数用 Query() 约束范围。

搜索 + 分类筛选 + 分页可以任意组合，条件不会丢失。


## 复习重点

- 能说明 `关键词搜索与分页` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
