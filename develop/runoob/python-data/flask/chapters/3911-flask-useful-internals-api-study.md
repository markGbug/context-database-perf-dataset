# Flask：Flask 内部对象 API

- 来源：[Flask 内部对象 API](https://www.runoob.com/flask/flask-useful-internals-api.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：学习笔记
- 章节序号：3911

## 本章内容

Flask 提供了几个底层内部对象，用于访问活跃的应用上下文和蓝图的注册状态。大多数应用不需要直接使用它们。


## AppContext 应用上下文


## app_ctx 代理


## BlueprintSetupState

蓝图注册时的状态对象，可在 record 回调中使用。


## 废弃的 RequestContext

自 Flask 3.2 起，RequestContext 已合并到 AppContext。相关的 request_ctx 代理也已合并到 app_ctx。旧名称将在 Flask 4.0 中移除。


## 代码示例


## 实例


## 复习重点

- 能说明 `Flask 内部对象 API` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
