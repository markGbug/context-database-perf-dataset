# Django：Django 模板

- 来源：[Django 模板](https://www.runoob.com/django/django-template.html)
- 分类：Python / 数据科学
- 技术：Django
- 笔记类型：练习笔记
- 章节序号：3811

## 本章内容

Django 的模板系统（Template System）是用于将业务逻辑（Python）与展示层（HTML）分离的核心组件，它允许开发者通过简单的标签和变量动态生成 HTML 页面。

在上一章节中我们使用 django.http.HttpResponse() 来输出 "Hello World！"，该方式将数据与视图混合在一起，不符合 Django 的 MVT 思想。

本章节我们将为大家详细介绍 Django 模板的应用，模板是一个文本，用于分离文档的表现形式和内容。


## 模板应用实例

我们接着上一章节的项目将在 HelloWorld 目录底下创建 templates 目录并建立 runoob.html文件，整个目录结构如下：

```text
HelloWorld/
|-- HelloWorld
|   |-- __init__.py
|   |-- __init__.pyc
|   |-- settings.py
|   |-- settings.pyc
|   |-- urls.py
|   |-- urls.pyc
|   |-- views.py
|   |-- views.pyc
|   |-- wsgi.py
|   `-- wsgi.pyc
|-- manage.py
`-- templates
    `-- runoob.html
```

runoob.html 文件代码如下：


## HelloWorld/templates/runoob.html 文件代码：

```html
<h1>{{ hello }}</h1>
```

从模板中我们知道变量使用了双括号 {{ }}。

接下来我们需要向 Django 说明模板文件的路径，打开 HelloWorld/HelloWorld/settings.py 文件，修改 TEMPLATES 中的 DIRS 为 [BASE_DIR / "templates"]，如下所示:


## HelloWorld/HelloWorld/settings.py 文件代码：

我们现在修改 views.py，增加一个新的对象，用于向模板提交数据：


## HelloWorld/HelloWorld/views.py 文件代码：

```text
from django.shortcuts import render

def runoob(request):
    context          = {}
    context['hello'] = 'Hello World!'
    return render(request, 'runoob.html', context)
```

可以看到，我们这里使用 render 来替代之前使用的 HttpResponse,render 还使用了一个字典 context 作为参数。

context 字典中元素的键值 hello 对应了模板中的变量 {{ hello }}。


## HelloWorld/HelloWorld/urls.py 文件代码：

```text
from django.contrib import admin
from django.urls import path
from . import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('runoob/', views.runoob),
]
```

接下来我们进入 HelloWorld 目录输入以下命令，启动服务器：

```text
python3 manage.py runserver 0.0.0.0:8000
```

再次访问 http://127.0.0.1:8000/runoob，可以看到页面：

这样我们就完成了使用模板来输出数据，从而实现数据与视图分离。

接下来我们将具体介绍模板中常用的语法规则。


## Django 模板标签

语法：

```text
{% tag %}
```

控制模板逻辑，常用标签：


### 变量

模板语法：

```text
view：｛"HTML变量名" : "views变量名"｝
HTML：｛｛变量名｝｝
```


## HelloWorld/HelloWorld/views.py 文件代码：

templates 中的 runoob.html ：

```html
<p>{{ name }}</p>
```

再次访问 http://127.0.0.1:8000/runoob，可以看到页面：


### 列表

templates 中的 runoob.html中，可以用 . 索引下标取出对应的元素。


## HelloWorld/HelloWorld/views.py 文件代码：


## HelloWorld/templates/runoob.html 文件代码：

```html
<p>{{ views_list }}</p>   # 取出整个列表
<p>{{ views_list.0 }}</p> # 取出列表的第一个元素
```

再次访问 http://127.0.0.1:8000/runoob，可以看到页面：


### 字典

templates 中的 runoob.html中，可以用 .键 取出对应的值。


## HelloWorld/HelloWorld/views.py 文件代码：


## HelloWorld/templates/runoob.html 文件代码：

```html
<p>{{ views_dict }}</p>
<p>{{ views_dict.name }}</p>
```

再次访问 http://127.0.0.1:8000/runoob，可以看到页面：


### 过滤器

```text
{{ 变量名 | 过滤器：可选参数 }}
```

模板过滤器可以在变量被显示前修改它，过滤器使用管道字符，如下所示：

```text
{{ name|lower }}
```

{{ name }} 变量被过滤器 lower 处理后，文档大写转换文本为小写。

过滤管道可以被* 套接* ，既是说，一个过滤器管道的输出又可以作为下一个管道的输入：

```text
{{ my_list|first|upper }}
```

以上实例将第一个元素并将其转化为大写。

有些过滤器有参数。 过滤器的参数跟随冒号之后并且总是以双引号包含。 例如：

```text
{{ bio|truncatewords:"30" }}
```

这个将显示变量 bio 的前30个词。

其他过滤器：

- addslashes : 添加反斜杠到任何反斜杠、单引号或者双引号前面。
- date : 按指定的格式字符串参数格式化 date 或者 datetime 对象，实例： {{ pub_date|date:"F j, Y" }}
- length : 返回变量的长度。

default

default 为变量提供一个默认值。

如果 views 传的变量的布尔值是 false，则使用指定的默认值。

以下值为 false：

```text
0  0.0  False  0j  ""  []  ()  set()  {}  None
```


## HelloWorld/HelloWorld/views.py 文件代码：


## HelloWorld/templates/runoob.html 文件代码：

```text
{{ name|default:"菜鸟教程666" }}
```

再次访问 http://127.0.0.1:8000/runoob，可以看到页面：

length

返回对象的长度，适用于字符串和列表。

字典返回的是键值对的数量，集合返回的是去重后的长度。


## HelloWorld/HelloWorld/views.py 文件代码：


## HelloWorld/templates/runoob.html 文件代码：

```text
{{ name|length}}
```

再次访问 http://127.0.0.1:8000/runoob，可以看到页面：

filesizeformat

以更易读的方式显示文件的大小（即'13 KB', '4.1 MB', '102 bytes'等）。

字典返回的是键值对的数量，集合返回的是去重后的长度。


## HelloWorld/HelloWorld/views.py 文件代码：


## HelloWorld/templates/runoob.html 文件代码：

```text
{{ num|filesizeformat}}
```

再次访问 http://127.0.0.1:8000/runoob，可以看到页面：

date

根据给定格式对一个日期变量进行格式化。

格式 Y-m-d H:i:s返回 年-月-日 小时:分钟:秒 的格式时间。


## HelloWorld/HelloWorld/views.py 文件代码：


## HelloWorld/templates/runoob.html 文件代码：

```text
{{ time|date:"Y-m-d" }}
```

再次访问 http://127.0.0.1:8000/runoob，可以看到页面：

truncatechars

如果字符串包含的字符总个数多于指定的字符数量，那么会被截断掉后面的部分。

截断的字符串将以 ... 结尾。


## HelloWorld/HelloWorld/views.py 文件代码：


## 后续章节

- HelloWorld/templates/runoob.html 文件代码：
- HelloWorld/HelloWorld/views.py 文件代码：
- HelloWorld/templates/runoob.html 文件代码：
- if/else 标签
- HelloWorld/HelloWorld/views.py 文件代码：
- HelloWorld/templates/runoob.html 文件代码：
- for 标签
- HelloWorld/HelloWorld/views.py 文件代码：
- HelloWorld/templates/runoob.html 文件代码：
- HelloWorld/templates/runoob.html 文件代码：
- HelloWorld/HelloWorld/views.py 文件代码：
- HelloWorld/templates/runoob.html 文件代码：
- HelloWorld/HelloWorld/views.py 文件代码：
- HelloWorld/templates/runoob.html 文件代码：
- HelloWorld/HelloWorld/views.py 文件代码：
- HelloWorld/templates/runoob.html 文件代码：

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Django 模板` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
