# Scala：Scala 转义字符

- 来源：[Scala 转义字符](https://www.runoob.com/scala/scala-escape-char.html)
- 分类：编程语言
- 技术：Scala
- 笔记类型：练习笔记
- 章节序号：3760

## 本章内容

在 Scala 中，转义字符用于表示无法直接在字符串字面量中书写的特殊字符。

转义字符以反斜杠 \ 开头，紧跟一个特定的字符，表示某种特殊含义或效果。

下表列出了常见的转义字符：

在字符或字符串中，0 到 255 间的 Unicode 字符可以用一个八进制转义序列来表示，即反斜杠 \ 后跟最多三位八进制数字。

如果反斜杠 \ 后面的字符序列不能构成一个合法的转义序列，将会导致编译错误。

以下实例演示了一些转义字符的使用：


## 实例

执行以上代码输出结果如下所示：

```text
$ scalac Test.scala
$ scala Test
Hello    World
```

以下是一个展示各种转义字符使用的 Scala 程序示例：


## 实例

执行上述代码，输出结果如下：

```text
Backspace: HelloWorld
Tab: Hello    World
Newline: Hello
World
FormFeed: Hello
World
CarriageReturn: World
DoubleQuote: He said, "Hello, World!"
SingleQuote: "
Backslash: This is a backslash: \
```

实例说明：

- \b (退格符): 使光标回退一个位置，但不会删除字符。例如，"Hello\bWorld" 结果为 HelloWorld，这里的并不删除 "o"，所以实际显示效果取决于终端或输出设备。
- \t (制表符): 插入一个水平制表符，相当于一定数量的空格。"Hello\tWorld" 会在 "Hello" 和 "World" 之间插入一个制表符，通常是四个或八个空格。
- \n (换行符): 移动到下一行开始新的输出。"Hello\nWorld" 会把 "Hello" 和 "World" 分成两行显示。
- \f (换页符): 插入一个换页符，通常用来控制打印机换页，但在控制台输出中一般没有明显效果。
- \r (回车符): 回到当前行的开头。"Hello\rWorld" 会覆盖掉当前行的内容，显示 "World"。
- \" (双引号): 插入一个双引号。"He said, \"Hello, World!\"" 显示 He said, "Hello, World!"。
- \' (单引号): 插入一个单引号。通常用在字符字面量中，如 '\'\'' 表示一个单引号字符。
- \\ (反斜杠): 插入一个反斜杠。"This is a backslash: \\" 显示 This is a backslash: \。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Scala 转义字符` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
