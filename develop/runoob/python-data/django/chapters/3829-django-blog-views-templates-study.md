# Django：视图与模板 — 渲染文章列表

- 来源：[视图与模板](https://www.runoob.com/django/django-blog-views-templates.html)
- 分类：Python / 数据科学
- 技术：Django
- 笔记类型：学习笔记
- 章节序号：3829

## 本章内容

本章你将学会用 Django 视图从数据库取数据，配合模板渲染出博客首页的文章卡片列表。


## 视图（View）的作用

视图是 Django 的核心逻辑层，负责：

- 接收用户请求（request 参数）
- 从数据库查询需要的数据
- 将数据传给模板渲染 HTML，返回给用户

Django 视图有两种写法：函数视图（FBV） 和类视图（CBV）。

前八章我们优先使用 FBV——它更直观，适合初学者理解请求处理流程。


## 函数视图基础

一个 Django 视图函数接收 request 参数，返回 HttpResponse 对象。


## 实例

render() 是 Django 中最常用的快捷函数，它组合了：加载模板 → 注入数据 → 生成 HTML → 返回响应。


## Django 模板语法

Django 模板语法与 Vue3 模板语法非常相似，但有一些关键区别。

关键区别：Django 模板用 {% %} 包裹控制标签，Vue3 用 v- 指令。Django 模板在服务器端渲染——HTML 生成完毕后才发给浏览器；Vue3 在浏览器端渲染——浏览器收到 JS 后才拼接 HTML。


## 模板继承：base.html

多个页面共享相同的导航栏和页脚，用 模板继承 避免重复。

父模板定义「块（block）」，子模板填充具体内容。


### 创建 base.html 父模板


## 实例


### 创建 index.html 子模板


## 实例

模板中用到的几个知识点：

Django 模板中的 过滤器 用管道符 | 表示，跟在变量后面，用于格式化输出。常用过滤器：date、truncatechars、length、default。


## 添加文章列表样式

在 base.html 的 style 标签中追加以下 CSS：


## 实例


## 动手：验证首页效果

确认以下几点已做好：

- models.py 中定义了 Post 和 Category 模型，并已 migrate
- Admin 后台已录入至少 3-5 篇文章（归属于不同的分类）
- views.py 中的 index 函数从数据库查询文章并传给模板
- urls.py 中 / 路由指向 index 视图

启动服务器，访问首页，应该能看到由数据库数据动态渲染的文章卡片列表。


## 本章小结

本章你掌握了 Django 视图和模板的核心配合：views.py 从数据库查询数据并传入 context、render() 渲染模板、base.html 父模板定义布局 + block、子模板 extends 继承并填充内容、Django 模板语法（{{ }}、{% %}、过滤器）。

现在博客首页由数据库驱动，不再硬编码。


## 复习重点

- 能说明 `视图与模板` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
