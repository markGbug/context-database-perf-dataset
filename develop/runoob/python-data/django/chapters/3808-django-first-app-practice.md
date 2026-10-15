# Django：Django 创建第一个项目

- 来源：[Django 创建第一个项目](https://www.runoob.com/django/django-first-app.html)
- 分类：Python / 数据科学
- 技术：Django
- 笔记类型：练习笔记
- 章节序号：3808

## 本章内容

本章我们将介绍 Django 管理工具及如何使用 Django 来创建项目，第一个项目我们以 HelloWorld 来命令项目。

测试版本说明：

- Python 3.9.7
- Django 4.2.7

通过以下命令可以查看版本号：

```text
# python3 -V
Python 3.9.7
# python3 -m django --version
4.2.7
```


## Django 管理工具

安装 Django 之后，您现在应该已经有了可用的管理工具 django-admin，Windows 如果没有配置环境变量可以用 django-admin。

我们可以来看下django-admin 的命令介绍:

```html
$ django-admin

Type 'django-admin help <subcommand>' for help on a specific subcommand.

Available subcommands:

[django]
    check
    compilemessages
    createcachetable
    dbshell
    diffsettings
    dumpdata
    flush
    inspectdb
    loaddata
    makemessages
    makemigrations
    migrate
    runserver
    sendtestemail
    shell
    showmigrations
    sqlflush
    sqlmigrate
    sqlsequencereset
    squashmigrations
    startapp
    startproject
    test
    testserver
……省略部分……
```


## 创建第一个项目

使用 django-admin 来创建 HelloWorld 项目：

```text
django-admin startproject HelloWorld
```

创建完成后我们可以查看下项目的目录结构：

```text
$ cd HelloWorld/
$ tree
HelloWorld/                  # 项目根目录
├── manage.py                # 项目管理脚本
├── db.sqlite3               # SQLite 数据库文件
├── __pycache__/             # Python 字节码缓存
└── HelloWorld/              # 项目配置目录（与项目同名）
    ├── __init__.py          # 包标识文件
    ├── settings.py          # 项目设置
    ├── urls.py             # 主路由配置
    ├── asgi.py             # ASGI 配置
    └── wsgi.py             # WSGI 配置
```

项目根目录 (HelloWorld/)：

主项目配置目录 (HelloWorld/HelloWorld/) ：

接下来我们进入 HelloWorld 目录输入以下命令，启动服务器：

```text
python3 manage.py runserver 0.0.0.0:8000
```

0.0.0.0 让其它电脑可连接到开发服务器，8000 为端口号。如果不说明，那么端口号默认为 8000。

在浏览器输入你服务器的 ip（这里我们输入本机 IP 地址： 127.0.0.1:8000） 及端口号，如果正常启动，输出结果如下：


### 关键文件详解

1. settings.py（核心配置）


## 实例

2. urls.py（路由配置）


## 实例

3. manage.py（项目管理脚本）


## 实例


## 视图和 URL 配置

在先前创建的 HelloWorld 目录下的 HelloWorld 目录新建一个 views.py 文件，并输入代码：


## HelloWorld/HelloWorld/views.py 文件代码：

```text
from django.http import HttpResponse

def hello(request):
    return HttpResponse("Hello world ! ")
```

接着，绑定 URL 与视图函数。打开 urls.py 文件，删除原来代码，将以下代码复制粘贴到 urls.py 文件中：


## HelloWorld/HelloWorld/urls.py 文件代码：

```text
from django.urls import path

from . import views

urlpatterns = [
    path("", views.hello, name="hello"),
]
```

整个目录结构如下：

```text
$ tree
.
|-- HelloWorld
|   |-- __init__.py
|   |-- __init__.pyc
|   |-- settings.py
|   |-- settings.pyc
|   |-- urls.py              # url 配置
|   |-- urls.pyc
|   |-- views.py              # 添加的视图文件
|   |-- views.pyc             # 编译后的视图文件
|   |-- wsgi.py
|   `-- wsgi.pyc
`-- manage.py
```

完成后，启动 Django 开发服务器，并在浏览器访问打开浏览器并访问：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Django 创建第一个项目` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
