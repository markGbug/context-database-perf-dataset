# Django：表单与收藏功能

- 来源：[表单与收藏功能](https://www.runoob.com/django/django-blog-forms-favorites.html)
- 分类：Python / 数据科学
- 技术：Django
- 笔记类型：练习笔记
- 章节序号：3833

## 本章内容

本章你将学会处理用户 POST 请求，建立多对多关系，并实现「收藏文章」功能。


## 收藏功能的数据模型设计

收藏功能的核心是：一个用户可以收藏多篇文章，一篇文章可以被多个用户收藏。

这是典型的多对多（ManyToMany）关系。

我们不需要新建模型——Django 的 User 模型是内置的，只需要在 Post 模型中添加一个 ManyToManyField 指向 User。


## 实例

修改模型后，生成并执行迁移：

```text
(venv) $ python manage.py makemigrations
(venv) $ python manage.py migrate
```


## 收藏与取消收藏的视图逻辑


## 实例


### ManyToMany 操作方法速查


## 配置收藏路由


## 实例


## 在详情页添加收藏按钮


## 实例

在首页文章卡片中也加入收藏按钮：


## 实例

为什么收藏按钮用 form 而不是 a 标签？因为收藏操作修改了数据库，属于 POST 请求。按照 REST 规范，读操作用 GET，写操作用 POST。更重要的是，POST 请求携带 csrf_token，防止恶意网站伪造请求。


## 收藏列表页面

为登录用户展示已收藏的文章列表。


## 实例

在 urls.py 中添加路由，在导航栏添加「我的收藏」链接。


## 收藏按钮样式


## 实例


## 本章小结

本章你掌握了 Django 中的用户交互处理：ManyToManyField 建立多对多关系、POST 请求处理表单、csrf_token 安全防护、login_required 装饰器保护视图、request.user 判断当前用户身份。

收藏功能让用户可以标记喜欢的文章，并在个人收藏列表中查看。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `表单与收藏功能` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
