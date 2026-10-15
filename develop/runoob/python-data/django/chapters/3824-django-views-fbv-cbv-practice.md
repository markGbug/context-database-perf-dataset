# Django：Django 视图 - FBV 与 CBV

- 来源：[Django 视图 - FBV 与 CBV](https://www.runoob.com/django/django-views-fbv-cbv.html)
- 分类：Python / 数据科学
- 技术：Django
- 笔记类型：练习笔记
- 章节序号：3824

## 本章内容

FBV（function base views） 基于函数的视图，就是在视图里使用函数处理请求。

CBV（class base views） 基于类的视图，就是在视图里使用类处理请求。


### FBV

基于函数的视图其实我们前面章节一直在使用，就是使用了函数来处理用户的请求，查看以下实例：

路由配置：


## urls.py 文件


## views.py 文件

如果我们在浏览器中直接访问 http://127.0.0.1:8000/login/ ，输出结果为：

```text
GET 方法
```


### CBV

基于类的视图，就是使用了类来处理用户的请求，不同的请求我们可以在类中使用不同方法来处理，这样大大的提高了代码的可读性。

定义的类要继承父类 View，所以需要先引入库：

```text
from django.views import View
```

执行对应请求的方法前会优先执行 dispatch 方法(在get/post/put...方法前执行)，dispatch() 方法会根据请求的不同调用相应的方法来处理。

其实，在我们前面学到的知识都知道 Django 的 url 是将一个请求分配给可调用的函数的，而不是一个类，那是如何实现基于类的视图的呢？ 主要还是通过父类 View 提供的一个静态方法 as_view() ，as_view 方法是基于类的外部接口， 他返回一个视图函数，调用后请求会传递给 dispatch 方法，dispatch 方法再根据不同请求来处理不同的方法。

路由配置：


## urls.py 文件


## views.py 文件

如果我们在浏览器中直接访问 http://127.0.0.1:8000/login/ ，输出结果为：

```text
GET 方法
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Django 视图 - FBV 与 CBV` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
