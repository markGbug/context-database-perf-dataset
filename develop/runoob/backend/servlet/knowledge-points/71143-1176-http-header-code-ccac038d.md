# 知识点 71143：Servlet：Servlet 客户端 HTTP 请求 - HTTP Header 请求实例

- 来源：[Servlet 客户端 HTTP 请求](https://www.runoob.com/servlet/servlet-client-request.html)
- 来源章节：[1176-servlet-client-request-study.md](../chapters/1176-servlet-client-request-study.md)
- 分类：后端开发
- 技术：Servlet
- 所在小节：HTTP Header 请求实例
- 知识类型：代码
- 原章节序号：1176

## 原文片段

```text
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

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `HTTP Header 请求实例` 这一小节和 `Servlet 客户端 HTTP 请求` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
