# 知识点 61763：Servlet：Servlet 服务器 HTTP 响应 - HTTP Header 响应实例

- 来源：[Servlet 服务器 HTTP 响应](https://www.runoob.com/servlet/servlet-server-response.html)
- 来源章节：[1177-servlet-server-response-practice.md](../chapters/1177-servlet-server-response-practice.md)
- 分类：后端开发
- 技术：Servlet
- 所在小节：HTTP Header 响应实例
- 知识类型：代码
- 原章节序号：1177

## 原文片段

```text
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

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `HTTP Header 响应实例` 这一小节和 `Servlet 服务器 HTTP 响应` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
