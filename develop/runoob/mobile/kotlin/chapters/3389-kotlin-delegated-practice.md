# Kotlin：Kotlin 委托

- 来源：[kotlin 委托](https://www.runoob.com/kotlin/kotlin-delegated.html)
- 分类：移动开发
- 技术：Kotlin
- 笔记类型：练习笔记
- 章节序号：3389

## 本章内容

委托是一种基础的设计模式：一个对象把请求转交给另一个对象来处理。

Kotlin 用 by 关键字直接支持委托，编译器会自动生成转发代码，比手写委托类简洁得多。

Kotlin 的委托分为两类：类委托和属性委托，本章节会逐一讲解，并说明编译器的翻译规则。


## 类委托

类委托的写法是在类头后面加 : 接口 by 委托对象，编译器会为接口中的每个方法生成转发实现。


## 实例

输出结果为：

```text
BaseImpl: 10
```

编译器会把 b 保存到 Derived 的实例里，并生成 Base 接口的全部方法，把它们转发给 b。

你可以在 Derived 中重写某个方法，让它覆盖委托对象的行为。


## 实例

输出结果为：

```text
BaseImpl: 10
Derived
```


## 属性委托

属性委托把属性的读取和写入交给另一个对象来完成，语法是 val 或 var 属性名: 类型 by 委托表达式。

属性委托不需要实现任何接口，但必须提供 getValue()，var 属性还额外需要 setValue()。


## 实例

输出结果为：

```text
Example 读取了属性 p
Example 的 p 被赋值为 RUNOOB
```


### getValue 与 setValue 的签名要求

委托对象的这两个方法必须带 operator 关键字，参数和返回值都有明确约束。

对于扩展属性，thisRef 指的是被扩展的类型。


## 标准委托 lazy

Kotlin 标准库内置了常用的委托工厂方法，lazy() 是最常用的一个。

它接收一个 lambda，返回一个 Lazy<T> 实例，第一次读取属性时才执行 lambda 并记住结果，之后直接返回缓存值。


## 实例

输出结果为：

```text
computed!
Hello
Hello
```

局部变量也可以用 lazy 委托，这个特性从 Kotlin 1.1 起可用。


### LazyThreadSafetyMode

lazy() 的第二个可选参数控制多线程下的初始化行为，默认值是 SYNCHRONIZED。


## 实例

输出结果为：

```text
执行初始化
www.runoob.com
www.runoob.com
```

注意：默认的 SYNCHRONIZED 模式会让所有线程在首次访问时同步等待，如果初始化逻辑可能抛异常，再次访问时会重新尝试初始化，因此异常不会导致属性永久不可用。


## 可观察属性 observable 与 vetoable

Delegates.observable() 在每次赋值之后回调，适合做观察者模式。

它接收初始值和回调两个参数，回调有三个参数：属性对象、旧值和新值。


## 实例

输出结果为：

```text
name：初始值 -> 第一次赋值
name：第一次赋值 -> 第二次赋值
```

Delegates.vetoable() 的回调在赋值之前执行，返回 true 才允许写入，返回 false 则拒绝这次赋值。


## 实例

输出结果为：

```text
25
25
25
```


## 把属性存储在映射中

把属性委托给一个 Map 实例是很常见的用法，解析 JSON 或处理动态数据时尤其方便。

委托给 Map 时，属性的名字会作为 key 去映射里取值。


## 实例

输出结果为：

```text
菜鸟教程
www.runoob.com
```

如果要委托的是 var 属性，Map 必须换成 MutableMap，赋值会直接写回映射。


## 实例

输出结果为：

```text
菜鸟教程
RUNOOB
RUNOOB
```


## Delegates.notNull

有些属性的值无法在初始化阶段确定，Delegates.notNull() 就是为这种场景准备的。

它允许属性先声明后赋值，但在赋值之前读取会抛出异常。


## 实例

输出结果为：

```text
bar
```

如果跳过赋值直接读取，程序会抛出 IllegalStateException。


## 实例

输出结果为（省略堆栈信息）：

```text
Exception in thread "main" java.lang.IllegalStateException: Property notNullBar should be initialized before get.
```

注意：Delegates.notNull() 只适用于非空类型。它的语义是「延迟赋值但保证非空」，而 lateinit 也能达到类似效果，区别在于 lateinit 只能用于类属性，不能用于基本类型。


## 局部委托属性

委托不只可以用于类属性，局部变量也可以委托，这个特性从 Kotlin 1.1 起可用。

把局部变量委托给 lazy 就能实现「用到时才计算」的懒加载。


## 实例

输出结果为：

```text
执行规范化
结果：RUNOOB
执行规范化
```

如果某个分支根本不访问这个变量，它的初始化逻辑就完全不会执行，这正是懒加载的价值。


## provideDelegate

默认情况下，委托对象是在属性声明处直接创建的。

如果 by 右边的对象定义了 provideDelegate，编译器会改为调用它来创建真正的委托实例，这个特性从 Kotlin 1.1 起可用。

它最大的价值在于：可以在属性绑定阶段就做校验，而不必等到 getter 或 setter 执行时。


## 实例

输出结果为：

```text
菜鸟教程
```

如果把属性名写错，错误会在创建对象时立刻暴露，而不是拖到读取属性时才出现。


## 实例

输出结果为（省略堆栈信息）：

```text
Exception in thread "main" java.lang.IllegalArgumentException: 属性名必须是 name，实际是 siteName
```

provideDelegate 的参数与 getValue 相同，只影响辅助属性的创建，不会改变 getter 和 setter 生成的代码。


## 后续章节

- 翻译规则
- 实例
- 实例
- 常见问题

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `kotlin 委托` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
