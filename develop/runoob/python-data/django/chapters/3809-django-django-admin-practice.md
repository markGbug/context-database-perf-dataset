# Django：Django django-admin 命令详解

- 来源：[Django django-admin](https://www.runoob.com/django/django-django-admin.html)
- 分类：Python / 数据科学
- 技术：Django
- 笔记类型：练习笔记
- 章节序号：3809

## 本章内容

django-admin 是 Django 框架提供的一个命令行工具，它是管理 Django 项目的核心工具。

无论是创建新项目、运行开发服务器，还是执行数据库迁移，django-admin 都是不可或缺的工具。

要查看 django-admin 提供的所有命令，可以运行：

```text
django-admin help
```

输出内容类似如下：

```html
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
    optimizemigration
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
```


## 常用 django-admin 命令详解


### 1. 创建新项目

```text
django-admin startproject 项目名称
```

这个命令会在当前目录下创建一个新的 Django 项目，包含基本的项目结构：

- manage.py：项目管理脚本
- 项目名称/：项目主目录 __init__.py settings.py：项目设置文件 urls.py：URL 路由配置 wsgi.py：WSGI 应用入口


### 2. 创建新应用

虽然通常使用 manage.py 来创建应用，但也可以通过 django-admin：

```text
django-admin startapp 应用名称
```

这会创建一个新的 Django 应用，包含：

- migrations/：数据库迁移文件目录
- __init__.py
- admin.py：管理后台配置
- apps.py：应用配置
- models.py：数据模型定义
- tests.py：测试代码
- views.py：视图函数


### 3. 检查项目配置

```text
django-admin check
```

这个命令会检查你的 Django 项目是否有配置错误，包括：

- 模型定义是否正确
- URL 配置是否有效
- 模板设置是否正确
- 静态文件配置等


### 4. 数据库迁移

Django 使用迁移系统来管理数据库模式变更：

```text
django-admin makemigrations  # 创建迁移文件
django-admin migrate        # 应用迁移到数据库
```


### 5. 创建超级用户

```text
django-admin createsuperuser
```

这个命令会引导你创建一个可以访问 Django 管理后台的超级用户。


## django-admin 常用命令


### django-admin startproject（创建项目）

基本语法:

```text
django-admin startproject <项目名称> [目标目录]
```

参数说明:


## 实例


### django-admin startapp（创建应用）

基本语法:

```text
django-admin startapp <应用名称> [目标目录]
```

参数说明:


## 实例


### django-admin runserver（启动开发服务器）

基本语法:

```text
python manage.py runserver [IP:端口]
```

参数说明:


## 实例


### django-admin migrate（数据库迁移）

基本语法:

```text
python manage.py migrate [应用名] [迁移版本]
```

参数说明:


## 实例


### 其他常用命令


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Django django-admin` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
