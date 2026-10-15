# Django：Django Admin — 后台管理文章

- 来源：[Django Admin](https://www.runoob.com/django/django-blog-admin.html)
- 分类：Python / 数据科学
- 技术：Django
- 笔记类型：学习笔记
- 章节序号：3828

## 本章内容

本章你将学会配置 Django Admin，无需写前端代码就能拥有内容管理后台。


## Admin 是什么？

Django Admin 是 Django 最强大的内置功能之一：你只需注册模型，它就自动生成一个完整的后台管理系统。

后台提供文章的增删改查、搜索、过滤、分页等功能，无需你自己写任何 CRUD 代码。


## 创建超级用户

首先需要创建一个管理员账号来登录后台：

```text
(venv) $ python manage.py createsuperuser
用户名：admin
电子邮件地址：admin@runoob.com
Password:        # 输入密码（不会回显）
Password (again): # 重复密码
Superuser created successfully.
```

启动服务器后访问 http://127.0.0.1:8000/admin/，用刚才创建的账号登录。

```text
(venv) $ python manage.py runserver
```


## 注册模型到 Admin

打开 blog/admin.py，注册 Post 和 Category 模型。


## 实例


### admin.py 关键配置说明

刷新后台页面，点击左侧「文章」，可以看到完整的列表、过滤、搜索功能。


## 通过 Admin 录入测试数据

点击「增加 文章」按钮，在表单中填入标题、摘要、正文内容。

分类字段会自动从已创建的 Category 中拉取选项（因为设置的是 ForeignKey）。

录入至少 5 篇文章，覆盖不同的分类，方便后续章节展示列表和筛选效果。

Admin 的表单字段顺序与 models.py 中字段的定义顺序一致。如果想调整顺序，可以在 Admin 类中设置 fields = ['title', 'category', ...] 显式指定排列。


## 富文本编辑（可选扩展）

默认的正文输入框是纯文本框，输入 HTML 不太方便。

可以安装 django-summernote 来获得所见即所得的富文本编辑器：

```text
(venv) $ pip install django-summernote
```


## 实例

然后在 Admin 中将 content 字段改为 Summernote 编辑器：


## 实例

现在编辑文章时，正文区域是一个完整的富文本编辑器，可以排版、插图、调整格式。

django-summernote 是可选的。如果不想安装第三方库，继续在纯文本框中写 HTML 也完全可以。本教程后续的代码与是否安装 Summernote 无关。


## 中文化 Admin 界面

如果在 settings.py 中设置了 LANGUAGE_CODE = 'zh-hans'，Admin 界面已经自动切换为中文。

模型定义中的 verbose_name 参数会用于 Admin 表单的字段标签。


## 本章小结

本章你配置了 Django Admin 后台：创建超级用户、注册模型、配置列表展示/搜索/过滤、可选接入富文本编辑器。

现在你可以在浏览器中直观地管理文章内容，不再需要进 Shell 手动录数据。


## 复习重点

- 能说明 `Django Admin` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
