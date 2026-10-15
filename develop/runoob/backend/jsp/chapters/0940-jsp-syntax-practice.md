# JSP：JSP 语法

- 来源：[JSP 语法](https://www.runoob.com/jsp/jsp-syntax.html)
- 分类：后端开发
- 技术：JSP
- 笔记类型：练习笔记
- 章节序号：0940

## 本章内容

本小节将会简单地介绍一下JSP开发中的基础语法。


## 脚本程序

脚本程序可以包含任意量的Java语句、变量、方法或表达式，只要它们在脚本语言中是有效的。

脚本程序的语法格式：

```text
<% 代码片段 %>
```

或者，您也可以编写与其等价的XML语句，就像下面这样：

```html
<jsp:scriptlet>
   代码片段
</jsp:scriptlet>
```

任何文本、HTML标签、JSP元素必须写在脚本程序的外面。

下面给出一个示例，同时也是本教程的第一个JSP示例：

```html
<html>
<head><title>Hello World</title></head>
<body>
Hello World!<br/>
<%
out.println("Your IP address is " + request.getRemoteAddr());
%>
</body>
</html>
```

注意：请确保Apache Tomcat已经安装在C:\apache-tomcat-7.0.2目录下并且运行环境已经正确设置。

将以上代码保存在hello.jsp中，然后将它放置在 C:\apache-tomcat-7.0.2\webapps\ROOT目录下，打开浏览器并在地址栏中输入http://localhost:8080/hello.jsp。运行后得到以下结果：


### 中文编码问题


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `JSP 语法` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
