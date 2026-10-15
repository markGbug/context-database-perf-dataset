# FastAPI：FastAPI 安装与环境配置

- 来源：[FastAPI 安装](https://www.runoob.com/fastapi/fastapi-install.html)
- 分类：Python / 数据科学
- 技术：FastAPI
- 笔记类型：练习笔记
- 章节序号：3837

## 本章内容

FastAPI 依赖 Python 3.8 及更高版本。本节介绍如何安装 FastAPI 以及配置开发环境。


## 检查 Python 版本

在安装 FastAPI 之前，先确认你的 Python 版本：

```text
$ python --version
Python 3.11.0

# 或者
$ python3 --version
Python 3.11.0
```

如果你的 Python 版本低于 3.8，请先升级 Python。


## 创建虚拟环境

推荐在虚拟环境中安装 FastAPI，避免与系统 Python 包产生冲突：

```text
# 创建虚拟环境
$ python -m venv venv

# 激活虚拟环境（macOS/Linux）
$ source venv/bin/activate

# 激活虚拟环境（Windows）
$ venv\Scripts\activate
```

虚拟环境是 Python 开发的最佳实践。每个项目使用独立的虚拟环境，可以避免不同项目之间的依赖冲突。


## 安装 FastAPI

使用 pip 安装 FastAPI：

```text
$ pip install fastapi
```

这条命令只安装 FastAPI 核心包。如果你需要一次性安装 FastAPI 及其所有可选依赖，可以使用：

```text
$ pip install "fastapi[all]"
```

fastapi[all] 会安装以下组件：


## 安装 Uvicorn

FastAPI 是一个 ASGI 框架，需要一个 ASGI 服务器来运行。最常用的是 Uvicorn：

```text
$ pip install "uvicorn[standard]"
```

[standard] 会安装 uvloop（高性能事件循环）和 httptools（高性能 HTTP 解析器），显著提升性能。

ASGI（Asynchronous Server Gateway Interface）是 Python 异步 Web 服务器与应用程序之间的标准接口，是 WSGI 的异步版本。传统框架如 Flask 使用 WSGI（同步），而 FastAPI 使用 ASGI（异步），能够更高效地处理并发请求。


## 运行第一个 FastAPI 应用

安装完成后，创建一个名为 main.py 的文件：


## 实例

在命令行中启动应用：

```text
$ uvicorn main:app --reload
```

参数说明：

启动成功后，终端会显示：

```text
INFO:     Uvicorn running on http://127.0.0.1:8000 (Press CTRL+C to quit)
INFO:     Started reloader process
INFO:     Started server process
INFO:     Waiting for application startup.
INFO:     Application startup complete.
```

打开浏览器访问 http://127.0.0.1:8000，你将看到如下 JSON 响应：

```text
{"message": "Hello World"}
```

同时，FastAPI 自动生成了交互式 API 文档：


## 使用 FastAPI CLI

FastAPI 新版本提供了 fastapi 命令行工具，可以更方便地运行应用：

```text
# 开发模式（自动重载）
$ fastapi dev

# 生产模式
$ fastapi run
```

fastapi dev 会自动查找项目中的 FastAPI 应用并启动开发服务器，等同于 uvicorn main:app --reload。


## 推荐开发工具


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `FastAPI 安装` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
