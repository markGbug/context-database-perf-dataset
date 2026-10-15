# Flask：Flask Message Flashing API

- 来源：[Flask Message Flashing API](https://www.runoob.com/flask/flask-message-flashing-api.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：学习笔记
- 章节序号：3906

## 本章内容

消息闪现（Flash）机制用于在下一次请求中显示一次性反馈消息，典型场景是「操作成功」或「输入错误」提示。

Flask 将消息存储在 Session 中，读取后自动清除。


## flash 函数


## get_flashed_messages 函数


## 模板中使用

get_flashed_messages() 在模板中可以直接调用，无需通过 render_template 传递。


## 实例


## 代码示例


## 实例

Flash 消息存储在 Session 中，因此必须设置 SECRET_KEY。消息仅在读取它的下一次请求中可见，之后自动清除。


## 复习重点

- 能说明 `Flask Message Flashing API` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
