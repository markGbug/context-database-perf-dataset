# Django：Django cookie 与 session

- 来源：[Django Cookie/Session](https://www.runoob.com/django/django-cookie-session.html)
- 分类：Python / 数据科学
- 技术：Django
- 笔记类型：学习笔记
- 章节序号：3822

## 本章内容

Cookie 是存储在客户端计算机上的文本文件，并保留了各种跟踪信息。

识别返回用户包括三个步骤：

- 服务器脚本向浏览器发送一组 Cookie。例如：姓名、年龄或识别号码等。
- 浏览器将这些信息存储在本地计算机上，以备将来使用。
- 当下一次浏览器向 Web 服务器发送任何请求时，浏览器会把这些 Cookie 信息发送到服务器，服务器将使用这些信息来识别用户。

HTTP 是一种"无状态"协议，这意味着每次客户端检索网页时，客户端打开一个单独的连接到 Web 服务器，服务器会自动不保留之前客户端请求的任何记录。

但是仍然有以下三种方式来维持 Web 客户端和 Web 服务器之间的 session 会话：


## Cookies

一个 Web 服务器可以分配一个唯一的 session 会话 ID 作为每个 Web 客户端的 cookie，对于客户端的后续请求可以使用接收到的 cookie 来识别。

在Web开发中，使用 session 来完成会话跟踪，session 底层依赖 Cookie 技术。


### Django 中 Cookie 的语法

设置 cookie:

```text
rep.set_cookie(key,value,...)
rep.set_signed_cookie(key,value,salt='加密盐',...)
```

获取 cookie:

```text
request.COOKIES.get(key)
```

删除 cookie:

```text
rep =HttpResponse || render || redirect
rep.delete_cookie(key)
```


### 创建应用和模型


## models.py


## urls.py


## views.py

以下创建三个模板文件：login.html、index.html、order.html。


## login.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>

<h3>用户登录</h3>
<form action="" method="post">
    {% csrf_token %}
    <p>用户名： <input type="text" name="username"></p>
    <p>密码： <input type="password" name="pwd"></p>
    <input type="submit">
</form>


</body>
</html>
```


## index.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>


<h2>index 页面。。。</h2>


<a href="/logout/">注销</a>

</body>
</html>
```


## order.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>


<h2>order 页面。。。</h2>


<a href="/logout/">注销</a>

</body>
</html>
```

运行结果如下图所示：


## Session(保存在服务端的键值对)

服务器在运行时可以为每一个用户的浏览器创建一个其独享的 session 对象，由于 session 为用户浏览器独享，所以用户在访问服务器的 web 资源时，可以把各自的数据放在各自的 session 中，当用户再去访问该服务器中的其它 web 资源时，其它 web 资源再从用户各自的 session 中取出数据为用户服务。


### 工作原理

- a. 浏览器第一次请求获取登录页面 login。
- b. 浏览器输入账号密码第二次请求，若输入正确，服务器响应浏览器一个 index 页面和一个键为 sessionid，值为随机字符串的 cookie，即 set_cookie ("sessionid",随机字符串)。
- c. 服务器内部在 django.session 表中记录一条数据。 django.session 表中有三个字段。 session_key：存的是随机字符串，即响应给浏览器的 cookie 的 sessionid 键对应的值。 session_data：存的是用户的信息，即多个 request.session["key"]=value，且是密文。 expire_date：存的是该条记录的过期时间（默认14天）
- d. 浏览器第三次请求其他资源时，携带 cookie :{sessionid:随机字符串}，服务器从 django.session 表中根据该随机字符串取出该用户的数据，供其使用（即保存状态）。

注意: django.session 表中保存的是浏览器的信息，而不是每一个用户的信息。 因此， 同一浏览器多个用户请求只保存一条记录（后面覆盖前面）,多个浏览器请求才保存多条记录。

cookie 弥补了 http 无状态的不足，让服务器知道来的人是"谁"，但是 cookie 以文本的形式保存在浏览器端，安全性较差，且最大只支持 4096 字节，所以只通过 cookie 识别不同的用户，然后，在对应的 session 里保存私密的信息以及超过 4096 字节的文本。

session 设置：

```text
request.session["key"] = value
```

执行步骤：

- a. 生成随机字符串
- b. 把随机字符串和设置的键值对保存到 django_session 表的 session_key 和 session_data 里
- c. 设置 cookie：set_cookie("sessionid",随机字符串) 响应给浏览器

session 获取：

```text
request.session.get('key')
```

执行步骤：

- a. 从 cookie 中获取 sessionid 键的值，即随机字符串。
- b. 根据随机字符串从 django_session 表过滤出记录。
- c. 取出 session_data 字段的数据。

session 删除，删除整条记录（包括 session_key、session_data、expire_date 三个字段）：

```text
request.session.flush()
```

删除 session_data 里的其中一组键值对：

```text
del request.session["key"]
```

执行步骤：

- a. 从 cookie 中获取 sessionid 键的值，即随机字符串
- b. 根据随机字符串从 django_session 表过滤出记录
- c. 删除过滤出来的记录


### 实例

创建路由:


## urls.py


## 复习重点

- 能说明 `Django Cookie/Session` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
