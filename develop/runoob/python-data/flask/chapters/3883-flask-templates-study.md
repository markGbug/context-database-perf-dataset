# Flask：Flask 模板渲染

- 来源：[Flask 模板渲染](https://www.runoob.com/flask/flask-templates.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：学习笔记
- 章节序号：3883

## 本章内容

在 Python 代码中拼接 HTML 字符串既繁琐又危险（容易产生 XSS 漏洞），Flask 集成了 Jinja2 模板引擎来解决这个问题。

模板让你将业务逻辑和页面展示分离，写出更安全、更易维护的代码。


## render_template 基础

render_template() 是 Flask 中最常用的模板渲染函数。

它的第一个参数是模板文件名，后面的关键字参数会作为变量传递给模板。


## 实例

模板文件放在项目目录下的 templates/ 文件夹中：

```text
runoob-flask-test/
├── app.py
└── templates/
    ├── index.html
    └── user.html
```

index.html 内容为：


## 实例（ index.html ）

访问 http://127.0.0.1:5000/ ，输出结果为：


## Jinja2 基础语法

Jinja2 模板中三种核心语法：


### 模板示例


## 实例（ user.html ）


## 常用过滤器

过滤器用于修改变量的输出格式，使用管道符 | 调用。

安全警告：safe 过滤器会关闭自动转义，只在绝对信任数据来源时使用。对于用户输入的内容，永远不要使用 safe。


## 自动转义——XSS 防护

Jinja2 默认会对所有变量输出进行 HTML 转义，这是 Web 安全的一道关键防线。

例如，如果用户提交的用户名是 <script>alert("xss")</script>，模板渲染时会自动转换为安全文本：

```html
<!-- 模板中直接使用变量 -->
<p>{{ username }}</p>

<!-- 渲染结果（HTML 特殊字符已被转义） -->
<p>&lt;script&gt;alert(&quot;xss&quot;)&lt;/script&gt;</p>
```

转义适用于 .html、.htm、.xml、.xhtml、.svg 结尾的模板文件。


## 模板继承——消除重复代码

模板继承是 Jinja2 最强大的功能之一，它让你可以定义一个「基础布局」，然后通过子模板填充内容。

这避免了在每个页面中重复编写头部、导航、页脚等公共部分。


### 基础模板（父模板）


## 实例


### 子模板（继承父模板）


## 实例

使用模板继承后，你只需要修改 base.html 一处，所有页面的公共部分（如导航、页脚）都会自动更新。


## 模板中的内置对象

以下 Flask 对象在模板中可以直接使用，无需通过 render_template() 传递：


## 包含其他模板——include

使用 {% include %} 可以在一个模板中嵌入另一个模板：


## 实例


## 实例

最佳实践：模板继承（extends）用于页面级的布局复用，include 用于组件级的代码复用。导航栏、侧边栏等可复用组件适合用 include。


## 完整示例：博客首页

将以上知识整合到一个实际场景中：


## 实例


## 实例


## Jinja2 特殊变量


## 复习重点

- 能说明 `Flask 模板渲染` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
