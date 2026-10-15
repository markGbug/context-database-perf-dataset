# Django：打包上线 — 部署到 Railway

- 来源：[打包上线](https://www.runoob.com/django/django-blog-deploy.html)
- 分类：Python / 数据科学
- 技术：Django
- 笔记类型：练习笔记
- 章节序号：3835

## 本章内容

本章你将学会配置生产环境，将 Django 博客应用部署到 Railway，获得公开访问链接。


## 生产环境配置

开发环境中 DEBUG=True，Django 会显示详细的错误信息和调试页面。

生产环境中必须关闭 DEBUG，并正确配置安全选项。


### settings.py 生产配置


## 实例

SECRET_KEY 是 Django 最重要的安全密钥，用于加密 session、CSRF token 等。绝对不能硬编码在代码中或提交到 Git。生产环境中通过环境变量注入。


## 依赖管理与 requirements.txt

生成依赖列表，部署平台用它来安装项目所需的包。

```text
(venv) $ pip freeze > requirements.txt
```

检查文件内容，确保包含以下关键依赖：

```text
Django>=5.0,<6.0
gunicorn>=21.0              # 生产级 WSGI 服务器
whitenoise>=6.0             # 静态文件服务（可选）
```

如果没有 gunicorn，先安装：

```text
(venv) $ pip install gunicorn
(venv) $ pip freeze > requirements.txt
```


## 配置 Gunicorn + Whitenoise

Django 自带的 runserver 不适合生产环境。

Gunicorn 是 Python 生产级 WSGI 服务器，处理并发请求。

Whitenoise 让 Gunicorn 能直接提供静态文件服务（CSS、JS、图片）。


## 实例

在项目根目录创建 Procfile，告诉 Railway 如何启动应用：

```text
web: gunicorn blog_project.wsgi --log-file -
```


## 收集静态文件

生产环境下，Django 不自动提供静态文件服务，需要用 collectstatic 收集到统一目录。

```text
(venv) $ python manage.py collectstatic
```

这个命令会把 Admin 后台的静态文件、blog 应用的静态文件都复制到 STATIC_ROOT 目录（staticfiles/）。

开发环境中一般不需要运行 collectstatic（Django 会自动查找各 App 的 static 目录）。但部署前必须运行，确保所有静态文件集中到一个目录供 Web 服务器使用。


## 将项目推送到 GitHub


### 创建 .gitignore

确保敏感文件和临时文件不被提交：

```text
venv/
__pycache__/
*.pyc
db.sqlite3
staticfiles/
.env
```


### 推送到 GitHub

```text
$ git init
$ git add .
$ git commit -m "初始化 Django 博客项目"
$ git branch -M main
$ git remote add origin https://github.com/你的用户名/django-blog.git
$ git push -u origin main
```


## Railway 部署

Railway 是新兴的云部署平台，对 Django 这类全栈应用支持良好。


### 部署步骤

- 访问 railway.app，用 GitHub 账号登录
- 点击 "New Project" → "Deploy from GitHub repo" → 选择 django-blog 仓库
- Railway 会自动检测 Procfile，识别启动命令
- 在 Variables 中设置环境变量
- 点击 Deploy，等待构建和部署完成


### 环境变量配置

快速生成 SECRET_KEY：

```text
$ python -c "import secrets; print(secrets.token_urlsafe(50))"
```

部署成功后，获得链接如：https://django-blog.up.railway.app

Railway 免费额度有限（每月 $5 或 500 小时）。如果只是测试学习，用完记得暂停项目。Heroku 已取消免费计划，所以本教程推荐 Railway 作为替代。


## 下一步学习方向


## 本章小结

本章你完成了最后一步：配置生产环境（SECRET_KEY/DEBUG/ALLOWED_HOSTS）、生成 requirements.txt、配置 Gunicorn + Procfile、推送到 GitHub、Railway 一键部署上线。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `打包上线` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
