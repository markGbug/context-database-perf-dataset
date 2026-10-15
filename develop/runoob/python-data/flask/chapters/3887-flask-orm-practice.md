# Flask：Flask 数据库操作

- 来源：[Flask 数据库操作](https://www.runoob.com/flask/flask-orm.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：练习笔记
- 章节序号：3887

## 本章内容

在 Flask 中，数据库操作是构建 Web 应用的一个重要方面。

Flask 提供了多种方式来与数据库进行交互，包括直接使用 SQL 和利用 ORM（对象关系映射）工具，如 SQLAlchemy。

以下是对 Flask 数据库操作的详细说明，包括使用 SQLAlchemy 的基本操作和 SQL 语句的直接执行。

- 使用 SQLAlchemy：定义模型，配置数据库，执行基本的 CRUD 操作。
- 创建和管理数据库：使用 db.create_all() 创建表。
- CRUD 操作：添加、读取、更新和删除记录。
- 查询操作：执行基本和复杂查询，包括排序和分页。
- Flask-Migrate：使用 Flask-Migrate 管理数据库迁移。
- 执行原始 SQL：使用原始 SQL 语句进行数据库操作。


## 1. 使用 SQLAlchemy

SQLAlchemy 是一个强大的 ORM 库，可以简化数据库操作，通过 Python 对象与数据库表进行交互。

Flask-SQLAlchemy 是 Flask 的一个扩展，用于集成 SQLAlchemy。


### 安装 Flask-SQLAlchemy

```text
pip install flask-sqlalchemy
```


### 配置 SQLAlchemy

app.py 文件代码：


## 实例


## 2. 定义模型

模型是数据库表的 Python 类，每个模型类代表数据库中的一张表。


## 实例

db.Model：所有模型类需要继承自 db.Model。

db.Column：定义模型的字段，指定字段的类型、是否为主键、是否唯一、是否可以为空等属性。


## 3. 创建和管理数据库


### 创建数据库和表

在定义了模型后，你可以使用 SQLAlchemy 提供的方法来创建数据库和表。

```text
with app.app_context():
    db.create_all()
```

db.create_all()：创建所有在当前上下文中定义的模型对应的表。


## 4. 基本的 CRUD 操作


### 创建记录


## 实例

db.session.add(new_user)：将新用户对象添加到会话中。

db.session.commit()：提交事务，将更改保存到数据库。


### 读取记录


## 实例

User.query.all()：查询所有用户记录。


### 更新记录


## 实例

User.query.get(user_id)：通过主键查询单个用户记录。

更新字段值并提交事务。


### 删除记录


## 实例

db.session.delete(user)：删除用户记录，并提交事务。


## 5. 查询操作

SQLAlchemy 提供了丰富的查询功能，可以通过查询对象来执行各种查询操作。


### 基本查询

```text
users = User.query.filter_by(username='john_doe').all()
```

filter_by()：根据字段值过滤记录。


### 复杂查询

```text
from sqlalchemy import or_

users = User.query.filter(or_(User.username == 'john_doe', User.email == 'john@example.com')).all()
```

or_()：用于执行复杂的查询条件。


### 排序和分页

```text
users = User.query.order_by(User.username).paginate(page=1, per_page=10)
```

order_by()：按指定字段排序。

paginate()：分页查询。


## 6. 使用 Flask-Migrate 进行迁移

Flask-Migrate 是一个用于数据库迁移的扩展，基于 Alembic，可以帮助你管理数据库的版本控制。


### 安装 Flask-Migrate

```text
pip install flask-migrate
```


### 配置 Flask-Migrate

app.py 文件代码：

```text
from flask_migrate import Migrate

migrate = Migrate(app, db)
```


## 后续章节

- 初始化迁移
- 创建迁移脚本
- 应用迁移
- 7. 执行原始 SQL
- 实例
- Flask 中连接和操作 MySQL 数据库
- 1. 使用 Flask-SQLAlchemy 连接 MySQL
- 配置 Flask-SQLAlchemy
- 实例
- 定义模型和执行基本操作
- 实例
- 直接使用 MySQL 的 Python 驱动
- 实例
- 实例

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Flask 数据库操作` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
