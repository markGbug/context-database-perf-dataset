# Servlet：Servlet 服务器 HTTP 响应

- 来源：[Servlet 服务器 HTTP 响应](https://www.runoob.com/servlet/servlet-server-response.html)
- 分类：后端开发
- 技术：Servlet
- 笔记类型：学习笔记
- 章节序号：1177

## 本章内容

正如前面的章节中讨论的那样，当一个 Web 服务器响应一个 HTTP 请求时，响应通常包括一个状态行、一些响应报头、一个空行和文档。一个典型的响应如下所示：

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

状态行包括 HTTP 版本（在本例中为 HTTP/1.1）、一个状态码（在本例中为 200）和一个对应于状态码的短消息（在本例中为 OK）。

下表总结了从 Web 服务器端返回到浏览器的最有用的 HTTP 1.1 响应报头，您会在 Web 编程中频繁地使用它们：


## 设置 HTTP 响应报头的方法

下面的方法可用于在 Servlet 程序中设置 HTTP 响应报头。这些方法通过 HttpServletResponse 对象可用。


## HTTP Header 响应实例

您已经在前面的实例中看到 setContentType() 方法，下面的实例也使用了同样的方法，此外，我们会用 setIntHeader() 方法来设置 Refresh 头。

```java
//导入必需的 java 库
import java.io.IOException;
import java.io.PrintWriter;
import java.text.SimpleDateFormat;
import java.util.Calendar;
import java.util.Date;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

@WebServlet("/Refresh")

//扩展 HttpServlet 类
public class Refresh extends HttpServlet {

    // 处理 GET 方法请求的方法
      public void doGet(HttpServletRequest request,
                        HttpServletResponse response)
                throws ServletException, IOException
      {
          // 设置刷新自动加载时间为 5 秒
          response.setIntHeader("Refresh", 5);
          // 设置响应内容类型
          response.setContentType("text/html;charset=UTF-8");

          //使用默认时区和语言环境获得一个日历
          Calendar cale = Calendar.getInstance();
          //将Calendar类型转换成Date类型
          Date tasktime=cale.getTime();
          //设置日期输出的格式
          SimpleDateFormat df=new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
          //格式化输出
          String nowTime = df.format(tasktime);
          PrintWriter out = response.getWriter();
          String title = "自动刷新 Header 设置 - 菜鸟教程实例";
          String docType =
          "<!DOCTYPE html>\n";
          out.println(docType +
            "<html>\n" +
            "<head><title>" + title + "</title></head>\n"+
            "<body bgcolor=\"#f0f0f0\">\n" +
            "<h1 align=\"center\">" + title + "</h1>\n" +
            "<p>当前时间是：" + nowTime + "</p>\n");
      }
      // 处理 POST 方法请求的方法
      public void doPost(HttpServletRequest request,
                         HttpServletResponse response)
          throws ServletException, IOException {
         doGet(request, response);
      }
}
```

以上测试实例是位于 TomcatTest 项目下，对应的 web.xml 配置为：

```html
<?xml version="1.0" encoding="UTF-8"?>
<web-app>
  <servlet>
     <!-- 类名 -->
    <servlet-name>Refresh</servlet-name>
    <!-- 所在的包 -->
    <servlet-class>com.runoob.test.Refresh</servlet-class>
  </servlet>
  <servlet-mapping>
    <servlet-name>Refresh</servlet-name>
    <!-- 访问的网址 -->
    <url-pattern>/TomcatTest/Refresh</url-pattern>
    </servlet-mapping>
</web-app>
```

现在，调用上面的 Servlet，每隔 5 秒会显示当前系统时间。只要运行 Servlet 并稍等片刻，即可看到如下的结果：


## 复习重点

- 能说明 `Servlet 服务器 HTTP 响应` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
