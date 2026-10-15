# Python：Python requests 模块

- 来源：[Python requests](https://www.runoob.com/python3/python-requests.html)
- 分类：Python / 数据科学
- 技术：Python
- 笔记类型：练习笔记
- 章节序号：4143

## 本章内容

Python requests 是一个常用的 HTTP 请求库，可以方便地向网站发送 HTTP 请求，并获取响应结果。

requests 模块比 urllib 模块更简洁。

使用 requests 发送 HTTP 请求需要先导入 requests 模块：

```text
import requests
```

导入后就可以发送 HTTP 请求，使用 requests 提供的方法向指定 URL 发送 HTTP 请求，例如：


## 实例

每次调用 requests 请求之后，会返回一个 response 对象，该对象包含了具体的响应信息，如状态码、响应头、响应内容等：

```text
print(response.status_code)  # 获取响应状态码
print(response.headers)  # 获取响应头
print(response.content)  # 获取响应内容
```

更多响应信息如下：


## 实例

输出结果如下：

```text
200
OK
utf-8
```

请求 json 数据文件，返回 json 内容：


## 实例

输出结果如下：

```text
{'name': '网站', 'num': 3, 'sites': [{'name': 'Google', 'info': ['Android', 'Google 搜索', 'Google 翻译']}, {'name': 'Runoob', 'info': ['菜鸟教程', '菜鸟工具', '菜鸟微信']}, {'name': 'Taobao', 'info': ['淘宝', '网购']}]}
```


## requests 方法

requests 方法如下表：

使用 requests.request() 发送 get 请求：


## 实例

输出结果如下：

```text
200
```

设置请求头：


## 实例

输出结果如下：

```text
200
UTF-8
https://www.runoob.com/?s=python+%E6%95%99%E7%A8%8B

... 其他内容...
```

post() 方法可以发送 POST 请求到指定 url，一般格式如下：

```text
requests.post(url, data={key: value}, json={key: value}, args)
```

- url 请求 url。
- data 参数为要发送到指定 url 的字典、元组列表、字节或文件对象。
- json 参数为要发送到指定 url 的 JSON 对象。
- args 为其他参数，比如 cookies、headers、verify等。


## 实例

输出结果如下：

```html
<p style='color:red;'>本内容是使用 POST 方法请求的。</p><p style='color:red;'>请求时间：
2022-05-26 17:30:47</p>
```

post 请求带参数：


## 实例

输出结果如下：

```html
<p style='color:red;'>你好，RUNOOB Boy，今天过得怎么样？</p>
```


## 附加请求参数

发送请求我们可以在请求中附加额外的参数，例如请求头、查询参数、请求体等，例如：

```text
headers = {'User-Agent': 'Mozilla/5.0'}  # 设置请求头
params = {'key1': 'value1', 'key2': 'value2'}  # 设置查询参数
data = {'username': 'example', 'password': '123456'}  # 设置请求体
response = requests.post('https://www.runoob.com', headers=headers, params=params, data=data)
```

上述代码发送一个 POST 请求，并附加了请求头、查询参数和请求体。

除了基本的 GET 和 POST 请求外，requests 还支持其他 HTTP 方法，如 PUT、DELETE、HEAD、OPTIONS 等。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Python requests` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
