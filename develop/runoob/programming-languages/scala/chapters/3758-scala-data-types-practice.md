# Scala：Scala 数据类型

- 来源：[Scala 数据类型](https://www.runoob.com/scala/scala-data-types.html)
- 分类：编程语言
- 技术：Scala
- 笔记类型：练习笔记
- 章节序号：3758

## 本章内容

Scala 支持的主要数据类型包括基本类型、集合类型、和特殊类型。

下表列出了 Scala 支持的数据类型：

在 Scala 中，所有数据类型都是对象。

Scala 没有像 Java 中的原生类型（primitive types）那样的概念。尽管 Scala 的基本数据类型（如 Int、Double 等）在语法上看起来类似于 Java 的原生类型，但它们实际上是对象。这意味着你可以在这些类型上调用方法。

例如，Int 类型在 Scala 中实际上是 scala.Int 类的一个实例，而 scala.Int 是一个最终类，继承自 AnyVal。AnyVal 是 Scala 中的一个特殊类，表示值类型。

下面是一个完整的 Scala 程序，展示了各种数据类型的使用：


## DataTypeExamples.scala 文件代码：

使用 scalac 编译器进行编译，使用 scala 命令运行：

```text
scalac DataTypeExamples.scala
scala DataTypeExamples
```

输出结果:

```text
Byte Value: 127
Short Value: 32767
Int Value: 2147483647
Long Value: 9223372036854775807
Float Value: 3.14
Double Value: 3.141592653589793
Char Value: A
String Value: Hello, Scala!
Boolean Value: true
List Value: List(1, 2, 3)
Set Value: Set(Scala, Java, Python)
Map Value: Map(one -> 1, two -> 2, three -> 3)
Array Value: 4, 5, 6
Tuple Value: (42,Answer,true)
Option Value: Some(I am here)
Either Value: Right(42)
Try Value: Success(5)
Unit Value: ()
Null Value: null
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Scala 数据类型` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
