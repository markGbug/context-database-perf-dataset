# Flask：Flask Web 应用

- 来源：[Flask Web 应用](https://www.runoob.com/flask/flask-blog-project-init.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：学习笔记
- 章节序号：3917

## 本章内容

本章带你从零开始，用 Flask 创建第一个 Web 应用，理解微框架的设计哲学。


## Flask 与 Django 的定位差异

Django 是「大而全」的全栈框架，自带 ORM、模板引擎、管理后台、用户认证、表单处理等。

Flask 是微框架——核心极简，只提供路由和模板渲染，其他功能通过扩展按需添加。

选择建议：新手快速出成果用 Django，喜欢自己掌控、按需组装的用 Flask。


## 环境准备

确认 Python 版本（需要 3.8 以上）：

```text
$ python3 --version
Python 3.12.0
```


### 创建虚拟环境并安装 Flask

```text
$ python3 -m venv venv
$ source venv/bin/activate           # Windows：venv\Scripts\activate
(venv) $ pip install flask
```

验证安装：

```text
(venv) $ python -c "import flask; print(flask.__version__)"
3.1.0
```


## Flask 最小应用

一个 Flask 应用只需要一个 Python 文件。


## 实例


### 启动开发服务器

```text
(venv) $ flask run
 * Running on http://127.0.0.1:5000
```

浏览器访问 http://127.0.0.1:5000/，看到页面内容。

开启热重载（修改代码后自动重启服务器）：

```text
(venv) $ flask run --debug
```

flask run 默认查找 app.py 中的 app 实例。如果文件名或实例名不同，需要设置环境变量：FLASK_APP=myapp.py（文件名）、FLASK_APP=myapp:create_app()（工厂函数）。


## Flask 命令行工具

除了 flask run，Flask 还提供了其他有用的命令。


## 项目目录结构规划

虽然 Flask 支持单文件应用，但真实项目需要清晰的目录组织。

```text
blog_project/
├── app/
│   ├── __init__.py          # 应用工厂 create_app()（第十章引入）
│   ├── blueprints/          # 路由 Blueprint（第四章分离）
│   ├── templates/           # Jinja2 模板（第二章创建）
│   ├── static/              # 静态文件 CSS/JS/图片
│   ├── models.py            # SQLAlchemy 模型（第三章创建）
│   └── forms.py             # Flask-WTF 表单（第八章创建）
├── config.py                # 配置文件
├── app.py                   # 应用入口（第一章从这里开始）
└── .env                     # 环境变量
```


## 动手：博客首页路由

创建项目骨架，配置首页路由，让浏览器显示欢迎信息。


## 实例

运行：

```text
flask run
```

访问首页和关于页面，确认路由正常工作。


## 本章小结

本章你完成了三件事：创建虚拟环境并安装 Flask、理解了 Flask 微框架与 Django 大而全的定位差异、编写了第一个路由页面。

核心收获：Flask 最小应用只需要 Flask(__name__) + @app.route() 装饰器，用 flask run 启动。


## 复习重点

- 能说明 `Flask Web 应用` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
