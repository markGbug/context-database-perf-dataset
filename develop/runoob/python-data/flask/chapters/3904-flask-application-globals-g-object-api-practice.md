# Flask：Flask Application Globals - g 对象 API

- 来源：[Flask Application Globals](https://www.runoob.com/flask/flask-application-globals-g-object-api.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：练习笔记
- 章节序号：3904

## 本章内容

g 是一个请求级别的全局命名空间，用于在同一请求的多个函数之间共享数据。

通过 from flask import g 导入，仅在应用上下文活跃时可用。


## g 对象说明


## _AppCtxGlobals 方法


## 典型使用模式


## 实例

核心原则：g 对象只用于同一请求内的数据共享。不要在 g 中存储跨请求的数据，也不要在 g 中存储需要持久化的信息。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Flask Application Globals` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
