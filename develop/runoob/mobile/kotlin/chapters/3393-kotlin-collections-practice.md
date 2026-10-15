# Kotlin：Kotlin 集合

- 来源：[Kotlin 集合](https://www.runoob.com/kotlin/kotlin-collections.html)
- 分类：移动开发
- 技术：Kotlin
- 笔记类型：练习笔记
- 章节序号：3393

## 本章内容

集合是日常开发中用得最多的数据结构，Kotlin 在 Java 集合框架之上重新设计了接口层次。

它把"只读"和"可变"拆成两套接口，让函数签名能明确表达"我不会修改这个集合"，同时保持了与 Java 集合的完全互操作。


## 集合层次结构

Kotlin 的集合接口都在 kotlin.collections 包中，该包默认导入，不需要写 import。

List 和 Set 属于同一个继承链，Map 则是完全独立的一支，不继承 Collection 也不继承 Iterable。

注意：Map 不是 Collection。它既不能直接用于 for 循环，也没有 size 之外的 Collection 方法，遍历时需要访问 keys、values 或 entries。


## 只读接口与可变接口

只读接口只提供读取方法，没有 add、remove、clear 这些修改操作。

把集合声明成 List 类型，调用方就无法往里添加元素，这个约束由编译器强制保证。


## 实例

运行结果：

```text
[Runoob, RUNOOB, Kotlin]
```

这说明只读接口约束的是"通过这个引用能做什么"，而不是"这个对象永远不能变"。


## 只读集合不是深不可变

只读集合有两条被忽略的边界，理解它们能避免线上事故。

第一，只读引用背后可能是可变集合，只要还持有另一个可变引用，内容就能被改动，上一节的例子已经演示过。

第二，只读约束只作用于集合本身，不会递归作用于元素，元素如果是可变对象，仍然可以被修改。


## 实例

运行结果：

```text
[[Runoob, RUNOOB]]
```

建议：如果确实需要不可变集合，可以使用 kotlinx.collections.immutable 库中的持久化集合，或者对外返回副本（如 list.toList()），不要依赖只读接口来保证线程安全。


## List：有序可重复

List 是最常用的集合，元素按插入顺序排列，允许重复，并支持按下标访问。

创建只读列表用 listOf，创建可变列表用 mutableListOf 或 arrayListOf。


## 实例

运行结果：

```text
[Runoob, RUNOOB, Kotlin]
[Runoob, RUNOOB, Kotlin]
[Runoob, RUNOOB, Kotlin]
Runoob
null
2
true
```

mutableListOf 和 arrayListOf 在 JVM 上都返回 ArrayList，功能等价。

区别在于 arrayListOf 的返回类型是具体的 ArrayList，需要显式使用这个类型时选它即可。


## Set：元素唯一

Set 保证元素不重复，重复添加不会报错，只是被忽略。

setOf 和 mutableSetOf 在 JVM 上基于 LinkedHashSet，会保持插入顺序；hashSetOf 基于 HashSet，不保证遍历顺序。


## 实例

运行结果：

```text
[Runoob, RUNOOB]
[Runoob, RUNOOB, Kotlin]
[Kotlin, RUNOOB, Runoob]
2
true
```

注意：依赖 Set 的遍历顺序是不安全的。需要稳定顺序时用 setOf、mutableSetOf 或 linkedSetOf，它们都保持插入顺序。


## Map：键值对集合

Map 存储键值对，键唯一，值可以重复。

取值时用方括号语法 map[key]，返回类型是 V?，键不存在时得到 null。


## 实例

运行结果：

```text
{Runoob=1, RUNOOB=2}
{Runoob=1, RUNOOB=2}
1
null
0
[Runoob, RUNOOB]
[1, 2]
```

需要遍历 Map 时，使用 for ((key, value) in map) 解构语法即可。


## 创建函数对比

创建函数名字相似，返回类型和底层实现却不同，选错会影响顺序和性能。

无参调用 listOf()、setOf()、mapOf() 会返回共享的空集合实例，因此创建空集合没有额外开销。


## 用 lambda 构造集合

List(n) { } 会创建一个长度为 n 的列表，lambda 的参数是下标。

需要按条件动态构建时，用 buildList、buildSet、buildMap，它们在 Kotlin 1.6 起稳定。


## 实例

运行结果：

```text
[0, 1, 4, 9, 16]
[0, 0, 0]
[Runoob, RUNOOB, Kotlin]
{Runoob=1, RUNOOB=2}
```


## 集合之间的转换

只读集合和可变集合之间、不同集合类型之间，都通过 toXxx 系列函数转换。

这些函数都会创建新的集合对象，原集合不受影响。


## 实例

运行结果：

```text
[3, 1, 2, 1]
[3, 1, 2]
[1, 1, 2, 3]
[3, 1, 2, 1, 99]
{Runoob=1, RUNOOB=2}
{Runoob=6, Kotlin=6}
```

常用的转换函数还有 toMutableSet、toMutableMap、toTypedArray，用法与上面一致。


## 常见问题

List 和 MutableList 是什么关系？

两者都是接口，MutableList 继承自 List。同一个对象可以同时被两种类型的引用指向，能做什么由引用的静态类型决定。

为什么 map[key] 返回可空类型？

因为键可能不存在。这是空安全设计的一部分，编译器强制你处理"取不到值"的情况，可以用 Elvis 提供默认值。

listOf 创建的列表真的不能改吗？

不能通过 List 接口改，但底层实现可能是 Arrays$ArrayList，如果把它强制转换成 MutableList，添加元素会在运行时抛出 UnsupportedOperationException。

什么时候用 Set 而不是 List？

需要去重或频繁判断元素是否存在时用 Set，因为 Set 的 contains 平均是常数时间；需要保持顺序和允许重复时用 List。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Kotlin 集合` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
