# FastAPI：FastAPI 查询参数

- 来源：[FastAPI 查询参数](https://www.runoob.com/fastapi/fastapi-query-params.html)
- 分类：Python / 数据科学
- 技术：FastAPI
- 笔记类型：练习笔记
- 章节序号：3848

## 本章内容

查询参数是 URL 中 ? 之后、以 & 分隔的键值对。当函数参数不是路径参数也不是请求体时，FastAPI 会将其自动解释为查询参数。


## 基本用法

声明查询参数只需要在函数参数中添加类型注解和默认值：


## 实例

查询参数在 URL 中的格式：

```text
http://127.0.0.1:8000/items/?skip=0&limit=10
```

不同访问方式的参数值：


## 可选参数

将默认值设为 None 即可声明可选的查询参数：


## 实例

这里 q: str | None = None 表示 q 可以是字符串或 None，默认值为 None。

FastAPI 通过默认值 = None 判断参数是否必填，而不是通过类型注解 str | None。类型注解主要帮助编辑器提供更好的支持。


## 查询参数类型转换

FastAPI 支持将查询参数自动转换为 bool 类型：


## 实例

以下 URL 中的 short 参数都会被转换为 True：

```text
/items/foo?short=1
/items/foo?short=True
/items/foo?short=true
/items/foo?short=on
/items/foo?short=yes
```

其他值会被转换为 False。


## 必选查询参数

不设置默认值的查询参数即为必选参数：


## 实例

如果访问 /items/foo 时没有提供 needy 参数，FastAPI 会返回类似以下的错误：

```text
{
  "detail": [
    {
      "type": "missing",
      "loc": ["query", "needy"],
      "msg": "Field required",
      "input": null
    }
  ]
}
```


## 混合使用必选、有默认值和可选参数

你可以在同一个函数中混合使用不同类型的查询参数：


## 实例

参数类型总结：


## 多个路径和查询参数

FastAPI 可以同时识别多个路径参数和查询参数，参数的声明顺序不影响识别：


## 实例

FastAPI 通过参数名匹配路径中的变量，因此函数参数的顺序无关紧要。


## 小结

查询参数的核心要点：

- 有默认值的参数是可选的，没有默认值的是必选的
- FastAPI 自动将 URL 中的字符串转为声明的类型
- bool 类型支持多种写法（true、1、on、yes 等）
- 查询参数可以与路径参数混合使用，顺序无关


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `FastAPI 查询参数` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
