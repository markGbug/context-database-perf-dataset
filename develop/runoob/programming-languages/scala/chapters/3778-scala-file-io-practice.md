# Scala：Scala 文件 I/O

- 来源：[Scala 文件 I/O](https://www.runoob.com/scala/scala-file-io.html)
- 分类：编程语言
- 技术：Scala
- 笔记类型：练习笔记
- 章节序号：3778

## 本章内容

Scala 进行文件写操作，直接用的都是 java中 的 I/O 类 （java.io.File)：


## 实例

执行以上代码，会在你的当前目录下生产一个 test.txt 文件，文件内容为"菜鸟教程":

```text
$ scalac Test.scala
$ scala Test
$ cat test.txt
菜鸟教程
```


## 从屏幕上读取用户输入

有时候我们需要接收用户在屏幕输入的指令来处理程序。实例如下：


## 实例

Scala2.11 后的版本 Console.readLine 已废弃，使用 scala.io.StdIn.readLine() 方法代替。

执行以上代码，屏幕上会显示如下信息:

```text
$ scalac Test.scala
$ scala Test
请输入菜鸟教程官网 : www.runoob.com
谢谢，你输入的是: www.runoob.com
```


## 从文件上读取内容

从文件读取内容非常简单。我们可以使用 Scala 的 Source 类及伴生对象来读取文件。以下实例演示了从 "test.txt"(之前已创建过) 文件中读取内容:


## 实例

执行以上代码，输出结果为:

```text
$ scalac Test.scala
$ scala Test
文件内容为:
菜鸟教程
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Scala 文件 I/O` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
