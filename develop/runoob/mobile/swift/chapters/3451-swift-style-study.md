# Swift：Swift 编码规范

- 来源：[Swift 编码规范](https://www.runoob.com/swift/swift-style.html)
- 分类：移动开发
- 技术：Swift
- 笔记类型：学习笔记
- 章节序号：3451

## 本章内容

代码写出来是给人看的，顺带才让编译器读懂。

同样的功能，不同的人可以写出完全不同的 Swift 代码，可读性差别巨大。

本文先讲 Apple 官方 API 设计指南的核心要点，再落到命名、格式化这些每天都要打交道的细节，最后用一张反模式对照表把常见坏味道一次讲清。


## 为什么需要编码规范

规范不是审美问题，它直接影响三件事：读代码的速度、改代码的风险、协作时的沟通成本。

Swift 的语法本身就在鼓励某些写法，比如值类型、可选绑定、协议扩展，顺着语言的设计走，代码会自然变短变清楚。

下面这套约定大部分来自 Apple 官方的 API Design Guidelines，也就是设计 Foundation 和 SwiftUI 时用的同一套标准。


## 官方 API 设计指南要点

指南的第一条是「调用处的清晰度比简洁更重要」，其余要点都可以看作这条的展开。

命名时不要盯着定义处怎么写最短，而要想象调用处读起来是什么样子。

下面这段代码把「参数标签成句」和「文档注释写契约」放在一起演示。


## 实例

```text
位移：3, 4
RunoobPoint(x: 8, y: 12)
```

注意：Swift 3 起所有参数默认只有局部名，首参数也不例外。需要外部标签时必须显式写 func f(label name: Type)，不能再按 Swift 2 的规则调用。


## 命名约定

命名是规范里收益最高的一项，改一个名字的成本极低，但它会被阅读成百上千次。


### 大小写与词法

类型、协议、枚举用大驼峰（UpperCamelCase），属性、方法、参数、局部变量用小驼峰（lowerCamelCase）。

不要用匈牙利命名法，把类型写进名字里：strName、iCount 这类写法在 Swift 里没有意义，因为类型系统会告诉你。


### 布尔属性用 is / has / can 前缀

布尔属性应该读起来像一句断言，放进 if 里就是一句自然语言。

对比一下：if article.published 读起来像名词，if article.isPublished 才像判断。


### 避免缩写

除社区公认的缩写（如 URL、ID、JSON）外，不要自创缩写。

viewCount 比 vc 清楚，message 比 msg 清楚，多打几个字母换来的是别人少猜一次。

下面这段代码把名词命名、布尔前缀、-ed 结尾的排序方法放在一起。


## 实例

```text
["Swift 进阶"]
["Swift 并发", "Swift 入门", "Swift 进阶"]
```


## 格式化与缩进

格式化是最不值得争论的问题，用工具定死，团队里每个人就都不用再想它。

Swift 工具链自带 swift format，可以格式化代码，也可以只做检查。

```java
$ swift format lint RunoobPoint.swift                 # 检查风格问题，只报错不改文件
$ swift format format RunoobPoint.swift               # 把格式化结果写到标准输出
$ swift format format --in-place RunoobPoint.swift    # 原地改写文件
```

假设源文件里缩进用了 4 个空格、冒号后没有空格，检查会给出这样的提示。

```text
RunoobPoint.swift:1:8: warning: [TypeNamesShouldBeCapitalized] rename the struct 'runoobPoint' using UpperCamelCase; for example, 'RunoobPoint'
RunoobPoint.swift:2:1: warning: [Indentation] unindent by 2 spaces
RunoobPoint.swift:2:11: warning: [Spacing] add 1 space
RunoobPoint.swift:3:1: warning: [Indentation] unindent by 2 spaces
RunoobPoint.swift:3:11: warning: [Spacing] add 1 space
```

格式化后的结果如下，注意它把缩进统一成了 2 个空格，并给冒号后补上了空格。

```java
struct runoobPoint {
  var x: Int
  var y: Int
}
```

注意：swift format 默认缩进是 2 个空格，而 Xcode 默认是 4 个空格。两者都不算错，关键是团队统一。可以在项目根目录放一份 .swift-format 固定下来。


## 实例

上面这份配置把缩进改成 4 个空格，并把单行长度上限设为 100 个字符。

除了缩进，下面这几条是 Swift 社区基本没有争议的排版约定。


## 惯用法

规范解决「怎么写不难看」，惯用法解决「怎么写更像 Swift」。

下面五条是日常代码里出现频率最高的，用熟了代码量会明显下降。


### 优先使用 let

值一旦确定就不再改变，就用 let 声明。

这不是洁癖：let 让编译器帮你拦住意外的重新赋值，也让读代码的人少一个需要追踪的状态。


### 用 guard 提前退出

前置条件不满足就立刻返回，主流程留在最外层，避免一层套一层的 if。


## 实例

```text
欢迎，Runoob（dev@runoob.com）
欢迎，Runoob（dev@runoob.com）
```

两个函数结果完全一样，但 guard 版本没有嵌套，异常分支一眼可见。

循环里同样适用：不满足条件就 continue，循环体不用再包一层 if。


## 实例

```text
有效条目：Runoob
有效条目：www.runoob.com
有效条目：RUNOOB
```


### 用 if let 同名简写

当可选值变量名和要绑定的常量名相同时，可以省略 = 变量名 这一半。

这个简写从 Swift 5.7 起可用（SE-0345），if let 和 guard let 都支持。


## 实例

```text
站点：www.runoob.com
欢迎访问 www.runoob.com
链接：https://www.runoob.com
无链接
```

更多可选类型的写法见《Swift 可选类型》。


### 优先使用值类型

能建模成 struct 或 enum 的，就不要用 class。

值类型在赋值和传参时天然产生独立副本，不需要担心别人在别处偷偷改掉你的数据。


## 实例

```text
1 100
```

什么时候才需要 class？需要身份（identity）、需要继承、或者需要被多处共享同一个可变状态时。详见《Swift 结构体》里的对比表。


### 用协议扩展共享实现

多个类型需要同一段实现时，把默认实现写进协议扩展，而不是复制粘贴到每个类型里。

一处修改，所有遵循类型同时生效。


## 实例

```text
你好，Runoob
你好，www.runoob.com
```

注意：协议扩展里的成员默认不走动态派发。如果类型自己也实现了同名方法，通过协议类型调用时可能仍然走到扩展里的版本。这个坑在《Swift 协议扩展与面向协议编程》里详细展开。


## 反模式对照表

下面这些写法都能编译通过，但会让代码更难读或更脆弱。

把它们当成一份速查清单，写代码时随手对照。


## 常见问题

下面这几个问题在团队落地规范时最常被问到。


### 缩进到底用 2 个还是 4 个空格？

两种都被广泛使用，官方工具 swift format 默认 2 个，Xcode 默认 4 个。

选一种写进配置文件，再用 swift format lint 在 CI 里卡住，就不用再讨论了。


## 后续章节

- guard 和 if 该怎么选？
- 必须用 swift format 吗？
- 协议扩展里的默认实现为什么不生效？
- 规范会不会和性能冲突？

## 复习重点

- 能说明 `Swift 编码规范` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
