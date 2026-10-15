# Flask：Flask Request 请求对象 API

- 来源：[Flask Request API](https://www.runoob.com/flask/flask-request-api.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：学习笔记
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


## 复习重点

- 能说明 `Flask Request API` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
