# FastAPI：FastAPI Web 应用

- 来源：[FastAPI Web 应用](https://www.runoob.com/fastapi/fastapi-blog-project-init.html)
- 分类：Python / 数据科学
- 技术：FastAPI
- 笔记类型：学习笔记
- 章节序号：3864

## 本章内容

本章带你从零开始，用 FastAPI 创建第一个 Web 应用，体验自动生成的 API 文档。


## FastAPI 与 Django/Flask 的定位差异

FastAPI 是 Python Web 框架中的新星，定位介于 Django 和 Flask 之间。

FastAPI 最大的不同：用 Python 类型提示驱动一切——路由参数自动校验、请求/响应自动序列化、交互文档自动生成。


## 环境准备

```text
$ python3 -m venv venv
$ source venv/bin/activate
(venv) $ pip install fastapi uvicorn jinja2 python-multipart
```

三个核心依赖说明：

- fastapi：Web 框架本身
- uvicorn：ASGI 服务器（相当于 Flask 的 Gunicorn）
- jinja2：模板引擎（可选，但做 SSR 需要）


## FastAPI 最小应用


## 实例


### 启动服务器

```text
(venv) $ uvicorn main:app --reload
INFO:     Uvicorn running on http://127.0.0.1:8000
```

注意启动方式与 Flask 不同：

- Flask：flask run（基于 Werkzeug）
- FastAPI：uvicorn main:app（基于 ASGI，原生支持异步）


## 自动生成的 API 文档

这是 FastAPI 最惊艳的特性——不写任何额外代码，自动生成交互式文档。

访问 /docs 看到 Swagger UI，可以在页面上直接测试 API：

```text
http://127.0.0.1:8000/docs      # Swagger UI（交互式测试）
http://127.0.0.1:8000/redoc     # ReDoc（只读文档，更美观）
```

在 Swagger UI 中：点击 GET /hello/{name} → Try it out → 输入 name → Execute，就能看到真实响应。


## 项目目录结构规划

```text
blog_project/
├── main.py               # 应用入口
├── models.py             # SQLAlchemy ORM 模型
├── schemas.py            # Pydantic Schema（FastAPI 独有）
├── database.py           # 数据库连接与 Session
├── auth.py               # JWT 认证逻辑
├── routers/              # APIRouter 路由模块
│   ├── posts.py
│   ├── categories.py
│   ├── users.py
│   └── favorites.py
├── templates/            # Jinja2 模板
├── static/               # 静态文件
└── alembic/              # 数据库迁移
```

Flask 用 Blueprint 组织路由，FastAPI 用 APIRouter。概念类似但语法不同，且 APIRouter 天然带类型约束。


## 本章小结

本章你完成了三件事：安装了 FastAPI + Uvicorn、编写了第一个带类型提示的路由、访问了自动生成的 /docs 交互式 API 文档。

核心收获：FastAPI 用 Python 类型提示驱动参数校验和文档生成，这是它区别于 Django/Flask 最本质的特性。


## 复习重点

- 能说明 `FastAPI Web 应用` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
