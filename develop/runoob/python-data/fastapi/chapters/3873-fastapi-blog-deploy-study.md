# FastAPI：打包上线 — 部署到 Railway

- 来源：[打包上线](https://www.runoob.com/fastapi/fastapi-blog-deploy.html)
- 分类：Python / 数据科学
- 技术：FastAPI
- 笔记类型：学习笔记
- 章节序号：3873

## 本章内容

本章你将学会 FastAPI 的生产环境配置，并用 Railway 将博客部署上线。


## 生产环境配置管理

```text
(venv) $ pip install pydantic-settings python-dotenv
```


## 实例

创建 .env 文件：

```text
SECRET_KEY=a1b2c3d4...your-real-secret-key
DATABASE_URL=sqlite:///./blog.db
DEBUG=False
```


## 生成依赖文件

```text
(venv) $ pip freeze > requirements.txt
```

确保包含核心依赖：fastapi、uvicorn、sqlalchemy、jinja2、alembic、passlib、python-jose、python-multipart、sqladmin、pydantic-settings。


## 配置 Procfile 和启动命令

FastAPI 使用 ASGI 服务器，与 Flask/Django 的 WSGI 不同：

```text
web: uvicorn main:app --host 0.0.0.0 --port $PORT
```

如果需要多 worker（生产环境推荐）：

```text
web: gunicorn -k uvicorn.workers.UvicornWorker -w 4 main:app
```

WSGI vs ASGI：Django/Flask 用 Gunicorn（WSGI 服务器），FastAPI 用 Uvicorn（ASGI 服务器）。Gunicorn 本身是 WSGI，但可以通过 uvicorn.workers.UvicornWorker 跑 ASGI 应用。


## 推送到 GitHub

```text
$ git init
$ echo "venv/" > .gitignore
$ echo "__pycache__/" >> .gitignore
$ echo "*.pyc" >> .gitignore
$ echo ".env" >> .gitignore
$ git add .
$ git commit -m "初始化 FastAPI 博客项目"
$ git branch -M main
$ git remote add origin https://github.com/你的用户名/fastapi-blog.git
$ git push -u origin main
```


## Railway 部署

- 访问 railway.app，用 GitHub 登录
- New Project → Deploy from GitHub repo → 选择 fastapi-blog
- Railway 自动检测 Procfile
- 在 Variables 中设置环境变量
- 点击 Deploy


### 环境变量配置

部署成功后获得链接，访问 /docs 能看到 Swagger 文档，访问 /admin 进入后台管理。


## 框架对比


## 下一步学习方向


## 复习重点

- 能说明 `打包上线` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
