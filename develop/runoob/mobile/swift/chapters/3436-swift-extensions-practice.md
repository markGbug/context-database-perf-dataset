# Swift：Swift 扩展

- 来源：[Swift 扩展](https://www.runoob.com/swift/swift-extensions.html)
- 分类：移动开发
- 技术：Swift
- 笔记类型：练习笔记
- 章节序号：3436

## 本章内容

扩展（Extension）可以给一个已有的类型添加新功能，而不需要修改它的原始定义。

被扩展的类型可以是结构体、类、枚举，也可以是协议，甚至是 Swift 标准库里的 Int、String 这类内置类型。

本文所有代码基于 Swift 6.x 与 Xcode 16，示例可直接用 swift 命令运行。


## 扩展能做什么

先看一张能力清单，明确扩展的边界在哪里。

扩展的语法很简单，用关键字 extension 加上类型名，大括号里写新增的成员。


## 实例


## 扩展计算属性

扩展可以添加计算属性，但不能添加存储属性，因为存储属性需要额外的内存布局，而扩展不能改变类型已有的内存布局。

下面的例子给 Double 添加了三个单位换算的计算属性。


## 实例

运行结果：

```text
3.0 千米 = 3000.0 米
3.0 千米 = 0.03 厘米
RUNOOB
RUNOOB
RUNOOB
```

计算属性里用到的 self 就是被扩展的那个值本身，所以 3.0.km 等价于 3.0 * 1000.0。


## 扩展方法

上例中的 repetitions(task:) 就是扩展的实例方法，它接收一个闭包并重复执行。

如果扩展的是结构体或枚举，而方法需要修改实例自身，同样要加 mutating。


## 实例

运行结果：

```text
当前计数：2
```

注意：只有用 var 声明的结构体实例才能调用 mutating 方法。如果用 let 声明，编译器会报错。


## 扩展构造器

扩展可以给类型添加新的构造器，方便用另一种方式创建实例。

结构体的成员逐一构造器 init(width:height:) 由编译器自动生成，扩展里可以再补一个「按边长创建正方形」的构造器。


## 实例

运行结果：

```text
width = 5.0, height = 5.0
```

扩展里的构造器必须保证所有存储属性都被正确初始化，所以这里通过 self.init(...) 委托给已有的构造器完成。

注意：给类写扩展构造器时，只能添加便利构造器，不能添加指定构造器；指定构造器必须写在类体内部。


## 扩展下标

扩展可以给类型添加下标，让取值语法更自然。

下面的例子给 Int 添加下标，用来取出十进制数从右往左第 n 位的数字。


## 实例

运行结果：

```text
5 9 2 7
```

number[0] 是个位 5，number[8] 是最高位 7，下标从 0 开始计数。


## 扩展嵌套类型

扩展可以在已有类型内部添加嵌套类型，常见做法是把某个枚举放进被扩展的类型里，避免污染全局命名空间。


## 实例

运行结果：

```text
-7 是负数
0 是零
42 是正数
```

枚举 RunoobKind 的完整名字是 Int.RunoobKind，这样命名不会和项目里其他同名的枚举冲突。


## 扩展实现协议

这是扩展最常用的场景：类型在定义时不遵循协议，之后再通过扩展补上。

这样做的好处是，可以让类型定义保持简洁，把协议实现按功能拆分到多个扩展里。


## 实例

运行结果：

```text
Hello, RUNOOB! Welcome to www.runoob.com
Hello, Runoob!
```

String 是标准库类型，我们没有它的源码，但依然能通过扩展让它遵循自定义协议。


## 扩展泛型类型

泛型类型也可以被扩展。扩展里可以直接使用原有的类型参数，也可以给扩展加上 where 子句，让新功能只在特定条件下可用。


## 实例

运行结果：

```text
栈顶元素：30
是否包含 20：true
是否包含 99：false
弹出一个元素：30
栈是否为空：false
```

contains 用到了 == 比较，所以必须约束 Element: Equatable；不满足条件的栈类型上根本不会出现这个方法。


## 扩展不能添加存储属性与析构器

扩展只负责添加功能，不能改变类型的存储布局，因此不能添加存储属性，也不能添加析构器。

先看添加存储属性的结果：


## 实例

编译报错：

```text
error: extensions must not contain stored properties
```

再看添加析构器的结果，即使被扩展的是类也一样不行：


## 实例

编译报错：

```text
error: deinitializers may only be declared within a class, actor, or noncopyable type
```

析构器必须写在类体内部，扩展里无法声明。

注意：扩展也不能「重写」类型已有的方法或属性。如果你在扩展里定义了同名方法，编译器会报重复定义，而不是覆盖。


## 回溯符合与 @retroactive

回溯符合（retroactive conformance）指的是：在模块 C 里，让来自模块 A 的类型遵循来自模块 B 的协议，而 A、B 都不归你所有。

这种写法本身合法，但存在风险：如果将来 A 的作者自己也让该类型遵循了 B 的协议，两份实现就会冲突。Swift 6 会对此给出警告。

下面用三个文件模拟三个模块。第一个文件是 LibA，只定义一个类型：


## 实例

第二个文件是 LibB，只定义一个协议：


## 实例

第三个文件是 App，在这里写回溯符合。此时 RunoobPoint 与 RunoobFormattable 都是「外部类型」。


## 实例

用 swiftc 类型检查时会出现警告：

```text
warning: extension declares a conformance of imported type 'RunoobPoint'
to imported protocol 'RunoobFormattable'; this will not behave correctly
if the owners of 'LibA' introduce this conformance in the future
note: add '@retroactive' to silence this warning
```

按提示加上 @retroactive 即可消除警告，同时明确表达「我知道这个符合是跨模块的、可能冲突」。


## 实例

运行结果：

```text
RunoobPoint(x: 42)
```

@retroactive 只是一个「确认标记」，它不改变行为，只是让编译器不再警告。

注意：如果类型或协议中至少有一个是你自己模块里定义的，就属于普通符合，不需要也不应该加 @retroactive。硬加会得到警告 'retroactive' attribute does not apply。


## 后续章节

- 常见问题
- 扩展能替代子类吗
- 扩展能给协议添加默认实现吗
- 给同一个类型写多个扩展有影响吗
- 扩展里的 static 成员可以用吗
- 能不能扩展协议本身

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Swift 扩展` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
