# JSP：JSP 页面重定向

- 来源：[JSP 页面重定向](https://www.runoob.com/jsp/jsp-page-redirect.html)
- 分类：后端开发
- 技术：JSP
- 笔记类型：学习笔记
- 章节序号：0953

## 本章内容

当需要将文档移动到一个新的位置时，就需要使用JSP重定向了。

最简单的重定向方式就是使用response对象的sendRedirect()方法。这个方法的签名如下：

```text
public void response.sendRedirect(String location)
throws IOException
```

这个方法将状态码和新的页面位置作为响应发回给浏览器。您也可以使用setStatus()和setHeader()方法来得到同样的效果：

```text
....
String site = "http://www.runoob.com" ;
response.setStatus(response.SC_MOVED_TEMPORARILY);
response.setHeader("Location", site);
....
```


## 实例演示

这个例子表明了JSP如何进行页面重定向：

```html
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<%@ page import="java.io.*,java.util.*" %>
<html>
<html>
<head>
<title>页面重定向</title>
</head>
<body>

<h1>页面重定向</h1>

<%
   // 重定向到新地址
   String site = new String("http://www.runoob.com");
   response.setStatus(response.SC_MOVED_TEMPORARILY);
   response.setHeader("Location", site);
%>

</body>
</html>
```

将以上代码保存在PageRedirecting.jsp文件中，然后访问http://localhost:8080/PageRedirect.jsp，它将会把您带至http://www.runoob.com/。


## 复习重点

- 能说明 `JSP 页面重定向` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
