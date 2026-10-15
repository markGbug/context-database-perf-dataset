# Django：Django 博客项目

- 来源：[Django 博客项目](https://www.runoob.com/django/django-blog-project-init.html)
- 分类：Python / 数据科学
- 技术：Django
- 笔记类型：学习笔记
- 章节序号：3826

## 本章内容

本章带你从零开始，用 Django 创建一个博客项目，理解项目结构和请求生命周期。


## 环境准备

Django 是 Python Web 框架，需要先确认 Python 环境。

打开终端，检查 Python 版本（需要 3.8 以上）：

```text
$ python3 --version
Python 3.12.0
```


### 创建虚拟环境并安装 Django

虚拟环境是 Python 项目的标准实践，让每个项目有独立的依赖，互不干扰。

```text
$ python3 -m venv venv               # 创建虚拟环境
$ source venv/bin/activate           # 激活虚拟环境（Windows：venv\Scripts\activate）
(venv) $ pip install django          # 在虚拟环境中安装 Django
```

验证安装是否成功：

```text
(venv) $ python -m django --version
5.0
```

每次打开新终端，都需要先执行 source venv/bin/activate 激活虚拟环境。终端提示符前面的 (venv) 表示当前已在虚拟环境中。


## 创建 Django 项目

Django 提供了 django-admin startproject 命令来初始化项目。

```text
(venv) $ django-admin startproject blog_project
(venv) $ cd blog_project
```

执行后会生成以下目录结构：

```text
blog_project/
├── manage.py                    # 项目管理入口（启动服务器、执行迁移、创建 admin 等）
├── blog_project/                # 项目配置包
│   ├── __init__.py              # 标识这是一个 Python 包
│   ├── settings.py              # 全局配置（数据库、中间件、模板、静态文件等）
│   ├── urls.py                  # 根 URL 路由表
│   ├── wsgi.py                  # WSGI 部署入口（生产环境用）
│   └── asgi.py                  # ASGI 部署入口（WebSocket 用）
```


### 启动开发服务器

```text
(venv) $ python manage.py runserver
Watching for file changes with StatReloader
Performing system checks...
System check identified no issues (0 silenced).
Starting development server at http://127.0.0.1:8000/
```

浏览器访问 http://127.0.0.1:8000/，看到 Django 的欢迎页面，说明启动成功。

开发服务器自带热重载：修改代码保存后，服务器会自动重启。按 Ctrl+C 停止服务器。


## settings.py 关键配置说明

settings.py 是 Django 项目的中央配置文件，每个配置项都有明确的含义。

把语言和时区改为中文环境：


## 实例


## 创建第一个应用：blog

Django 的项目组织方式是 项目（Project）包含多个应用（App）。

每个 App 负责一个独立的功能模块（如博客、用户、评论）。

```text
(venv) $ python manage.py startapp blog
```

执行后生成了 blog/ 目录：

```text
blog/
├── __init__.py
├── admin.py       # 后台管理配置（第三章用到）
├── apps.py        # 应用配置
├── models.py      # 数据库模型（第二章用到）
├── views.py       # 视图函数（本章用到）
├── urls.py        # 需要手动创建（应用级路由）
└── migrations/    # 数据库迁移文件（第二章用到）
```

创建 App 后，需要在 settings.py 中注册：


## 实例


## Django 请求生命周期

理解请求在 Django 中的流转过程，有助于后续快速定位问题。

浏览器输入 URL → urls.py 匹配路由 → views.py 处理逻辑 → templates 渲染 HTML → 返回浏览器。

这三步（URL → View → Template）是 Django 开发的骨架模式。


## 动手：第一个 Django 页面


### 第一步：编写视图函数（views.py）


## 实例


### 第二步：创建模板文件（templates）

在 blog/ 目录下创建 templates/blog/ 子目录，然后创建 index.html。


## 实例

Django 模板变量使用 {{ 变量名 }} 语法，与 Vue3 的插值表达式一样。views.py 中传给 render 的字典数据，在模板中可以直接用。


### 第三步：配置路由（urls.py）

先在 blog/ 下创建 urls.py 作为应用级路由。


## 实例

然后在项目级 urls.py 中用 include() 引入应用路由：


## 实例


## 本章小结

本章你完成了三件事：创建虚拟环境并安装 Django、用 startproject/startapp 初始化项目、编写了 View → Template → URL 的完整链路。

核心收获：理解 Django 的项目/应用层级结构，掌握 URL → View → Template 三步走开发模式。


## 复习重点

- 能说明 `Django 博客项目` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
