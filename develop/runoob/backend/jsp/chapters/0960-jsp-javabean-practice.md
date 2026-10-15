# JSP：JSP JavaBean

- 来源：[JSP JavaBean](https://www.runoob.com/jsp/jsp-javabean.html)
- 分类：后端开发
- 技术：JSP
- 笔记类型：练习笔记
- 章节序号：0960

## 本章内容

JavaBean 是特殊的 Java 类，使用 Java 语言书写，并且遵守 JavaBean API 规范。

接下来给出的是 JavaBean 与其它 Java 类相比而言独一无二的特征：

- 提供一个默认的无参构造函数。
- 需要被序列化并且实现了 Serializable 接口。
- 可能有一系列可读写属性。
- 可能有一系列的 getter 或 setter 方法。


## JavaBean 属性

一个 JavaBean 对象的属性应该是可访问的。这个属性可以是任意合法的 Java 数据类型，包括自定义 Java 类。

一个 JavaBean 对象的属性可以是可读写，或只读，或只写。JavaBean 对象的属性通过 JavaBean 实现类中提供的两个方法来访问：

一个只读的属性只提供 getPropertyName() 方法，一个只写的属性只提供 setPropertyName() 方法。


## JavaBean 程序示例

这是 StudentBean.java 文件：

```java
package com.runoob;

public class StudentsBean implements java.io.Serializable
{
   private String firstName = null;
   private String lastName = null;
   private int age = 0;

   public StudentsBean() {
   }
   public String getFirstName(){
      return firstName;
   }
   public String getLastName(){
      return lastName;
   }
   public int getAge(){
      return age;
   }

   public void setFirstName(String firstName){
      this.firstName = firstName;
   }
   public void setLastName(String lastName){
      this.lastName = lastName;
   }
   public void setAge(int age) {
      this.age = age;
   }
}
```

编译 StudentBean.java 文件(最后一个实例会用到):

```text
$ javac StudentsBean.java
```

编译后获得 StudentBean.class 文件，将其拷贝到 <JSP 项目>/WebContent/WEB-INF/classes/com/runoob，如下图所示:


## 访问JavaBean

<jsp:useBean> 标签可以在 JSP 中声明一个 JavaBean，然后使用。声明后，JavaBean 对象就成了脚本变量，可以通过脚本元素或其他自定义标签来访问。<jsp:useBean> 标签的语法格式如下：

```html
<jsp:useBean id="bean 的名字" scope="bean 的作用域" typeSpec/>
```

其中，根据具体情况，scope 的值可以是 page，request，session 或 application。id值可任意只要不和同一 JSP 文件中其它 <jsp:useBean> 中 id 值一样就行了。

接下来给出的是 <jsp:useBean> 标签的一个简单的用法：

```html
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<html>
<head>
<title>useBean 实例</title>
</head>
<body>

<jsp:useBean id="date" class="java.util.Date" />
<p>日期为：<%= date %>

</body>
</html>
```

它将会产生如下结果：

```text
日期为：Tue Jun 28 15:22:24 CST 2016
```


## 访问 JavaBean 对象的属性

在 <jsp:useBean> 标签主体中使用 <jsp:getProperty/> 标签来调用 getter 方法，使用 <jsp:setProperty/> 标签来调用 setter 方法，语法格式如下：

```html
<jsp:useBean id="id" class="bean 编译的类" scope="bean 作用域">
   <jsp:setProperty name="bean 的 id" property="属性名"
                    value="value"/>
   <jsp:getProperty name="bean 的 id" property="属性名"/>
   ...........
</jsp:useBean>
```

name属性指的是Bean的id属性。property属性指的是想要调用的getter或setter方法。

接下来给出使用以上语法进行属性访问的一个简单例子：

```html
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<html>
<head>
<title>get 和 set 属性实例</title>
</head>
<body>

<jsp:useBean id="students"
                    class="com.runoob.StudentsBean">
   <jsp:setProperty name="students" property="firstName"
                    value="小强"/>
   <jsp:setProperty name="students" property="lastName"
                    value="王"/>
   <jsp:setProperty name="students" property="age"
                    value="10"/>
</jsp:useBean>

<p>学生名字:
   <jsp:getProperty name="students" property="firstName"/>
</p>
<p>学生姓氏:
   <jsp:getProperty name="students" property="lastName"/>
</p>
<p>学生年龄:
   <jsp:getProperty name="students" property="age"/>
</p>

</body>
</html>
```

访问以上 JSP，运行结果如下：

```text
学生名字: 小强

学生姓氏: 王

学生年龄: 10
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `JSP JavaBean` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
