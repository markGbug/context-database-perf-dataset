# Flask：Jinja2 模板 — 渲染 HTML 页面

- 来源：[Jinja2 模板](https://www.runoob.com/flask/flask-blog-jinja2-templates.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：练习笔记
- 章节序号：3918

## 本章内容

本章你将学会用 Jinja2 模板引擎渲染完整的 HTML 页面，抽取公共布局。


## 从字符串到模板

上一章视图函数直接返回字符串，里行嵌 HTML 标签，无法复用、难以维护。

render_template() 是 Flask 渲染模板的入口：它加载 HTML 文件、注入变量、返回完整的 HTML 响应。


## 实例

Flask 默认在项目根目录的 templates/ 文件夹中查找模板。


## 创建模板文件

在项目根目录下创建 templates/ 文件夹，然后创建 index.html。


## 实例


## Jinja2 模板语法速览

Jinja2 语法与 Django 模板语法几乎完全一样，也与 Vue3 的插值语法类似。

Jinja2 和 Django 模板的语法几乎一致，但 Jinja2 更灵活：你可以在模板中写更复杂的 Python 表达式，Django 模板则故意限制了一些能力以避免业务逻辑泄漏到模板中。


## 模板继承：base.html

多个页面共享导航栏、页脚，用 模板继承 避免重复 HTML。


### 创建 base.html 父模板


## 实例


### 子模板继承父模板


## 实例

{% extends 'base.html' %} 必须写在子模板的第一行（注释除外）。这是 Jinja2 的硬性要求——模板引擎需要最先确定继承关系。


## url_for() 生成链接

不要硬编码 URL，用 url_for() 通过函数名反查地址。


## 实例


## 实例

路由变了（如 /post/ 改成 /article/），模板中的 url_for() 自动生成新地址。


## 静态文件配置

Flask 默认将 static/ 目录作为静态文件根目录。

```text
blog_project/
├── static/
│   ├── css/
│   │   └── style.css
│   ├── js/
│   │   └── main.js
│   └── images/
│       └── logo.png
├── templates/
└── app.py
```

模板中通过 url_for('static', filename='css/style.css') 引用。


## 本章小结

本章你掌握了 Jinja2 模板的核心：render_template() 渲染模板、{{ }} 输出变量、{% for/if %} 控制流、base.html + block + extends 模板继承、url_for() 生成链接。

现在博客页面变成了结构清晰的 HTML，公共部分抽取到了 base.html 中。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Jinja2 模板` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
