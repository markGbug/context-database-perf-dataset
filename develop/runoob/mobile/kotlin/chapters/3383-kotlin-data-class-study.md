# Kotlin：Kotlin 数据类与解构

- 来源：[Kotlin 数据类与解构](https://www.runoob.com/kotlin/kotlin-data-class.html)
- 分类：移动开发
- 技术：Kotlin
- 笔记类型：学习笔记
- 章节序号：3383

## 本章内容

数据类专门用来保存数据，只要在 class 前面加上 data，编译器就会自动生成一组常用方法。

这些方法包括 equals、hashCode、toString、componentN 和 copy，省去大量重复代码。

配合解构声明，还能把对象里的属性一次性拆到多个变量中。


## 定义一个数据类

数据类的写法很简单，主构造器里至少要有一个参数，并且参数都要标上 val 或 var。


## 实例

```text
RunoobSite(name=菜鸟教程, url=www.runoob.com, age=12)
菜鸟教程
true
true
```

如果用普通 class 写同样的内容，这些方法都得自己实现，非常啰嗦。


## 自动生成的成员

data class 生成的方法都有固定的语义，下面这张表可以当作速查。

只有主构造器里的属性会参与 equals、hashCode、toString 和 componentN。

写在类体里的属性不参与这些方法的生成。


## 生成条件

并不是随便加个 data 就能变成数据类，下面几条必须同时满足。


## 实例

```text
RunoobA(id=1)
```

数据类可以实现接口，但本身是 final 的，不能再被继承。

它也可以带类体，在类体里定义额外的函数和属性。


## copy() 与部分修改

数据类适合存放不可变数据，修改某个字段时通常用 copy 生成一个新对象，而不是改原对象。

copy 的每个参数都有默认值，默认取原对象对应的属性，因此可以只写要改的那几个。


## 实例

```text
RunoobSite(name=菜鸟教程, url=m.runoob.com, age=12)
RunoobSite(name=RUNOOB 教程, url=www.runoob.com, age=13)
true
false
```

copy 是浅拷贝，对象里的引用类型字段仍然指向同一个实例。


## 解构声明

数据类会自动生成 component1、component2 等函数，因此可以把对象拆成多个变量。

变量的顺序对应主构造器参数的顺序，不是属性在类体里的书写顺序。


## 实例

```text
名称：菜鸟教程，网址：www.runoob.com，年龄：12
只要网址：www.runoob.com
runoob -> 95
RUNOOB -> 88
```

普通类只要自己声明 componentN 运算符函数，也能支持解构。


## 实例

```text
x=3, y=4
```

注意：解构中的下划线占位符从 Kotlin 1.1 开始支持。老版本里如果想跳过某个位置，只能给它取个用不到的名字。


## 数据类的相等性

数据类的 equals 只比较主构造器属性，类体里的属性不参与。

这意味着两个对象可能相等，但它们的类体属性并不相同。


## 实例

```text
true
false
```

这也提醒我们：需要参与相等性判断的字段，都应该放进主构造器。


## Pair 与 Triple

标准库提供了两个现成的数据类，用来临时组合两到三个值。

Pair 表示两个值，Triple 表示三个值，它们都支持解构和 copy。


## 实例

```text
runoob
95
runoob 的分数是 95
RUNOOB - www.runoob.com - 2026
(runoob, 100)
```

Pair 和 Triple 适合函数临时返回多个值，字段含义不明确时建议改用自定义数据类。


## data object（Kotlin 1.9 起）

普通 object 打印出来是一串对象地址，data object 会自动生成有意义的 toString。

Kotlin 1.9 起可以用 data object 声明单例，它还会生成 equals 和 hashCode。


## 实例

```text
RunoobConfig
true
RUNOOB
```

data object 最常见的用途是放在密封类层次里表示没有数据的分支。


## 实例

```text
加载中
暂无数据
成功：www.runoob.com
```


## 常见问题

下面整理几个使用数据类时容易遇到的问题。


### 为什么改完属性没有生效

数据类的属性通常声明为 val，本身不可修改，正确做法是用 copy 生成新对象。

如果确实需要可变属性，把它写成 var，但要留意它仍然会参与 equals 和 hashCode。


### 类体里的属性为什么不参与比较

这是编译器的约定：只有主构造器参数才会生成到 equals、hashCode 和 toString 中。

需要比较的字段就放进主构造器，不要放在类体里。


### copy 之后两个对象共享内部对象怎么办

copy 只复制引用，不复制引用指向的对象，所以是浅拷贝。

如果内部有可变集合，需要自己手动深拷贝一份。


### Pair 和自定义数据类怎么选

只在函数内部临时返回两三个值，用 Pair 或 Triple 更省事。

一旦这些值会跨越模块传递，或者需要明确的字段名，就换成自定义数据类。


## 复习重点

- 能说明 `Kotlin 数据类与解构` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
