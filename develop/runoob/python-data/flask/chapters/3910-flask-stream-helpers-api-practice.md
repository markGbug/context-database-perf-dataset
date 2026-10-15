# Flask：Flask Stream Helpers API

- 来源：[Flask Stream Helpers API](https://www.runoob.com/flask/flask-stream-helpers-api.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：练习笔记
- 章节序号：3910

## 本章内容

stream_with_context 用于在生成器函数中保持请求上下文，使流式响应中仍能访问 request、session 等对象。


## stream_with_context


## 两种用法

注意事项：一旦响应体开始发送，就不能再修改响应头。如果生成器中需要访问 session，必须在视图函数中先访问 session 以触发 Vary: Cookie 头的设置。


## 代码示例


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Flask Stream Helpers API` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
