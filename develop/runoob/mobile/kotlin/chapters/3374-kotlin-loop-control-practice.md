# Kotlin：Kotlin 循环控制

- 来源：[Kotlin 循环控制](https://www.runoob.com/kotlin/kotlin-loop-control.html)
- 分类：移动开发
- 技术：Kotlin
- 笔记类型：练习笔记
- 章节序号：3374

## 本章内容

循环让同一段代码重复执行，是控制程序流程最基本的工具之一。

Kotlin 的循环语法和 Java 很像，但没有传统的三段式 for (int i = 0; i < n; i++)，取而代之的是直接遍历集合与区间。

本页介绍 for、while、do...while 三种循环，以及 break、continue 的标签跳转，最后是 Kotlin 2.2 起稳定的非局部 break 与 continue。


## for 循环

for 循环用于遍历任何提供了迭代器（iterator）的对象，集合、数组、区间都可以。

语法是 for (元素 in 可迭代对象) { ... }，元素不需要声明类型，编译器会自动推断。


## 实例

运行结果如下。

```text
Runoob
www.runoob.com
RUNOOB
```

遍历数组的方式完全一样，因为数组同样提供了迭代器。


## 实例

```text
当前元素：10
当前元素：20
当前元素：30
```

Kotlin 的 for 只负责"取出元素"，不负责维护计数器，因此不会有忘记写 i++ 导致死循环的问题。


## 区间与步长

区间（range）本身就是一个可遍历对象，用 ..、until、downTo、step 构造。

它们的边界规则各不相同，混用是初学者最容易出错的地方。

下面的例子把这几种写法放在一起对比。


## 实例

```text
123  => 1..3
12  => 1 until 3
321  => 3 downTo 1
135  => 1..6 step 2
12  => 半开区间
```

区间不只用于循环，也可以用 in 判断某个值是否落在区间内，例如 if (age in 18..60)。

提示：直接遍历区间会被编译器优化成普通计数循环，不会为每个元素创建对象。但如果先写 (1..1000).toList() 再遍历，就会真的创建一个包含 1000 个元素的列表。


## 用下标遍历：indices 与 withIndex

需要同时拿到下标和元素值时，可以用 indices 或库函数 withIndex()。

indices 是下标区间，withIndex() 返回一组带下标的元素，可以配合解构声明使用。


## 实例

```text
下标 0 -> Runoob
下标 1 -> www.runoob.com
下标 2 -> RUNOOB
---
0: Runoob
1: www.runoob.com
2: RUNOOB
```

Map 也是可迭代对象，遍历时可以直接解构出键和值。


## 实例

```text
name = Runoob
site = www.runoob.com
```


## while 循环

while 先判断条件，条件为真才执行循环体，可能一次都不执行。

循环次数不确定、依赖运行时状态时，while 比 for 更合适。


## 实例

```text
倒计时 3
倒计时 2
倒计时 1
循环结束
```

如果条件一开始就是 false，循环体一次也不会执行。


## 实例

```text
循环结束，count = 0
```


## do...while 循环

do...while 先执行一次循环体，再判断条件，因此循环体至少执行一次。

适合"先做一次、再决定要不要继续"的场景，比如读取输入、重试操作。


## 实例

```text
循环体执行：count = 0
循环结束
```

注意：do...while 的 while 后面要写分号，而普通 while 和 for 不需要。这是 Kotlin 中少数必须写分号的位置之一。


## break 与 continue

break 立即结束最内层的循环，continue 跳过本次迭代、直接进入下一次。

两者都只作用于"最直接包围它们的循环"，除非配合标签使用。


## 实例

```text
1
2
4
5
```


## 标签与标签跳转

标签是标识符后面加 @，写在循环或 lambda 前面，用来给 break、continue、return 指定目标。

没有标签时，break 只能结束最内层循环；有了标签才能一次跳出多层嵌套。


## 实例

```text
i = 1, j = 1
i = 2, j = 1
循环结束
```

标签也可以标在 lambda 上，此时 return@标签 表示从这个 lambda 返回，而不是从外层函数返回。


## 实例

```text
非负数
负数
```

提示：标签名和变量名可以重名，但为了可读性，建议给循环和 lambda 起有含义的标签名，例如 outer@、rows@。


## 非局部 break 与 continue（2.2 起稳定）

Kotlin 2.2 起，内联 lambda 中的 break 和 continue 可以直接作用到外层的循环，这种写法叫非局部跳转。

它解决的是"在 lambda 内部想跳过或结束外层循环"的问题，此前只能用 return@标签 或者额外的标志变量绕开。

这个特性在 Kotlin 2.1 中作为预览提供，需要编译器选项 -Xnon-local-break-continue 才能使用；从 2.2 起默认可用（KT-1436）。


## 实例

```text
处理数字：1
遇到 null，跳过本次循环
处理数字：3
遇到 null，跳过本次循环
处理数字：5
循环结束
```

break 同样可以这样用，效果是直接结束外层的整个循环。


## 实例

```text
当前数字：1
当前数字：2
当前数字：3
循环结束
```

注意：非局部 break/continue 只对传给内联函数（inline function）的 lambda 有效，例如 run、let、forEach 的 lambda。如果 lambda 被保存成变量再传给普通函数，仍然不允许这样跳转，因为编译器无法保证它一定在原地执行。


## return 与标签返回

return 默认从最近的函数返回，但在 lambda 中要区分两种情况：返回外层函数，还是只结束这个 lambda。

return@标签 只从标签对应的 lambda 返回，效果相当于 lambda 里的 continue。


## 实例

```text
forEach：1
forEach：2
forEach：4
---
for：1
for：2
for：4
```

标签名可以省略，此时编译器用接收 lambda 的函数名作为隐式标签，所以 return@forEach 里的 forEach 就是隐式标签。

注意：forEach 是内联函数，所以在它的 lambda 里直接写 return 会从外层函数返回，而不是只结束这一次遍历。这种非局部返回的规则会在《Kotlin 内联函数与 reified》一篇详细展开；日常写法中，只跳过当前元素请用 return@forEach。


## 常见问题

下面整理几个初学者经常遇到的疑问。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Kotlin 循环控制` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
