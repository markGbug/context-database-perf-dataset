# Flask：Flask JSON

- 来源：[Flask JSON](https://www.runoob.com/flask/flask-json.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：练习笔记
- 章节序号：3907

## 本章内容

Flask 的 JSON 模块提供了序列化/反序列化功能，底层默认使用 Python 标准库 json，可通过 JSONProvider 替换。

导入方式：

```text
from flask import jsonify
```

或

```text
from flask.json import dumps, loads
```


## jsonify 函数

最常用的 JSON 响应构建函数。将 Python 对象序列化为 JSON Response。


## dumps / loads / dump / load


## JSONProvider 类

可自定义的 JSON 处理器基类。要替换默认 JSON 实现，继承此类并覆盖相关方法。


## DefaultJSONProvider

默认的 JSONProvider 实现，基于 Python 标准库 json。


## JSON Tag 序列化

flask.json.tag 模块支持序列化更多 Python 类型，如 datetime、tuple、set 等。


## 代码示例


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Flask JSON` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
