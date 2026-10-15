# FastAPI：路由与文章列表、详情页

- 来源：[路由](https://www.runoob.com/fastapi/fastapi-blog-routers-views.html)
- 分类：Python / 数据科学
- 技术：FastAPI
- 笔记类型：练习笔记
- 章节序号：3868

## 本章内容

本章你将学会用 APIRouter 拆分路由，实现首页文章列表和文章详情页。


## APIRouter — FastAPI 的路由拆分方案

APIRouter 对标 Flask 的 Blueprint 和 Django 的 include()。


## 实例

在 main.py 中挂载 APIRouter：


## 实例


## 渲染文章列表页


## 实例

str | None = Query(None) 是 Python 3.10+ 的类型联合语法，等价于 Optional[str]。FastAPI 会根据类型提示自动：1. 使参数可选；2. 在 Swagger 文档中标记为可选；3. 不传时不报错。


## 渲染文章详情页


## 实例

注意区分：同一个路由可以同时提供 JSON API（声明 response_model）和 HTML 页面（返回 TemplateResponse）。通常的做法是：API 路由放在 /api/ 前缀下，页面路由放在根路径下。


## 创建首页和详情页模板


## 实例


## 实例


## 本章小结

本章你完成了 FastAPI 的核心路由开发：APIRouter 按模块拆分路由（prefix + tags）、查询参数用 Query() + 类型提示声明、TemplateResponse 渲染页面、404 异常处理。

博客现在有了首页文章列表、分类筛选和详情页三个完整页面。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `路由` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
