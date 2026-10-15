# JSP：JSP HTTP 状态码

- 来源：[JSP HTTP 状态码](https://www.runoob.com/jsp/jsp-http-status-codes.html)
- 分类：后端开发
- 技术：JSP
- 笔记类型：学习笔记
- 章节序号：0946

## 本章内容

HTTP请求与HTTP响应的格式相近，都有着如下结构：

- 以状态行+CRLF（回车换行）开始
- 零行或多行头模块+CRLF
- 一个空行，比如CRLF
- 可选的消息体比如文件，查询数据，查询输出

举例来说，一个服务器响应头看起来就像下面这样：

```html
HTTP/1.1 200 OK
Content-Type: text/html
Header2: ...
...
HeaderN: ...
  (Blank Line)
<!doctype ...>
<html>
<head>...</head>
<body>
...
</body>
</html>
```

下表列出了可能会从服务器返回的HTTP状态码和与之关联的消息：


## 设置HTTP状态码的方法

下表列出了HttpServletResponse 类中用来设置状态码的方法：


## HTTP状态码程序示例

接下来的例子将会发送407错误码给浏览器，然后浏览器将会告诉您"Need authentication!!!"。

```html
<html>
<head>
<title>Setting HTTP Status Code</title>
</head>
<body>
<%
   // 设置错误代码，并说明原因
   response.sendError(407, "Need authentication!!!" );
%>
</body>
</html>
```

访问以上JSP页面，将会得到以下结果：

您也可以试试使用其他的状态码，看会不会得到什么意想不到结果。


## 复习重点

- 能说明 `JSP HTTP 状态码` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
