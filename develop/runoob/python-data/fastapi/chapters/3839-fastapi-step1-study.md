# FastAPI：FastAPI 第一个应用

- 来源：[第一个 FastAPI 应用](https://www.runoob.com/fastapi/fastapi-step1.html)
- 分类：Python / 数据科学
- 技术：FastAPI
- 笔记类型：学习笔记
- 章节序号：3839

## 本章内容

本节通过一个完整的示例，带你从零开始创建一个 FastAPI 应用，并理解其中每一行代码的含义。


## 最简应用

创建一个名为 main.py 的文件，添加以下代码：


## 实例

启动应用：

```text
$ uvicorn main:app --reload
```

访问 http://127.0.0.1:8000，返回：

```text
{"message": "Hello World"}
```


## 代码拆解


### 1. 导入 FastAPI

```text
from fastapi import FastAPI
```

FastAPI 是 Python 类，为你的 API 提供所有核心功能。它直接继承自 Starlette，因此你也可以使用 Starlette 的所有功能。


### 2. 创建应用实例

```text
app = FastAPI()
```

创建一个 FastAPI 实例，变量名通常用 app。这个实例是创建所有 API 的主要交互对象。与 Flask 不同，FastAPI 不需要传递 __name__ 参数。


### 3. 定义路径操作装饰器

```text
@app.get("/")
```

这行代码告诉 FastAPI：当用户通过 GET 方法访问根路径 / 时，执行下方函数。

其中涉及两个概念：

FastAPI 支持所有 HTTP 方法的装饰器：


### 4. 定义路径操作函数

```text
async def root():
```

这是路径操作函数，每当 FastAPI 接收到 GET / 请求时就会调用它。函数名可以随意取，但建议取有意义的名称。


### 5. 返回响应内容

```text
return {"message": "Hello World"}
```

函数返回一个字典，FastAPI 会自动将其转换为 JSON 格式响应。你可以返回 dict、list、str、int 等类型，FastAPI 都会自动处理 JSON 转换。


## 添加更多路由

接下来我们添加路径参数和查询参数，丰富应用功能：


## 实例

新增路由的参数说明：

访问测试：

```text
# 访问根路径
GET http://127.0.0.1:8000/
响应: {"message": "Hello World"}

# 访问带路径参数的路由
GET http://127.0.0.1:8000/items/5
响应: {"item_id": 5, "q": null}

# 同时传递路径参数和查询参数
GET http://127.0.0.1:8000/items/5?q=runoob
响应: {"item_id": 5, "q": "runoob"}
```

注意 item_id 的值是整数 5 而不是字符串 "5"，这就是 FastAPI 类型声明的数据转换功能。如果传入非整数（如 /items/foo），FastAPI 会返回清晰的校验错误信息。


## 添加 POST 请求

下面我们添加一个使用请求体的 POST 路由：


## 实例

这里使用了 Pydantic 的 BaseModel 来定义请求体的结构。FastAPI 会自动：

- 将请求中的 JSON 数据解析为 Item 对象
- 校验数据类型和必填字段
- 在 API 文档中展示请求体结构

Pydantic 是 FastAPI 的核心依赖，用于数据校验和序列化。后续章节会详细介绍它的用法。


## FastAPI 参数识别规则

FastAPI 通过以下规则自动识别参数来源：

你可以在同一个函数中混合使用这三种参数，FastAPI 会自动从正确的位置获取数据。


## 小结

创建 FastAPI 应用的核心步骤：

- 导入 FastAPI
- 创建应用实例 app = FastAPI()
- 使用装饰器（如 @app.get()）定义路径操作
- 定义路径操作函数，使用类型注解声明参数
- 使用 uvicorn main:app --reload 运行开发服务器


## 复习重点

- 能说明 `第一个 FastAPI 应用` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
