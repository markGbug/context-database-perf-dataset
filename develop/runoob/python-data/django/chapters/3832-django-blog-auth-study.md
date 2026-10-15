# Django：用户系统 — 注册、登录、登出

- 来源：[用户系统](https://www.runoob.com/django/django-blog-auth.html)
- 分类：Python / 数据科学
- 技术：Django
- 笔记类型：学习笔记
- 章节序号：3832

## 本章内容

本章你将学会使用 Django 内置的认证系统，实现用户注册、登录和登出功能。


## Django 内置 auth 系统

Django 自带一套完整的用户认证模块：

- 内置 User 模型（用户名、密码、邮箱等）
- 内置登录/登出视图（无需自己写逻辑）
- 内置的权限和组管理
- 表单验证和安全防护（CSRF、XSS）

这个模块是 django.contrib.auth，在创建项目时已经默认注册到了 INSTALLED_APPS。


## 注册页面

Django 内置了登录/登出视图，但没有内置注册视图，需要我们自己写。


### 第一步：创建注册表单


## 实例


### 第二步：编写注册视图


## 实例

Django 的 messages 框架用于在请求之间传递一次性消息（如「注册成功」）。在模板中渲染 messages 区域，用户就能看到操作反馈。它和 session 配合使用，消息显示一次后自动消失。


## 登录与登出

Django 内置了登录和登出视图，只需在路由中引入即可。


## 实例

在 settings.py 中配置登录登出的跳转地址：


## 实例


## 创建认证相关模板


### 登录模板


## 实例


### 注册模板


## 实例

{% csrf_token %} 是 Django 的安全机制，防止跨站请求伪造攻击。任何 POST 表单必须包含它，否则 Django 会拒绝请求（403 错误）。这个标签会生成一个隐藏的 input，包含随机的 CSRF token。


## 在导航栏显示登录状态

更新 base.html 的导航栏，根据登录状态显示不同内容。


## 实例

Django 的模板上下文处理器会自动将 {{ user }} 注入到每个模板中，无需在 views.py 中手动传递。你可以通过 user.is_authenticated 判断用户是否登录。


## 登录页面样式


## 实例


## 本章小结

本章你接入了 Django 内置认证系统：继承了 UserCreationForm 创建注册表单、使用 LoginView/LogoutView 实现登录登出、用 csrf_token 保护 POST 请求、在模板中使用 user.is_authenticated 判断登录状态。

现在博客有了完整的用户注册、登录、登出流程。


## 复习重点

- 能说明 `用户系统` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
