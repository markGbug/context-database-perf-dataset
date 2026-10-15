# Swift：Swift Sendable 与严格并发

- 来源：[Swift Sendable 与严格并发](https://www.runoob.com/swift/swift-sendable.html)
- 分类：移动开发
- 技术：Swift
- 笔记类型：学习笔记
- 章节序号：3448

## 本章内容

Swift 6 最重要的变化，是把「并发安全」从开发者自觉遵守的约定，变成了编译器强制检查的规则。

这套规则的核心是一个叫 Sendable 的协议：它回答同一个问题——这个值能不能安全地跨越并发边界，被另一条线程或另一个 actor 使用。

本篇从数据竞争讲起，再说明 Sendable 的自动推导、手动标注、@unchecked Sendable 的代价，最后给出从 Swift 5 迁移到 Swift 6 的完整路径。

注意：本页示例均在 Swift 6 语言模式下验证。用命令行脚本方式运行时，需要显式加上 -swift-version 6，否则 swift 命令默认仍按 Swift 5 的宽松规则编译，很多错误不会出现。


## 数据竞争：并发里最难查的一类 bug

数据竞争（data race）指两条以上线程同时访问同一块内存，其中至少一次是写操作，而且没有任何同步机制。

它的可怕之处在于「不一定出错」：多数时候结果正确，偶尔给出错误结果，或者干脆崩溃，换台机器又复现不了。


## 实例

上面这段代码每次运行的结果都不一样，可能小于 1000，也可能崩溃。

问题不在于代码写得「不够小心」，而在于编译器完全无法知道 counter 会被多条线程共享。

Sendable 就是为了让编译器能知道这件事：如果一个值被标记为 Sendable，就表示把它交给另一条线程是安全的。

数据竞争和竞态条件不是一回事：数据竞争是「同一时刻访问同一内存」这个客观事实；竞态条件是「结果依赖执行顺序」这个逻辑问题。Sendable 消除的是前者，后者要靠正确的同步设计。


## Sendable 协议是什么

Sendable 是一个「标记协议」，它没有任何必须实现的要求。

一个类型遵循 Sendable，等于向编译器承诺：这个类型的值可以安全地跨并发域传递。

它出现在两类位置：泛型约束 T: Sendable，以及闭包类型 @Sendable () -> Void。

下面这张表列出了常见类型的 Sendable 状态，这是理解后续所有规则的基础。

这张表里最容易记错的是最后两行：结构体自动推导，类不自动推导。


## 自动推导 Sendable

结构体和枚举只要所有存储属性都是 Sendable 的，就自动满足 Sendable，不需要写任何标注。


## 实例

```text
RunoobConfig 满足 Sendable
Int 满足 Sendable
String 满足 Sendable
```

注意 RunoobConfig 并没有写 : Sendable，但把它传给 T: Sendable 的泛型函数完全不报错。

反过来，只要有一个属性不满足，整个结构体就不满足。


## 实例

```text
error: type 'RunoobBad' does not conform to the 'Sendable' protocol
```

枚举同样会逐层推导，关联值全部 Sendable 时整个枚举就 Sendable。


## 实例

```text
success("RUNOOB")
ok
```

类的规则完全不同：即使一个类满足「final + 所有存储属性都是不可变且 Sendable」的条件，编译器也不会自动推导，必须显式写出来。


## 实例

```text
RunoobSite 满足 Sendable
```

如果这个类里出现了可变存储属性，显式声明 Sendable 会直接被编译器拒绝。


## 实例

```text
error: stored property 'name' of 'Sendable'-conforming class 'RunoobSite' is mutable
```


## 手动标注 Sendable 的几种正确做法

当类确实需要跨并发域传递，又带有可变状态时，正确做法是用同步原语把状态保护起来，再声明 Sendable。

Swift 6 提供了 Synchronization 模块里的 Mutex，这是目前最推荐的方式。


## 实例

```text
1
2
```

只有不可变状态的类，声明 Sendable 后不需要任何同步，因为没有任何东西可以被改坏。

被全局 actor 隔离的类型，例如 @MainActor 标注的类，也自动满足 Sendable，因为所有访问都被强制串行化到主 actor 上。


## 实例

```text
RunoobVM 满足 Sendable
[Int] 满足 Sendable
[String: String] 满足 Sendable
```

另一个常见场景是全局可变状态。Swift 6 不允许顶层的全局 var 被非隔离的代码直接读写，解决办法是把它收进一个命名空间并标注 @MainActor。


## 实例

```text
www.runoob.com
```


## @unchecked Sendable 的风险

有些类无法用编译器的规则证明安全，但开发者知道自己在做什么，这时可以写 @unchecked Sendable。

「unchecked」的含义非常直接：跳过编译器的检查，后果自负。


## 实例

```text
www.runoob.com
```

上面这段代码可以正常编译运行，但它并不是「被证明安全」，而是「被声明为安全」。

危险就在于：@unchecked Sendable 加上去之后，编译器从此对这个类不再做任何检查，写错也不会提示。


## 实例

这段代码一样能编译通过，但它在多线程下就是彻底的数据竞争。

使用原则：先尝试用 actor、Mutex、不可变状态等编译器能理解的方式解决问题；只有当这些方式都不适用，并且你确实用底层同步原语保护了全部可变状态时，才使用 @unchecked Sendable。它应当是最后手段，而不是消除报错的快捷方式。


## Swift 6 语言模式的严格检查

Swift 6 模式并不是引入了新的语法，而是把原来只给警告的问题升级成了编译错误。

最典型的一类是 @Sendable 闭包捕获了非 Sendable 的值。


## 实例

```text
error: capture of 'box' with non-Sendable type 'RunoobBox' in a '@Sendable' closure
```

同一份代码在 Swift 5 模式下运行时不会报任何错，这正是很多人升级时突然「冒出一堆错误」的原因。

第二类常见错误是全局可变状态被非隔离代码访问。


## 实例

```javascript
error: main actor-isolated var 'runoobGlobalCounter' can not be mutated from a nonisolated context
```

如果这个全局变量确实只在单线程里使用，可以用 nonisolated(unsafe) 显式关掉检查。


## 实例

```text
1
```

开启 Swift 6 模式的方式有三种，按使用场景选择即可。


## 从 Swift 5 迁移到 Swift 6 的路径

官方并不要求一步到位。Swift 5 模式下有一个 -strict-concurrency 选项，可以分三档逐步收紧检查。

可以把这三个档位理解成「先看警告、再改代码、最后开错误」的渐进过程。

```text
# 在 Swift 5 模式下逐步收紧检查，问题先以警告形式出现
swiftc -swift-version 5 -strict-concurrency=targeted Runoob.swift
swiftc -swift-version 5 -strict-concurrency=complete Runoob.swift

# 全部警告处理完之后，切换到 Swift 6 模式
swiftc -swift-version 6 Runoob.swift
```

迁移时按下面的顺序处理，通常比逐个改报错要快得多。

依赖的第三方库还没适配时，可以在 import 前加 @preconcurrency，让编译器按 Swift 5 的规则使用这个模块，给自己争取时间。

写法是 @preconcurrency import 模块名，例如项目依赖了一个尚未适配严格并发的网络库 RunoobLegacyKit，就先这样导入它，等依赖升级后再去掉这个前缀。


## 常见问题


### 结构体一定满足 Sendable 吗

不一定。只有当它全部存储属性都 Sendable 时才满足。

只要有一个属性是普通 class，整个结构体就不满足，而且这个判断是递归的。


### actor 为什么天然是 Sendable

因为 actor 的内部状态只允许通过 await 访问，编译器会自动把它串行化。

因此把 actor 实例交给另一条线程是安全的，它自己会处理隔离。


## 后续章节

- @unchecked Sendable 可以随便加吗
- Task 和 Task.detached 在 Sendable 上有什么区别
- 为什么我的 Swift 5 项目完全没有这些报错

## 复习重点

- 能说明 `Swift Sendable 与严格并发` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
