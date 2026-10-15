# Kotlin：Kotlin 异常处理

- 来源：[Kotlin 异常处理](https://www.runoob.com/kotlin/kotlin-exception.html)
- 分类：移动开发
- 技术：Kotlin
- 笔记类型：练习笔记
- 章节序号：3396

## 本章内容

异常是程序运行过程中出现的意外情况，Kotlin 用 try-catch 捕获它们，让程序在出错后仍能继续执行。

与 Java 相比，Kotlin 最大的不同是没有受检异常，编译器不再强迫你为每个方法声明它可能抛出的异常。

本章节从异常层次讲到资源自动关闭，覆盖日常开发中会用到的全部异常处理手段。


## 异常层次

Kotlin 的异常体系与 JVM 一致，根类型是 Throwable，下面分成 Error 和 Exception 两支。

提示：不要把 Error 也一并捕获。像内存耗尽、栈溢出这类问题，即使捕获了也无从恢复，反而会掩盖真正的故障。


## try-catch-finally

try 块放可能出错的代码，catch 块按异常类型依次匹配，finally 块无论是否发生异常都会执行。

catch 的匹配是从上到下的，因此子类型要写在父类型前面。


## 实例

```text
42 转换成功：42
--- 处理完一轮 ---
数字格式错误：For input string: "runoob"
--- 处理完一轮 ---
遇到 null 值
--- 处理完一轮 ---
循环结束，程序继续运行
```

如果某个异常没有被任何 catch 分支匹配，它会继续向上传播给调用者，最终导致程序终止并打印堆栈。


## try 作为表达式

在 Kotlin 中 try 是表达式而不是语句，它可以有返回值，返回值是 try 或 catch 块中最后一个表达式的结果。

这一点让「尝试转换，失败时给默认值」这类逻辑可以写得很紧凑。


## 实例

```text
18
-1
finally 块执行了，但不影响 try 的值
20
```

注意：不要在 finally 块里写 return。这会让 try 和 catch 中的返回值被丢弃，也会吞掉正在传播的异常，是很容易出错的写法。


## throw 与 Nothing

用 throw 主动抛出异常，表达式本身永远不会有返回值，因此它的类型是 Nothing。

Nothing 是 Kotlin 所有类型的子类型，表示「此处不会正常返回」，编译器会据此做控制流分析。


## 实例

```text
年龄合法：18
捕获到异常：年龄不能为负数：-1
```

标准库里的 error()、TODO() 以及 throw 表达式，返回类型都是 Nothing，它们的作用就是把「不可能继续」这件事告诉编译器。


## 自定义异常

当内置异常无法表达业务语义时，可以继承 Exception 定义自己的异常类型。

把出错的上下文作为属性保存下来，捕获时就能拿到更多信息。


## 实例

```text
注册成功：runoob
注册失败：非法的站点名称：example，问题字段：example
```

命名上建议以 Exception 结尾，并保留一个接收 message 和 cause 的构造器，方便异常链向上传递。


## Kotlin 没有受检异常

Java 把异常分为受检异常和非受检异常，受检异常必须显式 try-catch 或在方法签名上声明 throws。

Kotlin 取消了这个区分，所有异常都是非受检的，编译器不会强制你处理它们。


## 实例

```text
配置来自 runoob.conf
读取失败：配置路径为空
```

注意：取消受检异常不等于不用处理异常。Kotlin 把「是否处理」的决定权交回给开发者，代价是漏掉 catch 时只能在运行时才发现问题。


## use 与资源自动关闭

文件、流、数据库连接这类资源使用完必须关闭，否则会泄漏句柄。

Kotlin 用扩展函数 use 替代 Java 的 try-with-resources，无论块内是否抛出异常，它都会调用 close()。


## 实例

```text
Hello RUNOOB
Hello Kotlin
总行数：2
```

use 适用于所有实现了 Closeable 或 AutoCloseable 的对象，返回值为代码块最后一行表达式的结果，因此也可以这样写：

下面的例子沿用上一段示例生成的 runoob.txt，请先运行上一段代码，或者确保当前目录下已存在这个文件。


## 实例

```text
文件共有 2 行
```


## runCatching

runCatching 把「执行 + 捕获」合并成一个表达式，成功和失败都包装进 Result 对象。

适合那些「失败是正常分支」的场景，比如解析用户输入、读取可能不存在的配置。


## 实例

```text
成功：isSuccess=true，值=42
失败：isFailure=true，值=null
失败时给默认值：-1
兜底结果：兜底(For input string: "runoob")
onFailure：NumberFormatException
```

runCatching 从 Kotlin 1.3 起提供，它返回的 Result 类型在 1.5 起稳定。

注意：runCatching 捕获的是 Throwable，会把协程的 CancellationException 也一并吞掉，导致协程无法正常取消。在协程里使用时，要么改用 try-catch 只捕获具体异常，要么在失败分支里把 CancellationException 重新抛出。


## 常见问题

下面汇总异常处理中最常见的几个疑问。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Kotlin 异常处理` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
