# FastAPI：FastAPI 请求头与 Cookie

- 来源：[FastAPI 请求头与 Cookie](https://www.runoob.com/fastapi/fastapi-header-cookie.html)
- 分类：Python / 数据科学
- 技术：FastAPI
- 笔记类型：练习笔记
- 章节序号：3856

## 本章内容

FastAPI 提供了 Header 和 Cookie 类型，用于从 HTTP 请求头和 Cookie 中获取数据。


## 请求头参数

使用 Header 声明请求头参数：


## 实例

访问 http://127.0.0.1:8000/items/，返回的 JSON 中包含浏览器的 User-Agent 信息。


## 请求头的自动转换

HTTP 请求头中的字段名使用连字符（如 X-Token），而 Python 变量名不能包含连字符。FastAPI 会自动进行转换：


## 实例

转换规则：

FastAPI 自动将变量名中的下划线 _ 转换为连字符 - 来匹配请求头。如果你需要禁用此转换，设置 Header(convert_underscores=False)。


## 接收重复的请求头

有些请求头可能出现多次（如 Set-Cookie），使用 list 类型接收：


## 实例

请求示例：

```text
GET /items/ HTTP/1.1
X-Token: foo
X-Token: bar
```

响应：{"X-Token values": ["foo", "bar"]}


## Cookie 参数

使用 Cookie 声明 Cookie 参数：


## 实例


## 请求头与 Cookie 同时使用

可以在同一个路由中同时获取请求头和 Cookie：


## 实例


## 小结

- 使用 Header 获取 HTTP 请求头参数
- 使用 Cookie 获取 Cookie 参数
- FastAPI 自动将 Python 变量名中的下划线转为请求头中的连字符
- 使用 list[str] 接收重复的请求头
- 请求头和 Cookie 参数支持与查询参数相同的校验规则


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `FastAPI 请求头与 Cookie` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
