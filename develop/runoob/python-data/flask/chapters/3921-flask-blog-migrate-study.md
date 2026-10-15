# Flask：Flask-Migrate — 数据库迁移

- 来源：[Flask-Migrate](https://www.runoob.com/flask/flask-blog-migrate.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：学习笔记
- 章节序号：3921

## 本章内容

本章你将学会用 Flask-Migrate 安全地管理数据库结构变更，并理解与 Django migration 的对应关系。


## 为什么不能一直用 db.create_all()？

db.create_all() 有两个致命缺陷：

- 只在表不存在时创建。修改模型（如新增字段），已存在的表不会更新
- 不保留变更历史。无法回滚到之前的数据库状态

数据库迁移 就像数据库的 Git——每次结构变更生成一个版本文件，支持升级和回滚。

Flask-Migrate 是 Alembic 的 Flask 扩展，专为 SQLAlchemy 设计。


## 安装与配置

```text
(venv) $ pip install flask-migrate
```


## 实例


## 迁移三步曲


### 第一步：初始化迁移目录

```text
(venv) $ flask db init
Creating directory migrations/...  done
```

执行后生成 migrations/ 目录（类似 Git 的 .git 目录），只需执行一次。


### 第二步：生成迁移文件

```text
(venv) $ flask db migrate -m "初始化 Post 和 Category 模型"
INFO  [alembic.runtime.migration] Context impl SQLiteImpl.
Generating migrations/versions/xxxx_initial.py ... done
```

如果你还没有任何模型变更，直接在已有模型上执行这条命令即可。


### 第三步：执行迁移

```text
(venv) $ flask db upgrade
INFO  [alembic.runtime.migration] Running upgrade  -> xxxx, 初始化
```


## 实战：给 Post 模型新增字段

假设产品需求变更，需要给文章添加一个阅读计数。


## 实例

修改模型后，执行迁移：

```text
(venv) $ flask db migrate -m "Post 模型新增 read_count 字段"
(venv) $ flask db upgrade
```

现在数据库中 posts 表自动增加了 read_count 列，已有数据不受影响。


### 查看迁移历史

查看当前数据库处于哪个版本：

```text
(venv) $ flask db current
```

查看所有迁移历史：

```text
(venv) $ flask db history
```


## 回滚迁移

迁移是可以撤销的：

```text
(venv) $ flask db downgrade   # 回退到上一个版本
```

这会删除 read_count 列，撤销上一次迁移的所有变更。

不是所有操作都能自动回滚（如删除列在 SQLite 中）。回滚前先确认 flask db current 查看当前版本，确保你知道自己在回退什么。生产环境回滚前务必备份数据。


## Flask-Migrate vs Django Migration 对照

Django 的迁移系统更自动化、更集成；Flask 通过 Flask-Migrate 达到了同等级别的能力。


## 本章小结

本章你掌握了 Flask-Migrate 的完整流程：flask db init 初始化、flask db migrate 生成迁移脚本、flask db upgrade 执行迁移、flask db downgrade 回滚。

此后每次修改 models.py 都走这个三步流程，数据库结构变更永远有历史可追溯。


## 复习重点

- 能说明 `Flask-Migrate` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
