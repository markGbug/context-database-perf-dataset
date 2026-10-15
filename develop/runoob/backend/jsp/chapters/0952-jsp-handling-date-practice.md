# JSP：JSP 日期处理

- 来源：[JSP 日期处理](https://www.runoob.com/jsp/jsp-handling-date.html)
- 分类：后端开发
- 技术：JSP
- 笔记类型：练习笔记
- 章节序号：0952

## 本章内容

使用JSP最重要的优势之一，就是可以使用所有Java API。本章将会详细地讲述Java中的Date类，它在java.util包下，封装了当前日期和时间。

Date类有两个构造函数。第一个构造函数使用当前日期和时间来初始化对象。

```text
Date( )
```

第二个构造函数接受一个参数，这个参数表示从1970年1月1日凌晨至所要表示时间的毫秒数。

```text
Date(long millisec)
```

获取Date对象后，您就能够使用下表列出的所有方法：


## 获取当前日期和时间

使用JSP编程可以很容易的获取当前日期和时间，只要使用Date对象的toString()方法就行了，就像下面这样：

```html
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<%@ page import="java.io.*,java.util.*, javax.servlet.*" %>
<html>
<head>
<title>显示当前时间与日期</title>
</head>
<body>

<h1>显示当前时间与日期</h1>

<%
   Date date = new Date();
   out.print( "<h2 align=\"center\">" +date.toString()+"</h2>");
%>
</body>
</html>
```

将上面的代码保存在 main.jsp 文件中，然后访问 http://localhost:8080/testjsp/main.jsp，运行结果如下：

```text
显示当前时间与日期

Sat Jun 25 17:54:34 CST 2016
```

刷新 http://localhost:8080/testjsp/main.jsp，就可以发现每次刷新所得到的秒数都不相同。


## 日期比较

就像我在开头所提到的，您可以在JSP脚本中使用任何Java方法。如果您想要比较两个日期，

可以参照下面的方法来做：

- 使用getTime()方法得到毫秒数，然后比较毫秒数就行了。
- 使用before()，after()，equals()方法。比如，new Date(99,2,12).before(new Date(99,2,18))返回true。
- 使用compareTo()方法，这个方法在Comparable接口中定义，在Date中实现。


## 使用SimpleDateFormat格式化日期

SimpleDateFormat使用一种地区敏感的方式来格式化和解析日期，它允许您使用自定义的模式来格式化日期和时间。

对CurrentDate.jsp稍作修改，得到如下修改后的代码：

```html
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<%@ page import="java.io.*,java.util.*" %>
<%@ page import="javax.servlet.*,java.text.*" %>
<html>
<head>
<title>显示当前时间与日期</title>
</head>
<body>

<h1>显示当前时间与日期</h1>

<%
   Date dNow = new Date( );
   SimpleDateFormat ft =
   new SimpleDateFormat ("yyyy-MM-dd HH:mm:ss");
   out.print( "<h2 align=\"center\">" + ft.format(dNow) + "</h2>");
%>

</body>
</html>
```

再次编译 main.jsp，然后访问 http://localhost:8080/testjsp/main.jsp，就可以得到如下结果：

```text
显示当前时间与日期

2016-06-25 17:57:53
```


## SimpleDateFormat格式码

要指定模式字符串，需要使用下表列出的格式码：

更多关于Date类的详细信息请查阅Java API文档。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `JSP 日期处理` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
