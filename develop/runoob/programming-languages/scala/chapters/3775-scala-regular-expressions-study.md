# Scala：Scala 正则表达式

- 来源：[Scala 正则表达式](https://www.runoob.com/scala/scala-regular-expressions.html)
- 分类：编程语言
- 技术：Scala
- 笔记类型：学习笔记
- 章节序号：3775

## 本章内容

Scala 通过 scala.util.matching 包中的 Regex 类来支持正则表达式。以下实例演示了使用正则表达式查找单词 Scala :


## 实例

执行以上代码，输出结果为：

```text
$ scalac Test.scala
$ scala Test
Some(Scala)
```

实例中使用 String 类的 r() 方法构造了一个Regex对象。

然后使用 findFirstIn 方法找到首个匹配项。

如果需要查看所有的匹配项可以使用 findAllIn 方法。

你可以使用 mkString( ) 方法来连接正则表达式匹配结果的字符串，并可以使用管道(|)来设置不同的模式：


## 实例

执行以上代码，输出结果为：

```text
$ scalac Test.scala
$ scala Test
Scala,scala
```

如果你需要将匹配的文本替换为指定的关键词，可以使用 replaceFirstIn( ) 方法来替换第一个匹配项，使用 replaceAllIn( ) 方法替换所有匹配项，实例如下:


## 实例

执行以上代码，输出结果为：

```text
$ scalac Test.scala
$ scala Test
Java is scalable and cool
```


## 正则表达式

Scala 的正则表达式继承了 Java 的语法规则，Java 则大部分使用了 Perl 语言的规则。

下表我们给出了常用的一些正则表达式规则：


## 正则表达式实例

注意上表中的每个字符使用了两个反斜线。这是因为在 Java 和 Scala 中字符串中的反斜线是转义字符。所以如果你要输出 \，你需要在字符串中写成 \\ 来获取一个反斜线。查看以下实例：


## 实例

执行以上代码，输出结果为：

```text
$ scalac Test.scala
$ scala Test
able1
```


## 复习重点

- 能说明 `Scala 正则表达式` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
