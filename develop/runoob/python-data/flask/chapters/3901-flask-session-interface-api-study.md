# Flask：Flask Session Interface API

- 来源：[Flask Session Interface API](https://www.runoob.com/flask/flask-session-interface-api.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：学习笔记
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


## 复习重点

- 能说明 `Flask Session Interface API` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
