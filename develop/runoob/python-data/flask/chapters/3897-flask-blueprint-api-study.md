# Flask：Flask Blueprint 蓝图对象 API

- 来源：[Flask 蓝图对象 API](https://www.runoob.com/flask/flask-blueprint-api.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：学习笔记
- 章节序号：3897

## 本章内容

Blueprint 用于将应用拆分为可复用的模块，每个蓝图可以有自己的路由、模板、静态文件和钩子。

创建方式：

```text
bp = Blueprint("auth", __name__)
```


## 构造函数参数


## 核心属性


## 路由方法

蓝图的用法与 Flask 应用一致，只是把 app 换为 bp：


## 钩子装饰器

蓝图的钩子只影响该蓝图内的路由：


## 蓝图特有方法


## 注册蓝图时的 options 参数

调用 app.register_blueprint(bp, **options) 时可传递：


## 代码示例


## 实例


## 复习重点

- 能说明 `Flask 蓝图对象 API` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
