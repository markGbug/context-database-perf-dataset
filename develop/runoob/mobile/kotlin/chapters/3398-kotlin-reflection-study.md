# Kotlin：Kotlin 反射

- 来源：[Kotlin 反射](https://www.runoob.com/kotlin/kotlin-reflection.html)
- 分类：移动开发
- 技术：Kotlin
- 笔记类型：学习笔记
- 章节序号：3398

## 本章内容

反射是指在运行时检查类、函数、属性等程序结构，并且可以动态调用它们的能力。

Kotlin 提供了一套自己的反射 API，通过 kotlin-reflect 库使用，比 Java 反射更简洁，还能保留可空性、属性等 Kotlin 特有的信息。


## 什么是反射

正常情况下，我们写的代码在编译期就确定了要调用哪个函数、访问哪个属性。

反射打破了这一点：程序在运行时才知道自己要操作的对象是谁。

举例来说，配置文件里写了一个方法名 save，程序读进来之后通过反射找到并调用它，代码里不需要写死 obj.save()。

常见的使用场景有依赖注入框架、序列化库、测试工具、脚本引擎等。

业务代码里很少需要直接写反射，但理解它能帮你读懂这些框架的内部行为。


### 使用代价

反射很强大，代价也不小，不要为了「看起来灵活」而滥用。

提示：能用普通代码表达的逻辑就不要用反射。只有当「调用方在编译期确实不知道要操作谁」时，反射才是合理选择。


## KClass 与 ::class

Kotlin 用 KClass 表示一个类的运行时信息，通过 ::class 获取。

KClass 是 Kotlin 自己的类型，它能告诉你类的简单名、限定名，也能知道属性是否可空。


## 实例

实例执行输出结果为：

```text
简单名: Runoob
限定名: com.runoob.Runoob
实例的类: Runoob
是同一个对象: true
```

注意 KClass 是泛型类型，KClass<Runoob> 表示它描述的是 Runoob 这个类。

泛型参数写在尖括号里，KClass 本身也带类型参数，这样调用方就能拿到具体类型。


### ::class.java 与 Class.kotlin

JVM 平台上，Kotlin 的 KClass 和 Java 的 Class 可以互相转换。

调用 ::class.java 拿到 Java 的 Class 对象，再用 Class.kotlin 转回来。


## 实例

实例执行输出结果为：

```text
Java 类名: com.runoob.Runoob
转回 KClass: Runoob
```

KClass 的 simpleName、qualifiedName、java 由标准库直接支持，不需要额外依赖。

枚举成员、调用函数、创建实例等更强的功能，则需要引入 kotlin-reflect。


## KFunction 与函数引用

把函数当作值来传递时，得到的是函数引用，它的类型是 KFunction 的子类型。

例如两个参数的函数，引用类型是 KFunction2<P1, P2, R>，泛型参数依次是参数类型和返回类型。


## 实例

实例执行输出结果为：

```text
函数名: add
参数个数: 2
直接调用: 7
call 调用: 7
成员函数名: multiply
call 调用: 30
```

提示：函数引用 ::add 本身不是「重反射」。f(3, 4) 会被编译器优化成直接调用；只有 f.call(3, 4) 才走反射路径。所以能用 invoke 就不要用 call。

如果不想记参数顺序，可以用 callBy 按参数名传值，参数对象从 parameters 里取。


## 实例

实例执行输出结果为：

```text
callBy: 7
```

函数引用的类型是 KFunction，而普通 lambda 是 FunctionN 类型，两者不能直接互相赋值。


## KProperty 与属性引用

用 类名::属性名 可以得到属性引用，类型是 KProperty1<T, R>。

其中 T 是接收者类型，R 是属性类型；如果属性是 var，类型会变成 KMutableProperty1，可以写值。


## 实例

实例执行输出结果为：

```text
属性名: name
读取 name: RUNOOB
读取 age: 10
写入后 age: 20
```

顶层属性或对象属性的接收者不是某个实例，得到的是 KProperty0<R>，调用 get() 时不需要传接收者。


## 实例

实例执行输出结果为：

```text
siteName = www.runoob.com
version = Kotlin 2.2
```


## 通过反射调用函数与读写属性

实际使用反射时，我们通常先遍历出所有成员，再按名字查找目标。

下面这个例子把对象的属性和函数都列了出来，并按名字找到 greet 调用。


## 实例

实例执行输出结果为：

```text
成员属性：
  age = 10
  name = RUNOOB
本类声明的函数：
  greet
调用 greet(): 欢迎来到 RUNOOB
```

memberProperties 返回集合的顺序不保证稳定，所以例子里加了 sortedBy。

如果只想看类自己声明的成员，用 declaredMemberProperties 和 declaredMemberFunctions，它们不会带上父类的成员。

注意：memberProperties、memberFunctions、call 这些 API 都在 kotlin-reflect 里，没有引入依赖会抛出 KotlinReflectionNotSupportedError。


## createInstance 创建实例

KClass.createInstance() 可以调用无参构造器创建一个实例，Kotlin 1.1 起提供。

它要求类必须有一个无参构造器，或者所有参数都有默认值，否则会抛异常。


## 实例

实例执行输出结果为：

```text
Runoob 实例
RUNOOB
```

如果类需要参数，就用 primaryConstructor 拿到构造器，再调用 call。


## 实例

实例执行输出结果为：

```text
RUNOOB -> www.runoob.com
```


## kotlin-reflect 依赖

完整反射功能需要单独引入 kotlin-reflect，它不在标准库中。

用 Gradle 的 Kotlin DSL 时，可以用 kotlin("reflect") 让插件自动匹配版本。


## 实例

用 Maven 时，坐标是 org.jetbrains.kotlin:kotlin-reflect。


## 实例

提示：kotlin-reflect 的版本必须和编译时使用的 Kotlin 版本一致，否则可能在运行时抛出版本不匹配的异常。在线工具 play.kotlinlang.org 已经内置了这个库，可以直接运行上面的例子。


## 反射 vs Java 反射

Kotlin 反射建立在 Java 反射之上，但对外暴露的 API 更贴合 Kotlin 的语义。

Java 反射要靠字符串加载类，例如 Class.forName("com.runoob.Runoob")，编译期完全无法检查。

Kotlin 也保留了这条路，但推荐优先用 ::class，这样至少类名是编译期检查过的。


## 实例

实例执行输出结果为：

```text
欢迎来到 RUNOOB
```

Kotlin 反射还有一个 Java 反射做不到的能力：判断一个类型是不是可空。


## 实例

实例执行输出结果为：

```text
name: kotlin.String，可空 = false
nickname: kotlin.String?，可空 = true
```


## 常见问题

下面几个问题在初学反射时出现频率最高。


## 后续章节

- KotlinReflectionNotSupportedError
- ::class 和 ::class.java 有什么区别
- 函数引用和反射调用哪个快
- createInstance 报 no argument constructor 错误
- 反射修改了 private 属性会怎样

## 复习重点

- 能说明 `Kotlin 反射` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
