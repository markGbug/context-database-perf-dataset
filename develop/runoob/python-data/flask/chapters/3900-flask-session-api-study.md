# Flask：Flask Session API

- 来源：[Flask Session API](https://www.runoob.com/flask/flask-session-api.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：学习笔记
- 章节序号：3900

## 本章内容

Session 用于在同一用户的不同请求之间保存数据。Flask 默认使用签名 Cookie 实现，数据存储在客户端但无法被篡改。

通过 from flask import session 导入，像字典一样使用。


## session 代理对象

session 是一个代理，指向当前请求的 SessionMixin 实例。只在请求上下文中可用。

当修改 session 中嵌套的可变对象（如列表、字典）时，Flask 无法自动检测到修改。

必须手动设置 session.modified = True，否则修改不会保存到 Cookie 中。


## 配置项


## 代码示例


## 实例


## 复习重点

- 能说明 `Flask Session API` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
