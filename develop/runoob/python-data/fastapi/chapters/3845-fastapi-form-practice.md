# FastAPI：FastAPI 表单数据

- 来源：[FastAPI 表单数据](https://www.runoob.com/fastapi/fastapi-form.html)
- 分类：Python / 数据科学
- 技术：FastAPI
- 笔记类型：练习笔记
- 章节序号：3845

## 本章内容

当客户端通过 HTML 表单（application/x-www-form-urlencoded）提交数据时，需要使用 Form 来接收表单字段，而不是 BaseModel。


## 安装 python-multipart

使用表单功能前，需要先安装 python-multipart：

```text
pip install python-multipart
```


## 接收表单数据

使用 Form 声明表单字段：


## 实例


## 表单字段与 JSON 请求体的区别

表单数据以"字段"的形式发送，不是 JSON。因此不能将 Form 参数声明为 Pydantic 模型。表单字段和 JSON 请求体不能在同一个路由中同时使用。


## 可选表单字段

与查询参数类似，有默认值的表单字段是可选的：


## 实例


## 使用 HTML 表单测试

你可以创建一个 HTML 页面来测试表单提交：


## 实例


## 表单数据的校验和文档

使用 Form 声明的字段，FastAPI 会自动进行数据校验并在 API 文档中展示：


## 小结

- 使用 Form 接收 HTML 表单提交的数据
- 表单数据不是 JSON，不能与 BaseModel 请求体混用
- Form() 声明必填字段，Form(None) 声明可选字段
- 需要安装 python-multipart 包
- 表单字段支持与查询参数相同的校验规则（min_length、gt 等）


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `FastAPI 表单数据` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
