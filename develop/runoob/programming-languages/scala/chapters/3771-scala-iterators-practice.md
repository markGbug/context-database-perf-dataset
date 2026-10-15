# Scala：Scala Iterator（迭代器）

- 来源：[Scala Iterator（迭代器）](https://www.runoob.com/scala/scala-iterators.html)
- 分类：编程语言
- 技术：Scala
- 笔记类型：练习笔记
- 章节序号：3771

## 本章内容

Scala 集合

Scala Iterator（迭代器）不是一个集合，它是一种用于访问集合的方法。

迭代器 it 的两个基本操作是 next 和 hasNext。

调用 it.next() 会返回迭代器的下一个元素，并且更新迭代器的状态。

调用 it.hasNext() 用于检测集合中是否还有元素。

让迭代器 it 逐个返回所有元素最简单的方法是使用 while 循环：


## 实例

执行以上代码，输出结果为：

```text
$ scalac Test.scala
$ scala Test
Baidu
Google
Runoob
Taobao
```


## 查找最大与最小元素

你可以使用 it.min 和 it.max 方法从迭代器中查找最大与最小元素，实例如下:


## 实例

执行以上代码，输出结果为：

```text
$ scalac Test.scala
$ scala Test
最大元素是：90
最小元素是：2
```


## 获取迭代器的长度

你可以使用 it.size 或 it.length 方法来查看迭代器中的元素个数。实例如下：


## 实例

执行以上代码，输出结果为：

```text
$ scalac Test.scala
$ scala Test
ita.size 的值: 6
itb.length 的值: 6
```


## Scala Iterator 常用方法

下表列出了 Scala Iterator 常用的方法：

def hasNext: Boolean

如果还有可返回的元素，返回true。

def next(): A

返回迭代器的下一个元素，并且更新迭代器的状态

def ++(that: => Iterator[A]): Iterator[A]

合并两个迭代器

def ++[B >: A](that :=> GenTraversableOnce[B]): Iterator[B]

合并两个迭代器

def addString(b: StringBuilder): StringBuilder

添加一个字符串到 StringBuilder b

def addString(b: StringBuilder, sep: String): StringBuilder

添加一个字符串到 StringBuilder b，并指定分隔符

def buffered: BufferedIterator[A]

迭代器都转换成 BufferedIterator

def contains(elem: Any): Boolean

检测迭代器中是否包含指定元素

def copyToArray(xs: Array[A], start: Int, len: Int): Unit

将迭代器中选定的值传给数组

def count(p: (A) => Boolean): Int

返回迭代器元素中满足条件p的元素总数。

def drop(n: Int): Iterator[A]

返回丢弃前n个元素新集合

def dropWhile(p: (A) => Boolean): Iterator[A]

从左向右丢弃元素，直到条件p不成立

def duplicate: (Iterator[A], Iterator[A])

生成两个能分别返回迭代器所有元素的迭代器。

def exists(p: (A) => Boolean): Boolean


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Scala Iterator（迭代器）` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
