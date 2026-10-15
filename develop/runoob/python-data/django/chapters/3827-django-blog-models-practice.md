# Django：模型与数据库

- 来源：[模型与数据库](https://www.runoob.com/django/django-blog-models.html)
- 分类：Python / 数据科学
- 技术：Django
- 笔记类型：练习笔记
- 章节序号：3827

## 本章内容

本章你将学会用 Django ORM 定义数据模型，创建数据库表，并插入测试数据。


## 为什么需要模型？

上一章我们硬编码了页面文字。真正的博客需要存储多篇文章，且内容随时会变。

模型（Model） 是 Django 的数据库层：用 Python 类定义数据结构，Django 自动生成对应的数据库表。

你不需要写一行 SQL——这就是 ORM（对象关系映射） 的核心价值。


## 定义 Post 模型

打开 blog/models.py，定义文章模型。


## 实例


### 常用字段类型速查

__str__ 方法决定了对象如何以字符串形式显示。在 Admin 后台的下拉选择框和 Shell 输出中，都会调用它来展示对象名称。不写这个方法，你会看到 Post object (1) 这样的无意义文字。


## 迁移：将模型同步到数据库

模型类写好后，需要用 迁移（Migration） 建立数据库表。

```text
(venv) $ python manage.py makemigrations   # 生成迁移文件（检测模型变化）
Migrations for 'blog':
  blog/migrations/0001_initial.py
    - Create model Category
    - Create model Post

(venv) $ python manage.py migrate           # 执行迁移（创建数据库表）
Operations to perform:
  Apply all migrations: admin, auth, blog, contenttypes, sessions
Running migrations:
  Applying blog.0001_initial... OK
```

两个命令的分工：

- makemigrations：扫描 models.py，生成迁移脚本（Python 文件）
- migrate：执行迁移脚本，在数据库中创建真实的表

每次修改 models.py 后，都要运行 makemigrations + migrate 这两个命令。缺一不可：只 makemigrations 没 migrate，表不会创建；直接 migrate 不 makemigrations，Django 不知道你改了模型。


## 用 Django Shell 插入测试数据

在开始写页面之前，先用 Django Shell 往数据库里录入几条数据，验证模型是否正常工作。

```text
(venv) $ python manage.py shell
```

这会打开一个交互式 Python Shell，可以在里面操作数据库。


## 实例


## Django ORM 基础查询

ORM 让你用 Python 方法链操作数据库，无需写 SQL。

QuerySet 是 惰性求值 的：定义了查询不会立即执行，只有在真正需要数据时（如遍历、打印、转为 list）才发 SQL。所以你可以链式调用多个 filter 而不产生多次查询。


## 动手：为后续章节准备数据

在 Shell 中多录入几篇文章和分类，覆盖 Django、Python、CSS 三个分类，每个分类至少 2 篇文章。

可以编写一个管理命令或脚本批量插入，但现阶段用 Shell 逐条插入足够了。


## 本章小结

本章你掌握了 Django ORM 的核心流程：在 models.py 中定义 Python 类（模型）、makemigrations 生成迁移文件、migrate 同步到数据库、用 Shell 和 ORM 查询插入数据。

至此，文章和分类的结构已在数据库中建立。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `模型与数据库` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
