# Django：Django 项目结构解析

- 来源：[Django 项目结构解析](https://www.runoob.com/django/django-project-intro.html)
- 分类：Python / 数据科学
- 技术：Django
- 笔记类型：学习笔记
- 章节序号：3810

## 本章内容

通过理解 Django 的项目结构，我们可以更高效地组织代码，遵循 Django 的最佳实践，构建可维护的 Web 应用程序。

```text
myproject/
│
├── manage.py
└── myproject/
    ├── __init__.py
    ├── settings.py
    ├── urls.py
    └── wsgi.py
```

使用 django-admin 来创建 HelloWorld 项目：

```text
django-admin startproject HelloWorld
```

创建完成后我们可以查看下项目的目录结构：


## 核心文件解析


### manage.py

manage.py 是 Django 项目的命令行工具入口，它提供了许多有用的命令：


## 实例

常用命令示例：

- python manage.py runserver - 启动开发服务器
- python manage.py migrate - 应用数据库迁移
- python manage.py createsuperuser - 创建管理员账户


### settings.py

settings.py 是 Django 项目的配置文件，包含所有重要的设置：


## 实例


### urls.py（URL 调度中心）


## 实例

- include()：实现路由模块化，将不同应用的路由分离到各自的 urls.py。
- namespace：用于反向解析 URL 时避免命名冲突。


### wsgi.py & asgi.py


### 扩展目录（非自动生成，但常用）

```text
HelloWorld/
├── apps/               # 推荐：存放所有自定义应用
│   └── blog/          # 示例应用
├── static/             # 静态文件（CSS/JS/图片）
├── media/              # 用户上传文件
├── templates/          # 全局模板目录
└── requirements.txt    # 项目依赖列表
```

将应用集中管理，避免散落在项目根目录。

需在 settings.py 中配置 Python 路径：

```text
import sys
sys.path.insert(0, os.path.join(BASE_DIR, 'apps'))
```

- static/：存放 CSS、JavaScript、图片等，通过 STATIC_URL 访问。
- media/：用户上传的文件（如头像），通过 MEDIA_URL 访问。需配置服务器在开发时提供访问： # urls.py（仅开发环境） from django.conf import settings from django.conf.urls.static import static urlpatterns += static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)


## Django 应用结构

在 Django 中，一个项目可以包含多个应用。使用 python manage.py startapp myapp 创建一个新应用后，会生成以下结构：

```text
myapp/
│
├── migrations/
│   └── __init__.py
├── __init__.py
├── admin.py
├── apps.py
├── models.py
├── tests.py
└── views.py
```


### 主要应用文件

定义数据模型，与数据库表对应：


## 实例

处理业务逻辑，返回响应：


## 实例

配置 Django 管理后台：


## 实例


## 完整项目结构示例

一个典型的 Django 项目完整结构如下：

```text
myproject/
│
├── manage.py
├── requirements.txt
├── static/
│   ├── css/
│   ├── js/
│   └── images/
├── media/
├── templates/
│   └── base.html
└── myproject/
    ├── __init__.py
    ├── settings.py
    ├── urls.py
    ├── wsgi.py
    └── asgi.py
└── myapp1/
    ├── migrations/
    ├── templates/
    │   └── myapp1/
    ├── __init__.py
    ├── admin.py
    ├── apps.py
    ├── models.py
    ├── tests.py
    ├── urls.py
    └── views.py
└── myapp2/
    └── ... (类似结构)
```


## 重要目录说明


### migrations 目录

存储数据库迁移文件，Django 使用这些文件来跟踪模型变更并同步到数据库。


### static 目录

存放静态文件（CSS, JavaScript, 图片等），在部署时会收集到指定位置。


### templates 目录

存放 HTML 模板文件，Django 使用模板语言动态生成页面。


### media 目录

存储用户上传的文件，需要在 settings.py 中配置：


## 实例


## 实践建议

- 项目与应用分离：保持每个应用的独立性，便于复用
- 环境配置：使用不同的 settings 文件区分开发和生产环境
- 静态文件管理：开发时使用 STATICFILES_DIRS，生产时使用 collectstatic
- URL 设计：在应用级别定义 URL，然后在项目级别包含
- 模板组织：为每个应用创建子目录存放模板


### 生产环境 vs 开发环境差异


## 复习重点

- 能说明 `Django 项目结构解析` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
