# Flask：Flask Stream Helpers API

- 来源：[Flask Stream Helpers API](https://www.runoob.com/flask/flask-stream-helpers-api.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：学习笔记
- 章节序号：3910

## 本章内容

stream_with_context 用于在生成器函数中保持请求上下文，使流式响应中仍能访问 request、session 等对象。


## stream_with_context


## 两种用法

注意事项：一旦响应体开始发送，就不能再修改响应头。如果生成器中需要访问 session，必须在视图函数中先访问 session 以触发 Vary: Cookie 头的设置。


## 代码示例


## 实例


## 复习重点

- 能说明 `Flask Stream Helpers API` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
