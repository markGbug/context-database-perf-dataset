# SOAP：SOAP HTTP 协议

- 来源：[SOAP HTTP Binding](https://www.runoob.com/soap/soap-httpbinding.html)
- 分类：XML / Web Service
- 技术：SOAP
- 笔记类型：学习笔记
- 章节序号：4348

## 本章内容

## HTTP 协议

HTTP 在 TCP/IP 之上进行通信。HTTP 客户机使用 TCP 连接到 HTTP 服务器。在建立连接之后，客户机可向服务器发送 HTTP 请求消息：

```text
POST /item HTTP/1.1
Host: 189.123.255.239
Content-Type: text/plain
Content-Length: 200
```

随后服务器会处理此请求，然后向客户机发送一个 HTTP 响应。此响应包含了可指示请求状态的状态代码：

```text
200 OK
Content-Type: text/plain
Content-Length: 200
```

在上面的例子中，服务器返回了一个 200 的状态代码。这是 HTTP 的标准成功代码。

假如服务器无法对请求进行解码，它可能会返回类似这样的信息：

```text
400 Bad Request
Content-Length: 0
```


## SOAP HTTP Binding

SOAP 方法指的是遵守 SOAP 编码规则的 HTTP 请求/响应。


### HTTP + XML = SOAP

SOAP 请求可能是 HTTP POST 或 HTTP GET 请求。

HTTP POST 请求规定至少两个 HTTP 头：Content-Type 和 Content-Length。


## Content-Type

SOAP 的请求和响应的 Content-Type 头可定义消息的 MIME 类型，以及用于请求或响应的 XML 主体的字符编码（可选）。


### 语法

```text
Content-Type: MIMEType; charset=character-encoding
```


### 实例

```text
POST /item HTTP/1.1
Content-Type: application/soap+xml; charset=utf-8
```


## Content-Length

SOAP 的请求和响应的 Content-Length 头规定请求或响应主体的字节数。


### 语法

```text
Content-Length: bytes
```


### 实例

```text
POST /item HTTP/1.1
Content-Type: application/soap+xml; charset=utf-8
Content-Length: 250
```


## 复习重点

- 能说明 `SOAP HTTP Binding` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
