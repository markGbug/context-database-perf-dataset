# Django：Django 用户认证（Auth）组件

- 来源：[Django Auth](https://www.runoob.com/django/django-auth.html)
- 分类：Python / 数据科学
- 技术：Django
- 笔记类型：学习笔记
- 章节序号：3821

## 本章内容

Django 用户认证（Auth）组件一般用在用户的登录注册上，用于判断当前的用户是否合法，并跳转到登陆成功或失败页面。

Django 用户认证（Auth）组件需要导入 auth 模块:

```text
# 认证模块
from django.contrib import auth

# 对应数据库
from django.contrib.auth.models import User
```

返回值是用户对象。

创建用户对象的三种方法：

- create()：创建一个普通用户，密码是明文的。
- create_user()：创建一个普通用户，密码是密文的。
- create_superuser()：创建一个超级用户，密码是密文的，要多传一个邮箱 email 参数。

参数：

- username: 用户名。
- password：密码。
- email：邮箱 (create_superuser 方法要多加一个 email)。

```text
from django.contrib.auth.models import User
User.objects.create(username='runboo',password='123')
```

```text
from django.contrib.auth.models import User
User.objects.create_user(username='runbooo',password='123')
```

```text
from django.contrib.auth.models import User
User.objects.create_superuser(username='runboooo',password='123',email='runboo@163.com')
```

验证用户的用户名和密码使用 authenticate() 方法，从需要 auth_user 表中过滤出用户对象。

使用前要导入：

```text
from django.contrib import auth
```


## 实例

给验证成功的用户加 session，将 request.user 赋值为用户对象。

使用前要导入：

```text
from django.contrib import auth
```

参数：

- request：用户对象

返回值：None


## 实例

注销用户使用 logout() 方法，需要清空 session 信息，将 request.user 赋值为匿名用户。

使用前要导入：

```text
from django.contrib import auth
```

参数：

- request：用户对象

返回值：None


## 实例

设置装饰器，给需要登录成功后才能访问的页面统一加装饰器。

使用前要导入：

```text
from django.contrib.auth.decorators import login_required
```


## 实例

设置从哪个页面访问，登录成功后就返回哪个页面。

解析：

django 在用户访问页面时，如果用户是未登录的状态，就给用户返回登录页面。

此时，该登录页面的 URL 后面有参数：next=用户访问的页面的 URL。

因此，设置在用户登录成功后重定向的 URL 为 next 参数的值。

但是，若用户一开始就输入登录页面 logi，request.GET.get("next") 就取不到值，所以在后面加 or，可以设置自定义返回的页面。


## 实例


## 复习重点

- 能说明 `Django Auth` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
