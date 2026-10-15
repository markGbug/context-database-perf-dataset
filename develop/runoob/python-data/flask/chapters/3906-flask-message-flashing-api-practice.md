# Flask：Flask Message Flashing API

- 来源：[Flask Message Flashing API](https://www.runoob.com/flask/flask-message-flashing-api.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：练习笔记
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


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Flask Message Flashing API` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
