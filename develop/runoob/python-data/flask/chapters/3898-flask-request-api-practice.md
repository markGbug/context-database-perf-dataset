# Flask：Flask Request 请求对象 API

- 来源：[Flask Request API](https://www.runoob.com/flask/flask-request-api.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：练习笔记
- 章节序号：3898

## 本章内容

Request 类封装了客户端发来的 HTTP 请求的所有信息。

通过 from flask import request 导入代理对象，在视图函数中直接使用。


## 常用属性速查


## 获取请求数据

对 args、form 等 MultiDict 类型，始终使用 .get(key, default) 方法获取值。直接用 request.args["key"] 访问不存在的键会抛出 KeyError（返回 400 错误）。


## 内容协商属性


## 代码示例


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Flask Request API` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
