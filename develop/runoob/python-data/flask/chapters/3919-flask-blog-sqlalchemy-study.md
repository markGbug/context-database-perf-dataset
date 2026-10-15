# Flask：Flask-SQLAlchemy — 设计数据库模型

- 来源：[Flask-SQLAlchemy](https://www.runoob.com/flask/flask-blog-sqlalchemy.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：学习笔记
- 章节序号：3919

## 本章内容

本章你将学会用 Flask-SQLAlchemy 定义数据模型，创建 SQLite 数据库表，并插入测试数据。


## 为什么要用 ORM？

直接写 SQL 语句操作数据库繁琐且容易出错。

ORM（对象关系映射） 让你用 Python 类来定义表结构，用 Python 方法操作数据。

Flask-SQLAlchemy 是 SQLAlchemy 的 Flask 集成版，封装了常见操作，配置更简单。


## 安装与配置

```text
(venv) $ pip install flask-sqlalchemy
```


## 实例

sqlite:///blog.db 中的三个斜杠表示相对路径。SQLite 数据库就是一个文件，无需安装任何数据库软件，非常适合开发和测试。


## 定义模型：Post 和 Category


## 实例


### 常用字段类型


## 创建数据库表

与 Django 的 migrate 不同，Flask 需要手动初始化数据库表。

```text
(venv) $ flask shell                        # 进入 Flask 交互式 Shell
```


## 实例

执行后，项目根目录下会生成 blog.db 文件。

db.create_all() 只在表不存在时才创建。如果修改了模型结构（如新增字段），它不会自动更新表。生产环境中应该用 Flask-Migrate（第五章）管理结构变更。


## 用 flask shell 插入测试数据


## 实例


### Flask-SQLAlchemy 基础查询


## 本章小结

本章你掌握了 Flask-SQLAlchemy 的完整流程：安装并配置 SQLALCHEMY_DATABASE_URI、db.Model 定义模型（字段类型/外键/relationship）、db.create_all() 初始化建表、flask shell 中插入与查询数据。

至此，文章和分类的数据结构已在 SQLite 数据库中建立。


## 复习重点

- 能说明 `Flask-SQLAlchemy` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
