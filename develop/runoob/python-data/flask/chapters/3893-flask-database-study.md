# Flask：Flask 数据库集成

- 来源：[Flask 数据库集成](https://www.runoob.com/flask/flask-database.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：学习笔记
- 章节序号：3893

## 本章内容

大多数 Web 应用都需要持久化存储数据。

本章使用 Python 内置的 SQLite 数据库，展示如何在 Flask 中集成数据库，无需安装额外依赖。


## SQLite 快速入门

SQLite 是一个轻量级数据库，数据存储在一个文件中，Python 标准库自带支持。

它是学习和原型开发的最佳选择——无需安装数据库服务器，无需配置。


## 实例


## 在 Flask 中使用 g 对象管理数据库连接

g 是一个特殊的对象，它的生命周期是单个请求。

将数据库连接存入 g，可以确保同一请求内的多次数据库操作共享同一连接，请求结束后自动清理。


## 实例


## 工厂模式整合

使用工厂模式将数据库与其他模块整合：


## 实例


## 写一个完整的博客 API

结合数据库，实现文章的增删改查（CRUD）操作：


## 实例

测试 API：

```text
# 获取文章列表
$ curl http://127.0.0.1:5000/api/posts

# 创建文章
$ curl -X POST http://127.0.0.1:5000/api/posts \
  -H "Content-Type: application/json" \
  -d '{"title":"RUNOOB 教程","body":"Flask 入门教程内容","author_id":1}'

# 更新文章
$ curl -X PUT http://127.0.0.1:5000/api/posts/1 \
  -H "Content-Type: application/json" \
  -d '{"title":"RUNOOB 教程（修订版）","body":"更新后的内容"}'

# 删除文章
$ curl -X DELETE http://127.0.0.1:5000/api/posts/1
```

最佳实践：API 返回 JSON 数据时，使用正确的 HTTP 状态码——创建用 201，成功用 200，客户端错误用 400，资源不存在用 404。这能让前端代码更容易判断请求结果。


## 数据库初始化命令

通过 Flask CLI 可以创建自定义命令来初始化数据库：

```text
# 初始化数据库（创建表结构）
(.venv) $ flask init-db

# 验证表已创建
(.venv) $ sqlite3 instance/runoob.db ".tables"
post  user
```


## SQL 注入防护

使用参数化查询（? 占位符）是防止 SQL 注入的关键：


## 实例


## 使用 Flask-SQLAlchemy（进阶选读）

对于大型项目，手动写 SQL 会逐渐变得繁琐。

Flask-SQLAlchemy 是一个广受欢迎的扩展，提供了 ORM（对象关系映射）能力：


## 实例

本章使用原生 SQLite 是为了不引入额外依赖，适合学习和小型项目。对于实际生产项目，建议使用 SQLAlchemy 或类似 ORM，能显著减少重复代码并提升安全性。


## 复习重点

- 能说明 `Flask 数据库集成` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
