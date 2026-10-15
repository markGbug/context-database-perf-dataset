# 知识点 80335：Servlet：Servlet 服务器 HTTP 响应 - HTTP Header 响应实例

- 来源：[Servlet 服务器 HTTP 响应](https://www.runoob.com/servlet/servlet-server-response.html)
- 来源章节：[1177-servlet-server-response-practice.md](../chapters/1177-servlet-server-response-practice.md)
- 分类：后端开发
- 技术：Servlet
- 所在小节：HTTP Header 响应实例
- 知识类型：代码
- 原章节序号：1177

## 原文片段

```text
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

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `HTTP Header 响应实例` 这一小节和 `Servlet 服务器 HTTP 响应` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
