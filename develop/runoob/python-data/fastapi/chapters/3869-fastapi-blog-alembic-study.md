# FastAPI：Alembic 数据库迁移

- 来源：[Alembic 数据库迁移](https://www.runoob.com/fastapi/fastapi-blog-alembic.html)
- 分类：Python / 数据科学
- 技术：FastAPI
- 笔记类型：学习笔记
- 章节序号：3869

## 本章内容

本章你将学会用 Alembic 管理数据库结构变更，理解与 Django Migration、Flask-Migrate 的异同。


## 为什么需要迁移工具？

Base.metadata.create_all() 同样有致命缺陷：只在表不存在时创建，修改已有表结构不会自动同步。

Alembic 是 SQLAlchemy 官方的迁移工具，Django 的 makemigrations/migrate 和 Flask 的 Flask-Migrate，底层都是借鉴了 Alembic 的设计。


## 安装与初始化

```text
(venv) $ pip install alembic
(venv) $ alembic init alembic
Creating directory alembic/... done
```

生成的目录结构：

```text
alembic/
├── versions/          # 迁移脚本存放目录
├── env.py             # 迁移环境配置（需手动修改！）
└── script.py.mako     # 迁移脚本模板
alembic.ini            # Alembic 配置文件
```


## 配置 env.py 连接到你的模型

这是关键步骤——Alembic 默认不知道你的 SQLAlchemy 模型在哪里。


## 实例

同时修改 alembic.ini 中的数据库连接：

```text
# 文件路径：alembic.ini
sqlalchemy.url = sqlite:///./blog.db
```


## 迁移三步曲


### 生成并执行迁移

```text
(venv) $ alembic revision --autogenerate -m "初始化 Post 和 Category 模型"
INFO  [alembic.autogenerate] Detected added table 'categories'
INFO  [alembic.autogenerate] Detected added table 'posts'
Generating alembic/versions/xxxx_initial.py ... done

(venv) $ alembic upgrade head
INFO  [alembic.runtime.migration] Running upgrade -> xxxx, 初始化
```


## 实战：新增 read_count 字段


## 实例

```text
(venv) $ alembic revision --autogenerate -m "Post 新增 read_count 字段"
(venv) $ alembic upgrade head
```


### 回滚

```text
(venv) $ alembic downgrade -1        # 回退到上一个版本
```

alembic upgrade head 中的 head 表示最新版本。也可以指定具体版本号：alembic upgrade xxxx（版本 ID）。


## 三框架迁移工具对照


## 本章小结

本章你掌握了 Alembic 的完整流程：alembic init 初始化、配置 env.py 连接模型、revision --autogenerate 生成迁移、upgrade head 执行、downgrade 回滚。

Alembic 比 Django/Flask 的迁移工具配置步骤多，但更底层、更灵活。

下一章预告：文章多了需要搜索和分页。下一章实现关键词联合搜索和基于 offset/limit 的分页功能。


## 复习重点

- 能说明 `Alembic 数据库迁移` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
