# Flask：收藏功能与后台管理

- 来源：[收藏功能与后台管理](https://www.runoob.com/flask/flask-blog-favorites-admin.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：学习笔记
- 章节序号：3925

## 本章内容

本章你将学会用多对多关系实现收藏功能，并用 Flask-Admin 快速搭建后台管理。


## 多对多关系设计

收藏功能的需求：一个用户可以收藏多篇文章，一篇文章可以被多个用户收藏。

在 SQLAlchemy 中，多对多关系通过关联表（Association Table）实现。


## 实例

然后执行迁移：

```text
(venv) $ flask db migrate -m "新增收藏关联表"
(venv) $ flask db upgrade
```


## 收藏与取消收藏视图


## 实例


### 在 app.py 中注册 Blueprint


## 实例


## 在详情页和列表页添加收藏按钮


## 实例

收藏操作用 POST 请求（form 提交），而非 GET 链接。GET 请求不应该产生副作用（修改数据库），这是 Web 开发的基本原则。


## Flask-Admin — 后台管理

Flask-Admin 是 Flask 生态中对标 Django Admin 的扩展。

配置后，你可以在浏览器中管理文章和分类数据。

```text
(venv) $ pip install flask-admin
```


## 实例

启动服务器，访问 /admin，即可进入后台管理界面。


### Flask-Admin vs Django Admin

Flask-Admin 默认不需要登录就能访问，需要结合 Flask-Login 加权限控制。一个简单的方式是在视图函数前加 @login_required，或者覆盖 ModelView 的 is_accessible 方法检查管理员权限。


## 本章小结

本章你实现了两个重要功能：用 db.Table 关联表 + db.session.execute 操作实现收藏的多对多关系；用 Flask-Admin 快速搭建后台管理系统。

现在博客的交互功能（用户、收藏）和管理功能（后台）都已完备。


## 复习重点

- 能说明 `收藏功能与后台管理` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
