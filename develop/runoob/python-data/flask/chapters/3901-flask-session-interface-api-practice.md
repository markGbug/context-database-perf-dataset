# Flask：Flask Session Interface API

- 来源：[Flask Session Interface API](https://www.runoob.com/flask/flask-session-interface-api.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：练习笔记
- 章节序号：3901

## 本章内容

SessionInterface 是 Session 的底层抽象，允许你替换 Flask 默认的 Cookie 存储方式为 Redis、数据库等外部存储。

自定义实现只需继承 SessionInterface 并实现两个方法。


## SessionInterface 抽象基类


## Cookie 选项方法

以下方法用于获取 Session Cookie 的各项属性，可被重写：


## 内置实现


## 替换默认 Session 实现


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Flask Session Interface API` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
