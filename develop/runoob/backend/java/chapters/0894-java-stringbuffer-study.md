# Java：Java StringBuffer 和 StringBuilder 类

- 来源：[Java StringBuffer](https://www.runoob.com/java/java-stringbuffer.html)
- 分类：后端开发
- 技术：Java
- 笔记类型：学习笔记
- 章节序号：0894

## 本章内容

当对字符串进行修改的时候，需要使用 StringBuffer 和 StringBuilder 类。

和 String 类不同的是，StringBuffer 和 StringBuilder 类的对象能够被多次的修改，并且不产生新的未使用对象。

在使用 StringBuffer 类时，每次都会对 StringBuffer 对象本身进行操作，而不是生成新的对象，所以如果需要对字符串进行修改推荐使用 StringBuffer。

StringBuilder 类在 Java 5 中被提出，它和 StringBuffer 之间的最大不同在于 StringBuilder 的方法不是线程安全的（不能同步访问）。

由于 StringBuilder 相较于 StringBuffer 有速度优势，所以多数情况下建议使用 StringBuilder 类。


## 实例

```java
public class RunoobTest{
    public static void main(String[] args){
        StringBuilder sb = new StringBuilder(10);
        sb.append("Runoob..");
        System.out.println(sb);
        sb.append("!");
        System.out.println(sb);
        sb.insert(8, "Java");
        System.out.println(sb);
        sb.delete(5,8);
        System.out.println(sb);
    }
}
```

以上实例编译运行结果如下：

```text
Runoob..
Runoob..!
Runoob..Java!
RunooJava!
```

然而在应用程序要求线程安全的情况下，则必须使用 StringBuffer 类。


## Test.java 文件代码：

```java
public class Test{
  public static void main(String[] args){
    StringBuffer sBuffer = new StringBuffer("菜鸟教程官网：");
    sBuffer.append("www");
    sBuffer.append(".runoob");
    sBuffer.append(".com");
    System.out.println(sBuffer);
  }
}
```

以上实例编译运行结果如下：

```text
菜鸟教程官网：www.runoob.com
```


## StringBuffer 方法

以下是 StringBuffer 类支持的主要方法：

以下列表列出了 StringBuffer 类的其他常用方法：

更多内容：

- StringBuffer 类：https://www.runoob.com/manual/jdk11api/java.base/java/lang/StringBuffer.html
- StringBuilder 类：https://www.runoob.com/manual/jdk11api/java.base/java/lang/StringBuilder.html


## 复习重点

- 能说明 `Java StringBuffer` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
