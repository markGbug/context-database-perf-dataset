# Flask：Flask Session API

- 来源：[Flask Session API](https://www.runoob.com/flask/flask-session-api.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：练习笔记
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


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Flask Session API` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
