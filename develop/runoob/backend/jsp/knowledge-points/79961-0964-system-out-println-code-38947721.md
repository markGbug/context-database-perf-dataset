# 知识点 79961：JSP：JSP 调试 - 使用System.out.println()

- 来源：[JSP 调试](https://www.runoob.com/jsp/jsp-debugging.html)
- 来源章节：[0964-jsp-debugging-practice.md](../chapters/0964-jsp-debugging-practice.md)
- 分类：后端开发
- 技术：JSP
- 所在小节：使用System.out.println()
- 知识类型：代码
- 原章节序号：0964

## 原文片段

```text
<%@taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<html>
<head><title>System.out.println</title></head>
<body>
<c:forEach var="counter" begin="1" end="10" step="1" >
   <c:out value="${counter-5}"/></br>
   <% System.out.println( "counter= " +
                     pageContext.findAttribute("counter") ); %>
</c:forEach>
</body>
</html>
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `使用System.out.println()` 这一小节和 `JSP 调试` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
