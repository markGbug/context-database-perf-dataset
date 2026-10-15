# FastAPI：FastAPI 路径参数

- 来源：[FastAPI 路径参数](https://www.runoob.com/fastapi/fastapi-path-params.html)
- 分类：Python / 数据科学
- 技术：FastAPI
- 笔记类型：学习笔记
- 章节序号：3847

## 本章内容

路径参数是 URL 路径中的动态部分，使用花括号 {} 声明。FastAPI 会自动将路径参数传递给路径操作函数，并根据类型注解进行数据转换和校验。


## 基本用法

使用 Python 格式化字符串的语法声明路径参数：


## 实例

访问 http://127.0.0.1:8000/items/5，返回：

```text
{"item_id": 5}
```

注意返回的 item_id 是整数 5，不是字符串 "5"。FastAPI 通过类型注解 item_id: int 自动将 URL 中的字符串转换为整数。


## 数据转换

当你声明类型为 int 时，FastAPI 会自动进行类型转换：

```text
# 传入整数，正常工作
GET /items/3       -> {"item_id": 3}

# 传入非整数，返回校验错误
GET /items/foo     -> 错误：Input should be a valid integer

# 传入浮点数，同样报错
GET /items/4.2     -> 错误：Input should be a valid integer
```

访问 http://127.0.0.1:8000/items/foo 时，FastAPI 返回的校验错误信息：

```text
{
  "detail": [
    {
      "type": "int_parsing",
      "loc": ["path", "item_id"],
      "msg": "Input should be a valid integer, unable to parse string as an integer",
      "input": "foo"
    }
  ]
}
```

FastAPI 的校验错误信息非常清晰，会指出具体的错误位置（loc）、错误类型（type）和错误描述（msg）。这在调试时非常有用。


## 路径参数的类型

除了 int，你还可以使用其他标准 Python 类型：


## 路径顺序很重要

当多个路由可能匹配同一个 URL 时，定义的顺序决定了匹配结果。FastAPI 按照路由定义的顺序依次匹配，第一个匹配的路由将被执行。


## 实例

如果把 /users/me 放在 /users/{user_id} 之后，那么访问 /users/me 时，FastAPI 会认为 "me" 是 user_id 的值，从而匹配到错误的函数。

固定路径的路由一定要放在动态路径参数的路由之前，否则动态参数会把固定路径的值"吞掉"。


## 预设值的路径参数（Enum）

当你需要限制路径参数只能是几个固定值时，可以使用 Python 的 Enum 类型：


## 实例

枚举类的要点：

访问 http://127.0.0.1:8000/models/alexnet，返回：

```text
{"model_name": "alexnet", "message": "Deep Learning FTW!"}
```

如果传入非预设值（如 /models/foobar），FastAPI 会返回校验错误，提示可选值为 alexnet、resnet、lenet。


## 包含路径的路径参数

当你需要路径参数本身包含路径（如文件路径）时，使用 Starlette 的路径转换器：


## 实例

访问 http://127.0.0.1:8000/files/home/johndoe/myfile.txt，返回：

```text
{"file_path": "home/johndoe/myfile.txt"}
```

注意 URL 中 /files/ 和 /home/ 之间会出现双斜杠 //，这是正常的，因为路径参数以 / 开头。


## 小结

通过 Python 标准的类型声明，FastAPI 路径参数可以同时获得：

- 数据转换：URL 中的字符串自动转为声明的类型
- 数据校验：类型不匹配时返回清晰的错误信息
- 自动文档：路径参数的类型和约束自动出现在 API 文档中
- 编辑器支持：类型注解让你在编辑器中获得自动补全


## 复习重点

- 能说明 `FastAPI 路径参数` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
