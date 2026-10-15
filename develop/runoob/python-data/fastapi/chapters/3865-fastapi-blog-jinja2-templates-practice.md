# FastAPI：Jinja2 模板

- 来源：[Jinja2 模板](https://www.runoob.com/fastapi/fastapi-blog-jinja2-templates.html)
- 分类：Python / 数据科学
- 技术：FastAPI
- 笔记类型：练习笔记
- 章节序号：3865

## 本章内容

本章你将学会在 FastAPI 中配置 Jinja2 模板引擎，用静态文件和模板继承构建完整的 HTML 页面。


## FastAPI 的两种渲染模式

FastAPI 默认返回 JSON（适合 API），但也能返回 HTML（适合 SSR）。

两种模式可以共存——同一个项目既可以提供 JSON API，也可以渲染网页。


## 挂载静态文件

静态文件（CSS、JS、图片）通过 StaticFiles 挂载到指定路径。


## 实例

模板中引用静态文件：


## 实例


## 配置 Jinja2 模板


## 实例

FastAPI 的模板渲染与 Flask 有两个关键区别：1. 视图函数必须接收 request: Request 参数；2. request 必须作为 context 传给模板。如果漏传 request，模板中的 url_for 功能会失效。


## 创建 base.html 父模板


## 实例


### 创建 index.html 子模板


## 实例


## FastAPI 模板中的 url_for()

与 Flask 类似，FastAPI 也支持 url_for()，但需要先给路由起名字。


## 实例


## 实例


## 创建基础 CSS 样式


## 实例


## 本章小结

本章你学会了 FastAPI 中的前端渲染配置：StaticFiles 挂载静态资源、Jinja2Templates 配置模板目录、TemplateResponse 返回 HTML、与 Flask 在模板渲染上的关键差异（Request 参数必须传入）。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Jinja2 模板` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
