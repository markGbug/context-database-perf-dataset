# Servlet：Servlet 客户端 HTTP 请求

- 来源：[Servlet 客户端 HTTP 请求](https://www.runoob.com/servlet/servlet-client-request.html)
- 分类：后端开发
- 技术：Servlet
- 笔记类型：学习笔记
- 章节序号：1176

## 本章内容

当浏览器请求网页时，它会向 Web 服务器发送特定信息，这些信息不能被直接读取，因为这些信息是作为 HTTP 请求的头的一部分进行传输的。您可以查看 HTTP 协议 了解更多相关信息。

以下是来自于浏览器端的重要头信息，您可以在 Web 编程中频繁使用：


## 读取 HTTP 头的方法

下面的方法可用在 Servlet 程序中读取 HTTP 头。这些方法通过 HttpServletRequest 对象可用。


## HTTP Header 请求实例

下面的实例使用 HttpServletRequest 的 getHeaderNames() 方法读取 HTTP 头信息。该方法返回一个枚举，包含与当前的 HTTP 请求相关的头信息。

一旦我们有一个枚举，我们可以以标准方式循环枚举，使用 hasMoreElements() 方法来确定何时停止，使用 nextElement() 方法来获取每个参数的名称。

```java
//导入必需的 java 库
import java.io.IOException;
import java.io.PrintWriter;
import java.util.Enumeration;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

@WebServlet("/DisplayHeader")

//扩展 HttpServlet 类
public class DisplayHeader extends HttpServlet {

    // 处理 GET 方法请求的方法
    public void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException
    {
        // 设置响应内容类型
        response.setContentType("text/html;charset=UTF-8");

        PrintWriter out = response.getWriter();
        String title = "HTTP Header 请求实例 - 菜鸟教程实例";
        String docType =
            "<!DOCTYPE html> \n";
            out.println(docType +
            "<html>\n" +
            "<head><meta charset=\"utf-8\"><title>" + title + "</title></head>\n"+
            "<body bgcolor=\"#f0f0f0\">\n" +
            "<h1 align=\"center\">" + title + "</h1>\n" +
            "<table width=\"100%\" border=\"1\" align=\"center\">\n" +
            "<tr bgcolor=\"#949494\">\n" +
            "<th>Header 名称</th><th>Header 值</th>\n"+
            "</tr>\n");

        Enumeration headerNames = request.getHeaderNames();

        while(headerNames.hasMoreElements()) {
            String paramName = (String)headerNames.nextElement();
            out.print("<tr><td>" + paramName + "</td>\n");
            String paramValue = request.getHeader(paramName);
            out.println("<td> " + paramValue + "</td></tr>\n");
        }
        out.println("</table>\n</body></html>");
    }
    // 处理 POST 方法请求的方法
    public void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
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
    <servlet-name>DisplayHeader</servlet-name>
    <!-- 所在的包 -->
    <servlet-class>com.runoob.test.DisplayHeader</servlet-class>
  </servlet>
  <servlet-mapping>
    <servlet-name>DisplayHeader</servlet-name>
    <!-- 访问的网址 -->
    <url-pattern>/TomcatTest/DisplayHeader</url-pattern>
  </servlet-mapping>
</web-app>
```

现在，调用上面的 Servlet，访问 http://localhost:8080/TomcatTest/DisplayHeader 会产生以下结果：


## 复习重点

- 能说明 `Servlet 客户端 HTTP 请求` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
