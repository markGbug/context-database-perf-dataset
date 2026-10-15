# Scala：Scala 字符串

- 来源：[Scala 字符串](https://www.runoob.com/scala/scala-strings.html)
- 分类：编程语言
- 技术：Scala
- 笔记类型：练习笔记
- 章节序号：3768

## 本章内容

以下实例将字符串赋值给一个常量：


## 实例

以上实例定义了变量 greeting，为字符串常量，它的类型为 String (java.lang.String)。

在 Scala 中，字符串的类型实际上是 Java String，它本身没有 String 类。

在 Scala 中，String 是一个不可变的对象，所以该对象不可被修改。这就意味着你如果修改字符串就会产生一个新的字符串对象。

但其他对象，如数组就是可变的对象。接下来我们会为大家介绍常用的 java.lang.String 方法。


## 创建字符串

创建字符串实例如下：

```text
val greeting = "Hello World!";

或

val greeting:String = "Hello World!";
```

你不一定为字符串指定 String 类型，因为 Scala 编译器会自动推断出字符串的类型为 String。

当然我们也可以直接显示的声明字符串为 String 类型，如下实例：


## 实例

执行以上代码，输出结果为：

```text
$ scalac Test.scala
$ scala Test
Hello, world!
```

我们前面提到过 String 对象是不可变的，如果你需要创建一个可以修改的字符串，可以使用 String Builder 类，如下实例:


## 实例

执行以上代码，输出结果为：

```text
$ scalac Test.scala
$ scala Test
buf is : abcdef
```


## 字符串长度

我们可以使用 length() 方法来获取字符串长度：


## 实例

执行以上代码，输出结果为：

```text
$ scalac Test.scala
$ scala Test
String Length is : 14
```


## 字符串连接

String 类中使用 concat() 方法来连接两个字符串：

```text
string1.concat(string2);
```

实例演示：

```text
scala> "菜鸟教程官网： ".concat("www.runoob.com");
res0: String = 菜鸟教程官网： www.runoob.com
```

同样你也可以使用加号(+)来连接：

```text
scala> "菜鸟教程官网： " + " www.runoob.com"
res1: String = 菜鸟教程官网：  www.runoob.com
```

让我们看个完整实例:


## 实例

执行以上代码，输出结果为：

```text
$ scalac Test.scala
$ scala Test
菜鸟教程官网：www.runoob.com
菜鸟教程的 Slogan 为：学的不仅是技术，更是梦想！
```


## 创建格式化字符串

String 类中你可以使用 printf() 方法来格式化字符串并输出，String format() 方法可以返回 String 对象而不是 PrintStream 对象。以下实例演示了 printf() 方法的使用：


## 实例

执行以上代码，输出结果为：

```text
$ scalac Test.scala
$ scala Test
浮点型变量为 12.456000, 整型变量为 2000, 字符串为  菜鸟教程!()
```


## String 方法

下表列出了 java.lang.String 中常用的方法，你可以在 Scala 中使用：

char charAt(int index)

返回指定位置的字符

int compareTo(Object o)

比较字符串与对象

int compareTo(String anotherString)

按字典顺序比较两个字符串

int compareToIgnoreCase(String str)

按字典顺序比较两个字符串，不考虑大小写

String concat(String str)

将指定字符串连接到此字符串的结尾

boolean contentEquals(StringBuffer sb)

将此字符串与指定的 StringBuffer 比较。

static String copyValueOf(char[] data)

返回指定数组中表示该字符序列的 String

static String copyValueOf(char[] data, int offset, int count)

返回指定数组中表示该字符序列的 String

boolean endsWith(String suffix)

测试此字符串是否以指定的后缀结束

boolean equals(Object anObject)

将此字符串与指定的对象比较

boolean equalsIgnoreCase(String anotherString)

将此 String 与另一个 String 比较，不考虑大小写

byte getBytes()

使用平台的默认字符集将此 String 编码为 byte 序列，并将结果存储到一个新的 byte 数组中

byte[] getBytes(String charsetName

使用指定的字符集将此 String 编码为 byte 序列，并将结果存储到一个新的 byte 数组中

void getChars(int srcBegin, int srcEnd, char[] dst, int dstBegin)


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Scala 字符串` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
