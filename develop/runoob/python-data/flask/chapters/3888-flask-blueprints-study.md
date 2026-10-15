# Flask：蓝图（Blueprint）

- 来源：[Flask 蓝图](https://www.runoob.com/flask/flask-blueprints.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：学习笔记
- 章节序号：3888

## 本章内容

当应用只有一个文件时，所有路由写在一起还没问题。

但随着功能增长——用户模块、文章模块、管理后台——代码会变得难以维护。

Blueprint（蓝图）就是 Flask 提供的模块化解决方案，让你将应用拆分为独立的功能单元。


## 为什么需要蓝图

蓝图解决的核心问题：

- 代码组织：将相关的路由、模板、静态文件归为一组
- 复用性：同一个蓝图可以注册到不同应用，或注册多次（加不同前缀）
- 团队协作：不同开发者负责不同的蓝图模块，减少冲突


## 创建蓝图

蓝图使用 Blueprint 类创建，用法和 Flask 非常相似——同样的路由装饰器、同样的视图函数写法：


## 实例


## 实例


## 注册蓝图

蓝图创建后不会自动生效，需要在应用中注册：


## 实例

注册后的完整路由表：

注册蓝图后，url_for() 中的 endpoint 需要加上蓝图名前缀，例如 url_for("auth.login") 而非 url_for("login")。


## url_for 在蓝图中的特殊用法

同一个蓝图中，可以使用点号开头的相对引用：


## 实例


## 蓝图的模板和静态文件

蓝图也可以拥有自己的模板和静态文件。

当蓝图有自己的模板文件夹时，Flask 会先在应用的 templates 中查找，找不到再去蓝图指定的文件夹查找。


## 实例

推荐的蓝图目录结构：

```text
myflaskapp/
├── app.py              # 应用入口，注册蓝图
├── auth.py             # 认证蓝图
├── blog.py             # 博客蓝图
├── templates/          # 应用级模板（公共 base.html 等）
│   └── base.html
├── static/             # 应用级静态文件
│   └── style.css
├── auth/               # auth 蓝图的独立资源（可选）
│   └── templates/
│       └── auth/
│           ├── login.html
│           └── register.html
└── blog/               # blog 蓝图的独立资源（可选）
    └── templates/
        └── blog/
            ├── index.html
            └── create.html
```

最简单的做法是不给蓝图配置独立模板文件夹，模板统一放在项目根目录的 templates/ 下，用子目录区分：templates/auth/login.html、templates/blog/index.html。


## 工厂模式——create_app

随着蓝图变多，直接在模块顶层创建 app = Flask(__name__) 会遇到循环导入问题。

工厂模式（Factory Pattern）是解决这个问题的最佳实践：


## 实例

工厂模式的优势：

- 消除循环导入：蓝图可以导入 app，app 也可以导入蓝图，因为导入发生在函数内部
- 支持测试：可以创建不同配置的 app 实例进行测试
- 多实例部署：同一份代码可以创建多个独立的 app 实例

使用工厂模式后，需要通过 flask --app "app:create_app()" run 启动：

```text
$ flask --app "app:create_app()" run
```


## 蓝图中的其他功能

蓝图也支持 before_request、errorhandler 等装饰器，用法和 app 一致：


## 实例

蓝图的 before_request 只影响该蓝图内的路由。如果你需要在所有请求前执行逻辑，应该用 app.before_request。


## 复习重点

- 能说明 `Flask 蓝图` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
