# Python：Python urllib

- 来源：[Python3 urllib](https://www.runoob.com/python3/python-urllib.html)
- 分类：Python / 数据科学
- 技术：Python
- 笔记类型：学习笔记
- 章节序号：4138

## 本章内容

Python urllib 库用于操作网页 URL，并对网页的内容进行抓取处理。

本文主要介绍 Python3 的 urllib。

urllib 包 包含以下几个模块：

- urllib.request - 打开和读取 URL。
- urllib.error - 包含 urllib.request 抛出的异常。
- urllib.parse - 解析 URL。
- urllib.robotparser - 解析 robots.txt 文件。


## urllib.request

urllib.request 定义了一些打开 URL 的函数和类，包含授权验证、重定向、浏览器 cookies等。

urllib.request 可以模拟浏览器的一个请求发起过程。

我们可以使用 urllib.request 的 urlopen 方法来打开一个 URL，语法格式如下：

```text
urllib.request.urlopen(url, data=None, [timeout, ]*, cafile=None, capath=None, cadefault=False, context=None)
```

- url：url 地址。
- data：发送到服务器的其他数据对象，默认为 None。
- timeout：设置访问超时时间。
- cafile 和 capath：cafile 为 CA 证书， capath 为 CA 证书的路径，使用 HTTPS 需要用到。
- cadefault：已经被弃用。
- context：ssl.SSLContext类型，用来指定 SSL 设置。

实例如下：


## 实例

以上代码使用 urlopen 打开一个 URL，然后使用 read() 函数获取网页的 HTML 实体代码。

read() 是读取整个网页内容，我们可以指定读取的长度：


## 实例

除了 read() 函数外，还包含以下两个读取网页内容的函数：

- readline() - 读取文件的一行内容 from urllib.request import urlopen myURL = urlopen("https://www.runoob.com/") print(myURL.readline()) #读取一行内容
- readlines() - 读取文件的全部内容，它会把读取的内容赋值给一个列表变量。 from urllib.request import urlopen myURL = urlopen("https://www.runoob.com/") lines = myURL.readlines() for line in lines: print(line)

我们在对网页进行抓取时，经常需要判断网页是否可以正常访问，这里我们就可以使用 getcode() 函数获取网页状态码，返回 200 说明网页正常，返回 404 说明网页不存在:


## 实例

更多网页状态码可以查阅：https://www.runoob.com/http/http-status-codes.html。

如果要将抓取的网页保存到本地，可以使用 Python3 File write() 方法 函数：


## 实例

执行以上代码，在本地就会生成一个 runoob_urllib_test.html 文件，里面包含了 https://www.runoob.com/ 网页的内容。

更多Python File 处理，可以参阅：https://www.runoob.com/python3/python3-file-methods.html

URL 的编码与解码可以使用 urllib.request.quote() 与 urllib.request.unquote() 方法：


## 实例

输出结果为：

```text
https%3A//www.runoob.com/
https://www.runoob.com/
```


### 模拟头部信息

我们抓取网页一般需要对 headers（网页头信息）进行模拟，这时候需要使用到 urllib.request.Request 类：

```text
class urllib.request.Request(url, data=None, headers={}, origin_req_host=None, unverifiable=False, method=None)
```

- url：url 地址。
- data：发送到服务器的其他数据对象，默认为 None。
- headers：HTTP 请求的头部信息，字典格式。
- origin_req_host：请求的主机地址，IP 或域名。
- unverifiable：很少用这个参数，用于设置网页是否需要验证，默认是 False。
- method：请求方法， 如 GET、POST、DELETE、PUT等。


## 实例 - py3_urllib_test.py 文件代码

执行以上 Python 代码，会在当前目录生成 urllib_test_runoob_search.html 文件，打开 urllib_test_runoob_search.html 文件（可以使用浏览器打开），内容如下：

表单 POST 传递数据，我们先创建一个表单，代码如下，我这里使用了 PHP 代码来获取表单的数据：


## 实例 - py3_urllib_test.php 文件代码：


## 实例

执行以上代码，会提交表单数据到 py3_urllib_test.php 文件，输出结果写入到 urllib_test_post_runoob.html 文件。

打开 urllib_test_post_runoob.html 文件（可以使用浏览器打开），显示结果如下：


## urllib.error

urllib.error 模块为 urllib.request 所引发的异常定义了异常类，基础异常类是 URLError。

urllib.error 包含了两个方法，URLError 和 HTTPError。

URLError 是 OSError 的一个子类，用于处理程序在遇到问题时会引发此异常（或其派生的异常），包含的属性 reason 为引发异常的原因。

HTTPError 是 URLError 的一个子类，用于处理特殊 HTTP 错误例如作为认证请求的时候，包含的属性 code 为 HTTP 的状态码， reason 为引发异常的原因，headers 为导致 HTTPError 的特定 HTTP 请求的 HTTP 响应头。

对不存在的网页抓取并处理异常:


## 实例


## 复习重点

- 能说明 `Python3 urllib` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
