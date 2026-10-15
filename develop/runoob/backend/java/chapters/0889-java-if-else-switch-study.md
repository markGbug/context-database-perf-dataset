# Java：Java 条件语句 - if...else

- 来源：[Java 条件语句](https://www.runoob.com/java/java-if-else-switch.html)
- 分类：后端开发
- 技术：Java
- 笔记类型：学习笔记
- 章节序号：0889

## 本章内容

Java 中的条件语句允许程序根据条件的不同执行不同的代码块。

一个 if 语句包含一个布尔表达式和一条或多条语句。


### 语法

if 语句的语法如下：

```text
if(布尔表达式)
{
   //如果布尔表达式为true将执行的语句
}
```

如果布尔表达式的值为 true，则执行 if 语句中的代码块，否则执行 else 语句块后面的代码。


## Test.java 文件代码：

```java
public class Test {

   public static void main(String args[]){
      int x = 10;

      if( x < 20 ){
         System.out.print("这是 if 语句");
      }
   }
}
```

以上代码编译运行结果如下：

```text
这是 if 语句
```


## if...else语句

if 语句后面可以跟 else 语句，当 if 语句的布尔表达式值为 false 时，else 语句块会被执行。


### 语法

if…else 的用法如下：

```text
if(布尔表达式){
   //如果布尔表达式的值为true
}else{
   //如果布尔表达式的值为false
}
```


### 实例


## Test.java 文件代码：

```java
public class Test {

   public static void main(String args[]){
      int x = 30;

      if( x < 20 ){
         System.out.print("这是 if 语句");
      }else{
         System.out.print("这是 else 语句");
      }
   }
}
```

以上代码编译运行结果如下：

```text
这是 else 语句
```


## if...else if...else 语句

if 语句后面可以跟 else if…else 语句，这种语句可以检测到多种可能的情况。

使用 if，else if，else 语句的时候，需要注意下面几点：

- if 语句至多有 1 个 else 语句，else 语句在所有的 else if 语句之后。
- if 语句可以有若干个 else if 语句，它们必须在 else 语句之前。
- 一旦其中一个 else if 语句检测为 true，其他的 else if 以及 else 语句都将跳过执行。


### 语法


## 复习重点

- 能说明 `Java 条件语句` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
