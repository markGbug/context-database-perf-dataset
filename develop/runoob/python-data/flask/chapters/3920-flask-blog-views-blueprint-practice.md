# Flask：视图函数 — 渲染文章列表与详情页

- 来源：[视图函数](https://www.runoob.com/flask/flask-blog-views-blueprint.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：练习笔记
- 章节序号：3920

## 本章内容

本章你将学会用视图函数从数据库查询数据，渲染首页和详情页，并用 Blueprint 拆分路由。


## 视图函数的职责

Flask 视图函数的职责与 Django 一致：接收请求 → 查询数据 → 渲染模板。


## 实例


## 路径参数与查询参数

Flask 路由支持多种类型转换器：<int:id>（整数）、<string:slug>（默认，不包含 /）、<path:path>（包含 /）、<float:price> 等。


## 文章详情页


## 实例


### 自定义 404 错误页面


## 实例


## 分类筛选


## 实例

request.args 是一个不可变的 MultiDict，用于读取 URL 查询参数。用 .get('key', '默认值') 安全获取，参数不存在时返回默认值而非报错。


## Blueprint — 拆分路由

当视图函数增多，全部堆在 app.py 中会失控。

Blueprint 是 Flask 的路由分组方案：按功能模块拆分视图，通过 app.register_blueprint() 注册。

```text
app/
├── blueprints/
│   ├── __init__.py
│   ├── main.py          # 首页、关于、搜索
│   └── posts.py         # 文章列表、详情
├── templates/
├── models.py
└── __init__.py
```


## 实例


## 实例

在应用入口注册 Blueprint：


## 实例

Blueprint 可以指定 url_prefix（如 url_prefix='/blog'），则蓝图内所有路由都会自动加上这个前缀。Blueprint 也可以有自己的模板和静态文件目录。


## 创建首页和详情页模板


### index.html


## 实例

url_for() 中使用 Blueprint 视图时，格式为 url_for('蓝图名.函数名')，如 url_for('posts.post_detail', post_id=3)。注意与 Django 的 {% url %} 标签对比：Flask 用 {{ url_for() }}，可以嵌套在 Python 表达式中更灵活。


## 本章小结

本章你掌握了 Flask 视图和路由组织：Post.query 查询数据、路径参数 <int:post_id> 和查询参数 request.args、get_or_404 安全查询、abort(404) 和自定义错误页、Blueprint 按模块拆分路由。

博客现在有了首页文章列表、分类筛选和详情页三个完整页面。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `视图函数` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
