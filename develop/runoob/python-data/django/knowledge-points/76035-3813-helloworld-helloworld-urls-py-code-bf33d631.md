# 知识点 76035：Django：Django 表单 - /HelloWorld/HelloWorld/urls.py 文件代码：

- 来源：[Django 表单](https://www.runoob.com/django/django-form.html)
- 来源章节：[3813-django-form-study.md](../chapters/3813-django-form-study.md)
- 分类：Python / 数据科学
- 技术：Django
- 所在小节：/HelloWorld/HelloWorld/urls.py 文件代码：
- 知识类型：代码
- 原章节序号：3813

## 原文片段

```text
from django.conf.urls import url
from . import views,testdb,search

urlpatterns = [
    url(r'^hello/$', views.runoob),
    url(r'^testdb/$', testdb.testdb),
    url(r'^search-form/$', search.search_form),
    url(r'^search/$', search.search),
]
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `/HelloWorld/HelloWorld/urls.py 文件代码：` 这一小节和 `Django 表单` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
