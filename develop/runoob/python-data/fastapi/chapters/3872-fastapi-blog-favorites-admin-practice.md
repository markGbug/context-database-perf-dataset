# FastAPI：收藏功能与后台管理

- 来源：[收藏功能与后台管理](https://www.runoob.com/fastapi/fastapi-blog-favorites-admin.html)
- 分类：Python / 数据科学
- 技术：FastAPI
- 笔记类型：练习笔记
- 章节序号：3872

## 本章内容

本章你将学会用多对多关系实现收藏功能，并用 sqladmin 搭建后台管理。


## 多对多关系设计


## 实例

执行迁移：

```text
(venv) $ alembic revision --autogenerate -m "新增收藏关联表"
(venv) $ alembic upgrade head
```


## 收藏与取消收藏路由


## 实例


## 在详情页添加收藏按钮


## 实例


## sqladmin — 后台管理

sqladmin 是 FastAPI 生态中对标 Django Admin 的后台管理扩展。

它专为 SQLAlchemy 设计，与 FastAPI 无缝集成。

```text
(venv) $ pip install sqladmin
```


## 实例

访问 /admin 进入后台管理界面。


### sqladmin vs Flask-Admin vs Django Admin

sqladmin 默认不需要登录就能访问。生产环境需要配置 authentication_backend 来添加认证保护，详见 sqladmin 官方文档。


## 本章小结

本章你实现了两个重要功能：用 Table 关联表实现收藏的多对多关系；用 sqladmin 快速搭建后台管理系统。

现在博客的用户交互（注册、登录、收藏）和管理功能（Admin 后台）都已完备。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `收藏功能与后台管理` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
