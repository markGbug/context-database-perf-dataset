# FastAPI：SQLAlchemy 模型 — 设计数据库表

- 来源：[SQLAlchemy 模型](https://www.runoob.com/fastapi/fastapi-blog-sqlalchemy.html)
- 分类：Python / 数据科学
- 技术：FastAPI
- 笔记类型：练习笔记
- 章节序号：3866

## 本章内容

本章你将学会用原生 SQLAlchemy ORM 定义数据模型，并通过 FastAPI 依赖注入管理数据库会话。


## FastAPI 为什么不用自带 ORM？

Django 有内置 ORM，Flask 推荐 Flask-SQLAlchemy。

FastAPI 没有内置 ORM——它希望你选择最适合的工具，SQLAlchemy + Pydantic 是社区公认的最佳组合。

```text
(venv) $ pip install sqlalchemy
```


## 配置数据库连接


## 实例

check_same_thread=False 是 SQLite 在 FastAPI 中的必要配置。默认情况下 SQLite 不允许跨线程使用同一连接，但在 Web 应用中每个请求可能在不同线程中处理。


### 依赖注入：get_db


## 实例

Depends(get_db) 是 FastAPI 的依赖注入系统，路由函数通过依赖注入自动获得数据库会话。


## 定义模型：Post 和 Category


## 实例

FastAPI 中使用的是 原生 SQLAlchemy（不是 Flask-SQLAlchemy 的 db.Model）。注意：Column 导入、Base 继承、relationship 写法的差异。后面会有对照表。


## 初始化数据库表


## 实例

之后会改用 Alembic 迁移（第六章），create_all 仅在快速原型阶段使用。


## 插入测试数据

在 Python 脚本中插入测试数据：


## 实例

运行 python seed.py，数据库中插入 3 篇文章。


## 四框架 ORM 写法对照


## 本章小结

本章你掌握了 FastAPI 中的 SQLAlchemy 集成：create_engine + SessionLocal 配置数据库连接、DeclarativeBase 定义模型基类、get_db 依赖注入管理会话、Column/relationship 定义字段和关系。

与 Flask-SQLAlchemy 相比，原生 SQLAlchemy 写法稍多但完全开源可控。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `SQLAlchemy 模型` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
