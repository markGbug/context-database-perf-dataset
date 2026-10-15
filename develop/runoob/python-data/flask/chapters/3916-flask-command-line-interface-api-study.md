# Flask：Flask 命令行 API

- 来源：[Flask 命令行 API](https://www.runoob.com/flask/flask-command-line-interface-api.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：学习笔记
- 章节序号：3916

## 本章内容

Flask 基于 Click 构建了命令行工具。

通过 flask 命令运行应用和管理任务。

所有 CLI 类都在 flask.cli 模块中。


## FlaskGroup

Flask 的主命令组。通过 flask 命令使用。


## AppGroup

应用和蓝图的 CLI 命令组基类。通过 app.cli 或 bp.cli 添加自定义命令。

AppGroup.command() 默认启用 with_appcontext=True，意味着你的命令函数会自动拥有应用上下文。如果不需要，传 with_appcontext=False。


## ScriptInfo

存储脚本运行时的信息，用于加载应用。通常不需要手动操作。


## 工具函数


## 默认命令


## 标准选项


## 代码示例


## 实例


## 复习重点

- 能说明 `Flask 命令行 API` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
