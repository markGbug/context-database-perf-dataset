# Kotlin：Kotlin 注解

- 来源：[Kotlin 注解](https://www.runoob.com/kotlin/kotlin-annotation.html)
- 分类：移动开发
- 技术：Kotlin
- 笔记类型：学习笔记
- 章节序号：3397

## 本章内容

注解（Annotation）是一种给代码附加元数据的机制，它本身不影响程序逻辑，但能被编译器、框架和注解处理器读取。

Kotlin 的注解既能作用于 Kotlin 自身的声明，也能精确指定落到 JVM 的哪个位置，比如字段、getter 或 setter。

本章节讲注解的定义与元注解、参数类型、使用处目标，以及日常开发最常用的内置注解。


## 注解的定义与使用

用 annotation class 定义一个注解，它也可以有构造参数。

使用注解时把 @注解名 放在目标声明之前，带参数的注解用括号传入实参。


## 实例

```text
类注解：author=RUNOOB, version=2.2, tags=[collection, annotation]
方法注解：author=RUNOOB, version=1.0
```

提示：方法注解只写了 author，version 就取默认值 "1.0"。如果 @Retention 不是 RUNTIME，反射就读取不到这个注解。


## 元注解

元注解是「用来修饰注解的注解」，它们决定一个注解能用在哪里、保留到什么时候。

三种保留级别对应不同的可见范围，选错级别会导致框架读不到注解。

注意：Kotlin 中不写 @Retention 时默认是 BINARY，而 Java 的默认是 CLASS，两者行为一致。想让反射读到，必须显式写成 RUNTIME。


## 注解参数

注解参数不是任意值都能写，它们必须是编译期就能确定的常量。

允许的类型包括基本类型、String、KClass、枚举、其他注解，以及这些类型的数组。


## 实例

```text
count=2, label=runoob, type=HIGH
target=String, owner=RUNOOB
aliases=[www.runoob.com, RUNOOB]
```

限制：注解参数不能是可空类型，也不能是任意对象；传入的值必须是字面量或 const val 常量，不能在运行时计算。


## 使用处目标

一个 Kotlin 属性在 JVM 上会同时产生字段、getter 和 setter，注解到底标在哪一个上，需要用使用处目标来指定。

不写使用处目标时，Kotlin 按 param、property、field 的优先级自动选择。


## 实例

```text
runoob / 12 / www.runoob.com
getter 上的注解：作用于 getter
```

文件级注解必须放在文件最顶部，包声明之前，下面是它的真实写法。


## 实例

注意：@property: 标注的注解在 Java 侧完全不可见，因为 JVM 上根本没有「属性」这个概念；如果 Java 框架需要读取，请改用 @field: 或 @get:。


## 常用内置注解

Kotlin 标准库和 JVM 扩展提供了大量开箱即用的注解，下面按用途分类介绍。


## 实例

```text
Hello runoob!
Hello runoob! Hello runoob!
Hello RUNOOB
www.runoob.com
RUNOOB
RUNOOB
```

@Synchronized 和 @Volatile 用于并发场景，它们只在 JVM 平台有效。


## 实例

```text
1
2
stopped=true
```

@Repeatable 让同一个注解可以重复标注，Kotlin 1.6 起会自动生成容器注解。


## 实例

```text
[collection, annotation]
```

使用实验性 API 时，需要先用 @RequiresOptIn 标记它，调用方再用 @OptIn 表态。


## 实例

```text
www.runoob.com
```

提示：不想在每个调用处都写 @OptIn，可以在编译参数里加上 -opt-in=ExperimentalSiteApi，让整个模块默认选择使用该 API。


## 注解处理：KSP 与 kapt

注解本身只是元数据，真正干活的是注解处理器，它在编译期扫描注解并生成代码。

Kotlin 生态里有两套方案，KSP 是官方主推的新方案，kapt 则用于兼容已有的 Java 注解处理器。

在 Gradle 中启用 KSP 只需要加一个插件，然后把注解处理器的依赖从 kapt 换成 ksp。


## 实例

注意：KSP 与 kapt 不能对同一个注解处理器同时启用，迁移时要把 kapt(...) 整行替换为 ksp(...)，并删除 kapt 插件。


## 常见问题

下面汇总注解使用中最容易遇到的几个问题。


## 复习重点

- 能说明 `Kotlin 注解` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
