# Django：类视图（CBV）重构

- 来源：[类视图（CBV）](https://www.runoob.com/django/django-blog-cbv.html)
- 分类：Python / 数据科学
- 技术：Django
- 笔记类型：学习笔记
- 章节序号：3834

## 本章内容

本章你将学习 Django 的类视图（CBV），用更简洁的代码重构首页和详情页。


## FBV vs CBV

到目前为止，我们所有的视图都是用函数写的（Function-Based View，FBV）。

Django 还提供了 类视图（Class-Based View，CBV），用类来封装视图逻辑。

两者没有绝对的优劣，Django 项目通常是 FBV 和 CBV 混用：复杂逻辑用 FBV，标准 CRUD 用 CBV。


## ListView — 列表页重构

首页的 index 视图本质是：查询文章列表 → 渲染模板。

这类模式化的逻辑，Django 的 ListView 已经帮你写好了。


## 实例

对比一下重构前后的代码量：FBV 约 40 行 → CBV 约 30 行，而且逻辑被清晰地划分到不同方法中。


## DetailView — 详情页重构


## 实例


## 更新路由配置

CBV 的路由写法与 FBV 略有不同——需要调用 .as_view()。


## 实例

为什么 CBV 要用 .as_view()？Django 的 URL 配置期望的是一个可调用对象（函数）。.as_view() 将类视图转换成一个符合 Django 视图函数签名的可调用对象，内部负责根据 HTTP 方法（GET/POST）自动分发到类的 get() 或 post() 方法。


## 常用通用视图一览

Django 的通用视图覆盖了约 80% 的 Web 开发场景。遇到不满足需求的情况再退回 FBV。


## LoginRequiredMixin

CBV 不能用 @login_required 装饰器（那是给函数用的），改用 LoginRequiredMixin。


## 实例

Mixin 的继承顺序很重要：LoginRequiredMixin 必须写在 ListView 前面。Python 多继承的解析顺序是从左到右，LoginRequiredMixin 先检查登录状态，通过后才继续执行 ListView 的逻辑。


## 什么时候用 CBV，什么时候用 FBV？

经验法则：

- FBV：逻辑复杂、条件分支多、非标准流程的视图（如 toggle_favorite）
- CBV：标准 CRUD 操作、逻辑可以清晰拆分为 get/post 的视图（如列表页、详情页）

toggle_favorite（收藏切换）这类操作逻辑简单但流程不同于常规 CRUD，FBV 更合适。

index 和 post_detail 这类标准的数据展示页面，CBV 可以显著减少样板代码。


## 本章小结

本章你学会了 Django 类视图的核心用法：ListView 展示列表、DetailView 展示详情、get_queryset/get_context_data 定制查询和上下文、as_view() 在路由中启用、LoginRequiredMixin 替代 login_required。

重构后的首页和详情页代码更短、结构更清晰。


## 复习重点

- 能说明 `类视图（CBV）` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
