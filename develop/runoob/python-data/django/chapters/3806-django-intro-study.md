# Django：Django 简介

- 来源：[Django 简介](https://www.runoob.com/django/django-intro.html)
- 分类：Python / 数据科学
- 技术：Django
- 笔记类型：学习笔记
- 章节序号：3806

## 本章内容

Django 是一个由 Python 编写的一个开放源代码的 Web 应用框架。

使用 Django，只要很少的代码，Python 的程序开发人员就可以轻松地完成一个正式网站所需要的大部分内容，并进一步开发出全功能的 Web 服务。

Django 提供了全栈开发所需的工具，包括数据库 ORM、模板引擎、路由系统、用户认证等，大幅减少重复代码。

Django 的哲学:

- DRY（Don't Repeat Yourself）: 避免重复代码，提倡复用（如模板继承、模型继承）。
- 约定优于配置: 默认提供合理配置（如自动生成 Admin 界面），减少决策成本。
- 快速开发: 从原型到生产环境均可高效推进。

Django 遵循 MVC（Model-View-Controller）架构，但在 Django 中更常被称为 MTV（Model-Template-View）。


### 内置功能


## 核心特点

- 快速开发：Django 提供了大量内置功能，如认证、管理后台、表单处理等，让开发者专注于业务逻辑，而非底层实现。
- 自动化管理后台：只需简单的模型定义，即可生成强大的后台管理界面，支持增删改查。
- ORM 数据库映射：Django 内置 ORM (Object-Relational Mapping)，可以让开发者使用 Python 类与数据库交互，无需编写 SQL。
- 强大的 URL 路由：使用正则表达式灵活定义 URL，轻松实现页面路由。
- 模板引擎：内置强大的模板系统，支持逻辑判断、循环处理，方便渲染 HTML 页面。
- 国际化支持：Django 支持多语言国际化，非常适合全球化应用。
- 高安全性：内置多种安全保护措施，如防止 SQL 注入、XSS 攻击、CSRF 攻击等。
- 丰富的社区与扩展：大量开源的第三方库，如 Django REST framework、Django CMS 等，快速扩展功能。


## MVC 与 MTV模型


### MVC (Model-View-Controller)

- Model (模型)：处理与数据库的交互，定义数据的结构和业务逻辑。
- View (视图)：负责数据展示，生成用户看到的 HTML 页面。
- Controller (控制器)：接收用户请求，调用 Model 处理数据，并将结果传递给 View 渲染页面。

流程：

- 用户发送请求到 Controller。
- Controller 处理逻辑，调用 Model 获取数据。
- Controller 将数据传递给 View。
- View 渲染并返回 HTML 页面给用户。


### MVT (Model-Template-View) —— Django 的实现方式

Django 中采用了 MVT 设计模式，类似于 MVC，但有一些区别：

- Model (模型)：与数据库交互，处理数据的创建、读取、更新、删除。
- Template (模板)：负责页面渲染，生成最终的 HTML 内容。
- View (视图)：Django 的 View 更偏向于控制器的角色，接收请求并决定使用哪个模板和数据。

流程：

- 用户访问 URL，请求被 Django 的 urls.py 映射到相应的 View。
- View 处理业务逻辑，调用 Model 获取数据。
- View 将数据传递给 Template。
- Template 渲染 HTML，最终返回给用户。


## Django 的适用场景

适合用 Django 的项目:

- ✅ 内容管理系统（CMS）（如新闻网站、博客）
- ✅ 社交平台（用户系统、动态发布）
- ✅ 电子商务网站（订单管理、支付集成）
- ✅ API 后端（结合 Django REST framework）

不适合的场景:

- ❌ 超高性能要求的实时系统（如高频交易平台，推荐 Go 或 Rust）
- ❌ 极度轻量级的微服务（可以考虑 Flask 或 FastAPI）


## Django vs 其他框架

Django 优势：

- "开箱即用"：无需额外安装插件即可实现完整功能。
- 安全性：自动防范 SQL 注入、XSS、CSRF 等常见攻击。
- 社区活跃：丰富的第三方库（如 Django REST framework、Django CMS）。


## 复习重点

- 能说明 `Django 简介` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
