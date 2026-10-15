# FastAPI：FastAPI 数据库集成

- 来源：[FastAPI 数据库集成](https://www.runoob.com/fastapi/fastapi-sql-database.html)
- 分类：Python / 数据科学
- 技术：FastAPI
- 笔记类型：学习笔记
- 章节序号：3863

## 本章内容

FastAPI 可以与各种数据库集成，最常用的方式是使用 SQLAlchemy 作为 ORM。本节介绍如何使用 FastAPI + SQLAlchemy 构建具有 CRUD（创建、读取、更新、删除）功能的 API。


## 安装依赖

```text
pip install sqlalchemy
```


## 项目结构

```text
project/
├── main.py          # FastAPI 应用入口
├── database.py      # 数据库连接配置
├── models.py        # SQLAlchemy 模型
├── schemas.py       # Pydantic 数据模型
└── crud.py          # 数据库操作函数
```


## 1. 数据库配置

在 database.py 中配置数据库连接：


## 实例

开发环境使用 SQLite 即可，它是一个文件数据库，无需安装额外的数据库服务。生产环境建议使用 PostgreSQL 或 MySQL，只需修改 SQLALCHEMY_DATABASE_URL 即可。


## 2. SQLAlchemy 模型

在 models.py 中定义数据库表结构：


## 实例


## 3. Pydantic 数据模型

在 schemas.py 中定义 API 的输入/输出数据结构：


## 实例

Pydantic 模型与 SQLAlchemy 模型是分离的。Pydantic 负责 API 层的数据校验，SQLAlchemy 负责数据库层的表结构。from_attributes=True 让 Pydantic 能够从 SQLAlchemy 对象中读取数据。


## 4. 数据库操作函数

在 crud.py 中封装数据库操作：


## 实例


## 5. FastAPI 应用入口

在 main.py 中整合所有组件：


## 实例


## 数据库会话的依赖注入

核心模式是使用依赖注入管理数据库会话：

```text
def get_db():
    db = SessionLocal()   # 创建会话
    try:
        yield db          # 提供会话给路由函数
    finally:
        db.close()        # 请求完成后关闭会话
```

每个请求获取独立的数据库会话，请求完成后自动关闭，避免资源泄露。


## 不同数据库的连接字符串

切换数据库只需修改连接字符串，其余代码无需改动。这也是使用 ORM 的优势之一。


## 小结

- 使用 SQLAlchemy 作为 ORM，FastAPI 通过依赖注入管理数据库会话
- Pydantic 模型（schemas.py）负责 API 数据校验，SQLAlchemy 模型（models.py）负责数据库表结构
- CRUD 操作封装在 crud.py 中，保持代码清晰
- 开发使用 SQLite，生产切换到 PostgreSQL/MySQL 只需改连接字符串
- from_attributes=True 让 Pydantic 能从 ORM 对象读取数据


## 复习重点

- 能说明 `FastAPI 数据库集成` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
