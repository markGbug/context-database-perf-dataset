# 知识点 22845：Servlet：Servlet 实例 - Hello World 示例代码

- 来源：[Servlet 实例](https://www.runoob.com/servlet/servlet-first-example.html)
- 来源章节：[1174-servlet-first-example-practice.md](../chapters/1174-servlet-first-example-practice.md)
- 分类：后端开发
- 技术：Servlet
- 所在小节：Hello World 示例代码
- 知识类型：代码
- 原章节序号：1174

## 原文片段

```text
// 导入必需的 java 库
import java.io.*;
import javax.servlet.*;
import javax.servlet.http.*;

// 扩展 HttpServlet 类
public class HelloWorld extends HttpServlet {

  private String message;

  public void init() throws ServletException
  {
      // 执行必需的初始化
      message = "Hello World";
  }

  public void doGet(HttpServletRequest request,
                    HttpServletResponse response)
            throws ServletException, IOException
  {
      // 设置响应内容类型
      response.setContentType("text/html");

      // 实际的逻辑是在这里
      PrintWriter out = response.getWriter();
      out.println("<h1>" + message + "</h1>");
  }

  public void destroy()
  {
      // 什么也不做
  }
}
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `Hello World 示例代码` 这一小节和 `Servlet 实例` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
