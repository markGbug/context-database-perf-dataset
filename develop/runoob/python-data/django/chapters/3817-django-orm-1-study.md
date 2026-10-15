# Django：Django ORM - 单表实例

- 来源：[Django ORM - 单表实例](https://www.runoob.com/django/django-orm-1.html)
- 分类：Python / 数据科学
- 技术：Django
- 笔记类型：学习笔记
- 章节序号：3817

## 本章内容

阅读本章节前你需要先阅读了 Django 模型 进行基础配置及了解常见问题的解决方案。

接下来我们重新创建一个项目 app01（如果之前已创建过，忽略以下操作）:

```text
django-admin.py startproject app01
```

接下来在 settings.py 中找到 INSTALLED_APPS 这一项，如下：

```text
INSTALLED_APPS = (
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'app01',               # 添加此项
)
```

接下来，告诉 Django 使用 pymysql 模块连接 mysql 数据库：


## 实例


### 创建模型

在项目中的 models.py 中添加以下类：


## app01/models.py

然后在命令行执行以下命令：

```text
$ python3 manage.py migrate   # 创建表结构

$ python3 manage.py makemigrations app01  # 让 Django 知道我们在我们的模型有一些变更
$ python3 manage.py migrate app01   # 创建表结构
```


### 常见报错信息

如果执行以上命令时会出现如下报错信息:

原因是 MySQLclient 目前只支持到 Python3.4，因此如果使用的更高版本的 python，需要修改如下：

通过报错信息的文件路径找到 ...site-packages\Django-2.0-py3.6.egg\django\db\backends\mysql 这个路径里的 base.py 文件，把这两行代码注释掉（代码在文件开头部分）：

```text
if version < (1, 3, 13):
    raise ImproperlyConfigured('mysqlclient 1.3.13 or newer is required; you have %s.' % Database.__version__)
```

一般点报错的代码文件路径信息，会自动跳转到报错文件中行数，此时我们在报错的代码行数注释掉。

这时数据库 runoob 就会创建一个 app01_book 的表。

接下来我们在app01 项目里添加 views.py 和 models.py 文件，app01 项目目录结构：

```text
app01
|-- app01
|   |-- __init__.py
|   |-- __pycache__
|   |-- asgi.py
|   |-- migrations
|   |-- models.py
|   |-- settings.py
|   |-- urls.py
|   |-- views.py
|   `-- wsgi.py
```


### 数据库添加

规则配置：


## app01/urls.py: 文件代码：

```text
from django.contrib import admin
from django.urls import path
from . import views

urlpatterns = [
    path('add_book/', views.add_book),
]
```

方式一：模型类实例化对象

需从 app 目录引入 models.py 文件：

```text
from app 目录 import models
```

并且实例化对象后要执行 对象.save() 才能在数据库中新增成功。


## app01/views.py: 文件代码：

```html
from django.shortcuts import render,HttpResponse
from app01 import models
def add_book(request):
    book = models.Book(title="菜鸟教程",price=300,publish="菜鸟出版社",pub_date="2008-8-8")
    book.save()
    return HttpResponse("<p>数据添加成功！</p>")
```

方式二：通过 ORM 提供的 objects 提供的方法 create 来实现（推荐）


## app01/views.py: 文件代码：

```html
from django.shortcuts import render,HttpResponse
from app01 import models
def add_book(request):
    books = models.Book.objects.create(title="如来神掌",price=200,publish="功夫出版社",pub_date="2010-10-10")
    print(books, type(books)) # Book object (18)
    return HttpResponse("<p>数据添加成功！</p>")
```


### 查找

使用 all() 方法来查询所有内容。

返回的是 QuerySet 类型数据，类似于 list，里面放的是一个个模型类的对象，可用索引下标取出模型类的对象。


## app01/views.py: 文件代码：

```html
from django.shortcuts import render,HttpResponse
from app01 import models
def add_book(request):
    books = models.Book.objects.all()
    print(books,type(books)) # QuerySet类型，类似于list，访问 url 时数据显示在命令行窗口中。
    return HttpResponse("<p>查找成功！</p>")
```

filter() 方法用于查询符合条件的数据。

返回的是 QuerySet 类型数据，类似于 list，里面放的是满足条件的模型类的对象，可用索引下标取出模型类的对象。

pk=3 的意思是主键 primary key=3，相当于 id=3。

因为 id 在 pycharm 里有特殊含义，是看内存地址的内置函数 id()，因此用 pk。


## app01/views.py: 文件代码：

```html
from django.shortcuts import render,HttpResponse
from app01 import models
def add_book(request):
    books = models.Book.objects.filter(pk=5)
    print(books)
    print("//////////////////////////////////////")
    books = models.Book.objects.filter(publish='菜鸟出版社', price=300)
    print(books, type(books))  # QuerySet类型，类似于list。
    return HttpResponse("<p>查找成功！</p>")
```

exclude() 方法用于查询不符合条件的数据。

返回的是 QuerySet 类型数据，类似于 list，里面放的是不满足条件的模型类的对象，可用索引下标取出模型类的对象。


## app01/views.py: 文件代码：

```html
from django.shortcuts import render,HttpResponse
from app01 import models
def add_book(request):
    books = models.Book.objects.exclude(pk=5)
    print(books)
    print("//////////////////////////////////////")
    books = models.Book.objects.exclude(publish='菜鸟出版社', price=300)
    print(books, type(books))  # QuerySet类型，类似于list。
    return HttpResponse("<p>查找成功！</p>")
```

get() 方法用于查询符合条件的返回模型类的对象符合条件的对象只能为一个，如果符合筛选条件的对象超过了一个或者没有一个都会抛出错误。


## app01/views.py: 文件代码：

```html
from django.shortcuts import render,HttpResponse
from app01 import models
def add_book(request):
    books = models.Book.objects.get(pk=5)
    books = models.Book.objects.get(pk=18)  # 报错，没有符合条件的对象
    books = models.Book.objects.get(price=200)  # 报错，符合条件的对象超过一个
    print(books, type(books))  # 模型类的对象
    return HttpResponse("<p>查找成功！</p>")
```

order_by() 方法用于对查询结果进行排序。

返回的是 QuerySet类型数据，类似于list，里面放的是排序后的模型类的对象，可用索引下标取出模型类的对象。

注意：

- a、参数的字段名要加引号。
- b、降序为在字段前面加个负号 -。


## app01/views.py: 文件代码：

```html
from django.shortcuts import render,HttpResponse
from app01 import models
def add_book(request):
    books = models.Book.objects.order_by("price") # 查询所有，按照价格升序排列
    books = models.Book.objects.order_by("-price") # 查询所有，按照价格降序排列
    return HttpResponse("<p>查找成功！</p>")
```

reverse() 方法用于对查询结果进行反转。

返回的是 QuerySe t类型数据，类似于 list，里面放的是反转后的模型类的对象，可用索引下标取出模型类的对象。


## app01/views.py: 文件代码：

```html
from django.shortcuts import render,HttpResponse
from app01 import models
def add_book(request):
    # 按照价格升序排列：降序再反转
    books = models.Book.objects.order_by("-price").reverse()
    return HttpResponse("<p>查找成功！</p>")
```

count() 方法用于查询数据的数量返回的数据是整数。


## app01/views.py: 文件代码：

```html
from django.shortcuts import render,HttpResponse
from app01 import models
def add_book(request):
    books = models.Book.objects.count() # 查询所有数据的数量
    books = models.Book.objects.filter(price=200).count() # 查询符合条件数据的数量
    return HttpResponse("<p>查找成功！</p>")
```

first() 方法返回第一条数据返回的数据是模型类的对象也可以用索引下标 [0]。


## app01/views.py: 文件代码：

```html
from django.shortcuts import render,HttpResponse
from app01 import models
def add_book(request):
    books = models.Book.objects.first() # 返回所有数据的第一条数据
    return HttpResponse("<p>查找成功！</p>")
```

last() 方法返回最后一条数据返回的数据是模型类的对象不能用索引下标 [-1]，ORM 没有逆序索引。


## app01/views.py: 文件代码：

```html
from django.shortcuts import render,HttpResponse
from app01 import models
def add_book(request):
    books = models.Book.objects.last() # 返回所有数据的最后一条数据
    return HttpResponse("<p>查找成功！</p>")
```

exists() 方法用于判断查询的结果 QuerySet 列表里是否有数据。

返回的数据类型是布尔，有为 true，没有为 false。

注意：判断的数据类型只能为 QuerySet 类型数据，不能为整型和模型类的对象。


## 实例

values() 方法用于查询部分字段的数据。

返回的是 QuerySet 类型数据，类似于 list，里面不是模型类的对象，而是一个可迭代的字典序列，字典里的键是字段，值是数据。

注意：

- 参数的字段名要加引号
- 想要字段名和数据用 values


## 复习重点

- 能说明 `Django ORM - 单表实例` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
