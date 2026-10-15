# Kotlin：Kotlin Lambda 高阶函数

- 来源：[Kotlin Lambda 高阶函数](https://www.runoob.com/kotlin/kotlin-lambda.html)
- 分类：移动开发
- 技术：Kotlin
- 笔记类型：练习笔记
- 章节序号：3376

## 本章内容

在 Kotlin 里，函数是一等公民（first‑class citizen）：可以赋值给变量、作为参数传递、作为返回值返回。

把函数当作数据来用，就引出了函数类型、Lambda 表达式和高阶函数这几个概念，它们也是 Kotlin 集合操作写法简洁的根本原因。

本章节从函数类型讲起，逐步过渡到 Lambda、闭包、函数引用与 SAM 转换。


## 函数类型

函数类型描述"接收什么参数、返回什么值"，写法是 (参数类型) -> 返回类型。

函数类型本身也是一种类型，所以可以声明变量、作为参数、作为返回值。


## 实例

```text
3
你好，Runoob
RUNOOB
42
```

函数类型里也可以给参数起名字，例如 (x: Int, y: Int) -> Int，这些名字只用于提示，不影响类型是否匹配。

还有一种带接收者的函数类型，写法是 String.(Int) -> String，表示这个函数要在 String 上调用，这正是扩展函数的函数类型形式。


## 实例

```text
RunRun
RUNOOBRUNOOB
```


## Lambda 表达式语法

Lambda 是一段可以传递的代码块，用花括号包围，参数在 -> 左边，函数体在右边。

函数体最后一个表达式的值，就是 Lambda 的返回值。


## 实例

```text
7
10
Hello, Runoob
结果是 正数
2
```

注意：Lambda 的类型推断依赖上下文。像 val f = { x -> x + 1 } 这样既不写参数类型、上下文又没有明确目标类型时，编译器会报"无法推断参数类型"。解决办法是补上类型标注，或者把 Lambda 直接传给一个签名明确的函数。


## 高阶函数

接收函数作为参数，或者返回一个函数的函数，叫做高阶函数（higher-order function）。

它把"做什么"从"怎么做"里抽出来，让调用方决定具体行为。


## 实例

```text
9
18
15
40
```

当函数的最后一个参数是函数类型时，可以把 Lambda 写在括号外面，这就是尾随 Lambda（trailing lambda）语法。

如果只有这一个参数，括号本身也可以省略，于是就有了 list.forEach { ... } 这种写法。


## 与集合结合：forEach、filter、map

集合库把高阶函数用到了极致，最常用的三个是 forEach、filter 和 map。

它们接收的 Lambda 决定了每个元素要做什么，返回的是新集合而不是修改原集合。


## 实例

```text
runoob
RUNOOB
java
kotlin
---
[RUNOOB]
[6, 6, 4, 6]
[RUNOOB, RUNOOB]
```

forEach 是内联函数，filter 和 map 同样接收内联的 Lambda，所以这些操作不会为 Lambda 额外创建对象。

需要下标时用 forEachIndexed，需要同时拿到键和值时可以对 Map 使用解构。


## 实例

```text
0 -> Runoob
1 -> www.runoob.com
name = Runoob
site = www.runoob.com
```


## 闭包与变量捕获

Lambda 可以访问定义它时所在作用域的变量，这种结构叫闭包（closure）。

Kotlin 允许捕获的变量是 var，也允许在 Lambda 内部修改它。


## 实例

```text
counter = 2
c1 = 3, c2 = 2
```

两个闭包各自持有一份 count，互不影响，这是闭包最典型的用途：把状态封装在函数内部。


## 匿名函数

Lambda 不是唯一的函数字面量，还可以用 fun 关键字定义没有名字的匿名函数。

匿名函数里的 return 只从匿名函数自身返回，不会影响外层函数，这一点和 Lambda 不同。


## 实例

```text
5
36
1
2
4
结束
```

匿名函数的另一个特点是返回类型可以显式写出，需要明确控制返回值类型时比 Lambda 更直观。


## 函数引用 ::

如果函数已经有名字，可以用 :: 把它变成函数类型的值，不必再包一层 Lambda。

函数引用分为顶层函数引用、绑定引用（已经绑定到实例）和未绑定引用（需要传入接收者）三种。


## 实例

```text
[2, 4]
你好，Runoob
你好，Runoob
```

当存在多个同名重载函数时，编译器会根据函数类型的目标类型来选择匹配的那个引用。


## 构造器引用与绑定引用

构造函数也可以被引用，写法是 ::类名，它产生一个返回该类实例的函数。

重载的构造函数同样由目标类型决定选哪一个。


## 实例

```text
Runoob - www.runoob.com
[Runoob, RUNOOB]
```

上面的 create 已经是一个函数类型的值，可以像普通函数一样在 map 里调用。

绑定引用除了成员函数，也可以引用属性，例如 site::name 会得到一个取值函数。


## SAM 转换

SAM 是 Single Abstract Method 的缩写，指只有一个抽象方法的接口。

Kotlin 允许把 Lambda 直接转换成这类接口的实例，这就是 SAM 转换。


## 实例

```text
true
false
在 Java 线程接口里运行 RUNOOB
```

Kotlin 1.4 起，用 fun interface 声明的 Kotlin 接口也支持 SAM 转换；在此之前，SAM 转换只对 Java 接口有效。

普通（非函数式）接口即使只有一个方法，也不能用 Lambda 转换，必须写对象表达式。


## 常见问题

下面整理几个关于 Lambda 的常见疑问。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Kotlin Lambda 高阶函数` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
