# FastAPI：FastAPI 测试

- 来源：[FastAPI 测试](https://www.runoob.com/fastapi/fastapi-testing.html)
- 分类：Python / 数据科学
- 技术：FastAPI
- 笔记类型：学习笔记
- 章节序号：3862

## 本章内容

FastAPI 基于 Starlette 的 TestClient 提供了便捷的测试支持，可以在不启动服务器的情况下测试 API 的请求和响应。


## 安装依赖

TestClient 基于 httpx，需要安装：

```text
pip install httpx
```


## 基本测试

使用 TestClient 创建测试客户端，然后像使用 httpx 一样发送请求：


## 实例

TestClient 直接调用 FastAPI 应用，不经过网络层，因此测试速度非常快。你不需要启动 Uvicorn 服务器。


## 测试各种请求类型


## 实例


## 测试查询参数和请求头


## 实例


## 测试异常响应


## 实例


## 使用 pytest 运行测试

将测试代码保存为 test_main.py，然后运行：

```java
$ pytest test_main.py

# 显示详细输出
$ pytest test_main.py -v

# 显示 print 输出
$ pytest test_main.py -s
```

pytest 会自动发现以 test_ 开头的文件和函数。


## 测试中覆盖依赖

在测试中，你可能需要覆盖某些依赖（如数据库连接、认证逻辑）：


## 实例

app.dependency_overrides 允许你在测试中替换任何依赖函数，非常适合模拟数据库连接、外部 API 调用等场景。测试完成后记得清除覆盖。


## 小结

- 使用 TestClient 直接测试 FastAPI 应用，无需启动服务器
- 支持 GET、POST、PUT、DELETE 等所有 HTTP 方法的测试
- 可以测试查询参数、请求头、请求体、异常响应等
- 使用 app.dependency_overrides 在测试中覆盖依赖
- 配合 pytest 可以方便地组织和运行测试


## 复习重点

- 能说明 `FastAPI 测试` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
