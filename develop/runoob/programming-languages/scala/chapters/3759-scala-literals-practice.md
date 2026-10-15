# Scala：Scala 字面量

- 来源：[Scala 字面量](https://www.runoob.com/scala/scala-literals.html)
- 分类：编程语言
- 技术：Scala
- 笔记类型：练习笔记
- 章节序号：3759

## 本章内容

在 Scala 中，字面量（Literals）是直接表示固定值的表达式。

Scala支持各种类型的字面量，涵盖了数值、字符、字符串、布尔值等。


### 整型字面量

整型字面量用于 Int 类型，如果表示 Long，可以在数字后面添加 L 或者小写 l 作为后缀。

整型字面量可以是十进制、十六进制和八进制。

- 十进制：42, 0, -99
- 十六进制：以0x或0X开头，如0x2A, 0x0, 0XFF
- 八进制：Scala 2.10 之前支持八进制字面量，以 0 开头，但在 Scala 2.10 及之后的版本中，八进制字面量被移除。

```text
val decimal = 42
val hex = 0x2A
```


### 浮点型字面量

如果浮点数后面有 f 或者 F 后缀时，表示这是一个 Float 类型，否则就是一个 Double 类型的。

- 双精度：3.14, -0.001, 1.0e-10
- 单精度：3.14f, -0.001F

```text
val doubleValue = 3.14
val floatValue = 3.14f
```


### 布尔型字面量

布尔型字面量有 true 和 false。

```text
val isScalaFun = true
val isSkyGreen = false
```


### 符号字面量

符号字面量被写成： '<标识符> ，这里 <标识符> 可以是任何字母或数字的标识（注意：不能以数字开头）。这种字面量被映射成预定义类 scala.Symbol 的实例。

如：符号字面量 'x 是表达式 scala.Symbol("x") 的简写，符号字面量定义如下：

```text
package scala
final case class Symbol private (name: String) {
   override def toString: String = "'" + name
}
```


### 字符字面量

在 Scala 字符变量使用单引号 ' 来定义，如下：

```text
'a'
'\u0041'
'\n'
'\t'
```

其中 \ 表示转义字符，其后可以跟 u0041 数字或者 \r\n 等固定的转义字符。


### 字符串字面量

在 Scala 字符串字面量使用双引号 " 来定义，如下：

```text
"Hello,\nWorld!"
"菜鸟教程官网：www.runoob.com"
```

- 普通字符串："Hello, World!"
- 多行字符串：使用三重引号 """ 括起来，可以包含换行符和引号。


### 多行字符串的表示方法

多行字符串用三个双引号来表示分隔符，格式为：""" ... """。

实例如下：

```text
val foo = """菜鸟教程
www.runoob.com
www.runnoob.com
以上三个地址都能访问"""
```


### Null 值

Null是一个特殊的字面量，表示所有引用类型的空值。

空值是 scala.Null 类型。

Scala.Null 和 scala.Nothing 是用统一的方式处理 Scala 面向对象类型系统的某些"边界情况"的特殊类型。

Null 类是 null 引用对象的类型，它是每个引用类（继承自AnyRef的类）的子类。Null不兼容值类型。

```text
val nullValue: String = null
```


### Unit

Unit 类型只有一个实例值，用字面量 () 表示，类似于 Java 中的 void。

```text
val unitValue: Unit = ()
```


### 实例

以下是使用不同类型字面量的示例代码：


## 实例

以上代码编译执行结果为：

```text
Decimal: 42, Hex: 42
Double: 3.14, Float: 3.14
Char: A, New Line:

Greeting: Hello, World!
Multiline String: This is
a multi-line
string
Is Scala Fun: true, Is Sky Green: false
Null Value: null, Unit Value: ()
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Scala 字面量` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
