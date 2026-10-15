# Kotlin：Kotlin Java 互操作

- 来源：[Kotlin Java 互操作](https://www.runoob.com/kotlin/kotlin-java-interop.html)
- 分类：移动开发
- 技术：Kotlin
- 笔记类型：学习笔记
- 章节序号：3400

## 本章内容

Kotlin 从设计之初就把「和 Java 无缝互操作」当作核心目标，两者编译后都运行在 JVM 上，可以直接互相调用。

本章节介绍两个方向调用时的规则、平台类型带来的空安全风险，以及让 Java 调用更友好的几个注解。


## Kotlin 调用 Java

Kotlin 可以直接使用任何 Java 类，不需要额外的包装。

Kotlin 还对 Java 的 getter 和 setter 做了语法糖：person.getName() 可以直接写成 person.name。

先看一个普通的 Java 类。


## 实例

在 Kotlin 中调用这个类时，getter 和 setter 可以省略写法。


## 实例

实例执行输出结果为：

```text
RUNOOB
10
修改后：20
欢迎来到 www.runoob.com
```

Java 的静态成员在 Kotlin 里也是静态调用，写法完全一致。

Java 的受检异常 Kotlin 不强制捕获，Kotlin 把异常都当作非受检异常处理。


## Java 调用 Kotlin

反过来，Java 调用 Kotlin 时需要注意 Kotlin 特有结构在 JVM 上的呈现方式。

顶层函数会放进一个名为「文件名 + Kt」的类，伴生对象成员要通过 Companion 访问。


## 实例

对应的 Java 调用代码如下。


## 实例

运行输出结果为：

```text
Kotlin 2.2
Kotlin 2.2
www.runoob.com
来自顶层函数的问候
```

Kotlin 的 object 单例在 JVM 上有一个静态字段 INSTANCE，Java 要写成 Runoob.INSTANCE.foo()。

如果想改掉「文件名 + Kt」这个类名，可以用文件级注解 @file:JvmName。


## 实例

这样 Java 里就可以写 RunoobUtils.version()，而不是 UtilsKt.version()。


## 平台类型与空安全风险

Java 的类型系统没有可空性信息，Kotlin 把这种「可能是空也可能不是空」的类型叫做平台类型，写作 String!。

平台类型可以被赋给非空类型，也可以被赋给可空类型，编译器不做检查，风险就藏在这里。


## 实例

如果 Kotlin 直接把它当作非空类型使用，编译能通过，运行时会抛空指针。


## 实例

实例执行输出结果为：

```text
内容：null
长度：0
```

注意：如果把上面写成 val message: String = service.message，编译器不会报错，但运行到 message.length 时会抛 NullPointerException。所以调用没有空标注的 Java 代码时，主动把返回值声明成可空类型更安全。

如果 Java 侧使用了 JSR-305 的 @Nullable 或 @NotNull，或者 Android 的 androidx.annotation 系列注解，Kotlin 会识别它们并生成真正的可空类型。


## 常用互操作注解

Kotlin 提供了一组 @Jvm 开头的注解，用来控制生成的 JVM 字节码，让 Java 调用更自然。

下面这个例子把几个常用注解放在一起演示。


## 实例

Java 侧的调用效果如下。


## 实例

运行输出结果为：

```text
3000
8080
[RUNOOB] hello
kotlin hello
KOTLIN HELLO
读取成功：runoob.conf
你好，RUNOOB
```

提示：@JvmField 的使用有条件：属性必须有 backing field，不能是 private，也不能是 open、override 或 const。


## 属性与 getter/setter 的映射规则

Kotlin 的属性在 JVM 上并不直接存在，编译器会为它生成私有字段和访问器。

记住这张映射表，就能推断出 Java 侧该用什么写法。

布尔属性以 is 开头时，getter 不会再加 get 前缀，直接就是属性名本身。

如果只是想改访问器的名字，而不是把整个属性变成字段，可以用 @get:JvmName 和 @set:JvmName。


## 实例


## 默认参数与 Java 重载

Java 没有默认参数的概念，Kotlin 函数带默认值时，Java 必须把参数全部传齐。

编译器会为默认参数生成一个带 $default 后缀的合成方法，但 Java 直接调用它很别扭。


## 实例

加注解后，Java 侧可以按不同参数个数调用，就像普通的重载方法一样。


## 实例

运行输出结果为：

```text
你好，RUNOOB
你好，RUNOOB
欢迎，RUNOOB
```

注意：@JvmOverloads 会为每一个默认参数生成一个重载，参数很多时会显著增加方法数量。参数超过三四个时，考虑改成 Builder 模式或配置对象。


## SAM 转换

SAM 转换是指把 lambda 直接当作只有一个抽象方法的接口实现。

Java 的函数式接口在 Kotlin 里天然支持这种写法，例如 Runnable、Comparator、Callable。


## 实例

Kotlin 侧可以直接用 lambda 实现这个接口。


## 实例

实例执行输出结果为：

```text
执行任务：RUNOOB
www.runoob.com
```

Kotlin 1.4 之前，只有 Java 接口支持 SAM 转换，Kotlin 接口必须写成对象表达式。

反方向的场景要注意：Java 调用 Kotlin 的 () -> Unit 参数时，看到的是 Function0<Unit>，需要显式实现。


## 实例


## 实例

运行输出结果为：

```text
来自 Java 的调用
```

提示：如果某个 API 主要给 Java 调用，把参数类型声明成 Java 的函数式接口（例如 Runnable）或 Kotlin 的 fun interface，Java 侧就能直接写 lambda，体验好很多。


## 版本说明

互操作相关的注解大多从 Kotlin 1.0 就已经存在，少数特性是后来补充的。


## 后续章节

- 常见问题
- Java 侧找不到 Kotlin 的函数
- 为什么 Java 访问 Kotlin 属性要加 get
- 伴生对象成员为什么不能直接调用
- Kotlin 调用 Java 时受检异常去哪了
- 平台类型能不能完全避免

## 复习重点

- 能说明 `Kotlin Java 互操作` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
