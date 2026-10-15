# Kotlin：Kotlin 作用域函数

- 来源：[Kotlin 作用域函数](https://www.runoob.com/kotlin/kotlin-scope-functions.html)
- 分类：移动开发
- 技术：Kotlin
- 笔记类型：学习笔记
- 章节序号：3378

## 本章内容

作用域函数是 Kotlin 标准库提供的一组小工具，它们让对象在一个临时的作用域里被操作，并决定这段代码最终返回什么。

用好它们能让代码更短、更清晰；用错则会让返回值与预期不符，这是初学者最容易踩的坑之一。


## 什么是作用域函数

作用域函数本质上都是接收一个 lambda 的普通函数，区别只有两点：lambda 里怎么引用对象，以及整个调用返回什么。

引用对象有两种方式：作为 lambda 的接收者（用 this 访问），或作为 lambda 的参数（用 it 访问）。

返回值也有两种：返回 lambda 最后一行的结果，或返回对象本身。

这两点组合起来，就得到了五个最常用的作用域函数：let、run、with、apply、also。


## 五个作用域函数总览

下表先建立整体印象，后面再逐个展开。

表中最后一行 runCatching 严格说不是作用域函数，而是异常处理工具，因为它经常和作用域函数一起出现，这里一并列出。

记忆口诀：let 和 also 用 it，run、with、apply 用 this。

返回 lambda 结果的是 let、run、with；返回接收者本身的是 apply 和 also。


## let

let 把对象作为参数传给 lambda，用 it 引用，返回 lambda 最后一行的结果。

它最常见的用法是配合安全调用处理可空对象，只有对象非空时 lambda 才会执行。


## 实例

输出结果：

```text
站点：www.runoob.com
长度：14
空对象兜底长度：0
```

因为 let 返回 lambda 的结果，所以它也常用来把对象转换成另一种类型或格式。


## 实例

输出结果：

```text
RUNOOB - www.runoob.com
```


## run 与 runCatching

run 把对象作为接收者，用 this 引用，同样返回 lambda 的结果。

当 lambda 里要反复访问对象的成员时，run 比 let 更顺手，因为不用每次都写 it.。


## 实例

输出结果：

```text
RUNOOB -> www.runoob.com
对象本身也被修改：RUNOOB
```

run 还有不带接收者的形式，用来把几行语句收成一个有返回值的代码块。


## 实例

输出结果：

```text
计算 10 + 20
结果：30
```


### runCatching 与 Result

runCatching 自 Kotlin 1.3 起可用，它把代码块包起来执行，把成功或失败都装进 Result 对象返回，不再向外抛异常。


## 实例

输出结果：

```text
是否成功：false
是否失败：true
异常类型：NumberFormatException
安全取值：null
兜底取值：0
onFailure 收到：NumberFormatException
onSuccess 收到：100
```

常用的 Result 方法有 isSuccess、isFailure、getOrNull()、getOrDefault()、exceptionOrNull()、onSuccess() 与 onFailure()。

注意：runCatching 捕获的是 Throwable，其中包括协程的 CancellationException。在协程里使用它会吞掉取消信号，需要谨慎。


## with

with 不是扩展函数，它把接收者写在括号里，lambda 内用 this 引用，返回 lambda 结果。

它适合对一个已经存在的对象连续做多件事，代码读起来像一段普通的顺序逻辑。


## 实例

输出结果：

```text
Runoob - www.runoob.com
builder 也被修改：Runoob - www.runoob.com
```

with 的接收者不能是 null，如果对象可能为空，要先判空，或者改用 ?.run。


## apply

apply 用 this 引用接收者，但返回的是接收者本身，而不是 lambda 的结果。

这个特性让 apply 成为配置对象的首选：花括号里设置属性，整个表达式的结果就是配置好的对象。


## 实例

输出结果：

```text
Site(name=RUNOOB, url=www.runoob.com, visits=100)
类型仍是 Site：Site
```

因为返回的是对象本身，apply 也常用来在创建对象后立即执行一次初始化逻辑。


## also

also 自 Kotlin 1.1 起可用，它用 it 引用接收者，返回接收者本身。

它与 apply 的唯一区别是引用方式，因此更适合做与对象配置无关的附加操作，例如打印日志、参数校验。


## 实例

输出结果：

```text
创建完成，元素个数：2
[Runoob, RUNOOB, www.runoob.com]
```

把 also 串在链式调用中间，可以在不打断链的前提下观察每一步的值。


## 选择决策表

遇到具体场景时，按下面这张表选择即可。

再补一条经验：如果一个函数返回的是接收者，它的价值在于不打断链式调用；如果返回的是 lambda 结果，它的价值在于把对象转成别的值。


## 常见误用

下面三个问题在实际代码里出现频率最高，写之前先想清楚返回的是谁。


### 把 apply 的返回值当成 lambda 的结果

apply 返回接收者，所以下面这段代码拿到的不是大写字符串。


## 实例

输出结果：

```text
runoob
RUNOOB
```

apply 里的 uppercase() 确实执行了，只是返回值被丢弃了，因为 apply 只关心对象本身。


### 嵌套时 it 被遮蔽

连续嵌套两个用 it 的作用域函数时，内层的 it 会遮蔽外层，代码虽然能编译，但很容易读错。


## 实例

输出结果：

```text
[RUNOOB, KOTLIN]
[runoob], [kotlin]
```

另一种做法是把其中一层改成 this 形式的 run，这样 it 就不会冲突。


### 在可空对象上忘记安全调用

作用域函数本身不会处理 null，可空对象必须先判空或用 ?.。


## 实例

输出结果：

```text
执行了：RUNOOB
also 也能配合安全调用：RUNOOB
```


## 后续章节

- 常见问题
- let 和 run 都能返回结果，怎么选
- apply 和 also 都返回对象，怎么选
- with 和 run 有什么区别
- 作用域函数会影响性能吗

## 复习重点

- 能说明 `Kotlin 作用域函数` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
