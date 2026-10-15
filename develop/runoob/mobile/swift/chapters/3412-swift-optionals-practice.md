# Swift：Swift 可选(Optionals)类型

- 来源：[Swift 可选类型](https://www.runoob.com/swift/swift-optionals.html)
- 分类：移动开发
- 技术：Swift
- 笔记类型：练习笔记
- 章节序号：3412

## 本章内容

可选类型（Optional）用来表示「这里可能有一个值，也可能没有值」。

当变量可能为「空」时，就把它声明成可选类型；Swift 会强制你在使用前处理这种「空」的情况，从而在编译期消灭大量空指针问题。

本文基于 Swift 6.x，示例可直接用 swift 命令运行。


## Optional<T> 与 T?

可选类型本质是一个泛型枚举 Optional<T>，它只有两个取值：.some(值) 和 .none。

Swift 提供了后缀问号 T? 作为 Optional<T> 的简写，两者完全等价。


## 实例

运行结果：

```text
Optional(42)
Optional(42)
nil
Optional(7) nil
nil
Optional("www.runoob.com")
Optional([1, 2, 3])
nil
```

从输出可以看出，可选值打印时会带上 Optional(...)，为 nil 时直接打印 nil。

注意：声明可选数组时，问号作用在整个数组类型上，写成 [Int]?；不要使用把方括号写在类型名后面的旧语法，Swift 早已移除那种写法。


## nil 不是布尔值

这是初学者最容易带进来的其他语言习惯：把可选值直接当条件用。

在 Swift 里，if、while 的条件必须是真正的 Bool，可选值不能自动转换成布尔值。


## 实例

编译报错：

```text
error: optional type 'String?' cannot be used as a boolean;
test for '!= nil' instead
```

正确写法是显式判断是否为空，或者用后面介绍的可选绑定。


## 实例

运行结果：

```text
有值
```

同样，nil 也不是布尔字面量，Bool 的取值只有 true 和 false 两个。


## 实例

编译报错：

```text
error: 'nil' cannot initialize specified type 'Bool'
note: add '?' to form the optional type 'Bool?'
```

如果确实需要「没有值」的布尔状态，应该声明为 Bool?，再用可选绑定取出真正的布尔值。


## 强制解包

在可选值后加感叹号 !，表示「我确定这里一定有值，直接取出来」。

强制解包的结果不再是可选类型，可以直接参与运算。


## 实例

运行结果：

```text
www.runoob.com
网站是 www.runoob.com
```

但如果可选值实际上是 nil，强制解包会让程序直接崩溃。


## 实例

运行结果：

```java
Fatal error: Unexpectedly found nil while unwrapping an Optional value
```

注意：强制解包是运行时检查，不是编译期检查。除非能百分百确定有值，否则应该用可选绑定或空合运算符。


## 可选绑定 if let 与 guard let

可选绑定会把解包后的值绑定到一个新的常量，只有确实有值时才执行对应分支，完全避免了崩溃风险。

if let 的作用域只在分支内部；guard let 则用于提前退出，解包后的值在后续代码中一直可用。


## 实例

运行结果：

```javascript
可选绑定得到：www.runoob.com
guard let 解包成功：RUNOOB，长度 6
值为 nil，直接返回
```

实际编码中，函数参数校验、字典取值、类型转换这类「不满足就退出」的场景，优先用 guard let，可以减少嵌套层级。


## 简写绑定 if let x

如果绑定出的常量名和可选变量名相同，Swift 允许省略 = 变量名，直接写 if let x {。

这个简写同样适用于 guard let，代码更短，也少了重复的变量名。


## 实例

运行结果：

```text
简写绑定：www.runoob.com
guard 简写绑定：100
没有值
两个都有值：www.runoob.com - 2026
至少有一个为 nil，条件不成立
```

多个可选值用逗号连接时，必须全部有值才会进入分支，等价于连续的 &&。


## 空合运算符 ??

?? 用来给可选值提供默认值：左边有值就取左边，为 nil 就取右边。

它比 if let 更紧凑，适合「有就用、没有就用默认值」的场景。


## 实例

运行结果：

```text
www.runoob.com
RUNOOB
0
```

注意 ?? 右侧的类型必须与左侧解包后的类型一致，否则编译器会报类型不匹配。


## 隐式解包可选 T!

在类型后加感叹号声明的可选类型叫隐式解包可选（Implicitly Unwrapped Optional），使用时不需要再写 !。


## 实例

运行结果：

```text
4
```

隐式解包可选本质上仍是可选类型，只是每次访问都自动强制解包，所以一旦为 nil 依然会崩溃。

注意：隐式解包可选已不推荐使用。它只适合「创建后一定会被赋值、之后不再为 nil」的少数场景，现代 Swift 代码应优先用普通可选类型配合可选绑定。


## 常见问题

最后整理几个高频疑问。


### 为什么打印可选值会多出 Optional

因为打印的是可选类型本身而不是里面的值。想打印干净的内容，先解包，例如 print(site ?? "") 或先 if let 再打印。


### 可选类型能比较吗

可以。当内部类型支持 == 时，可选值之间以及可选值与 nil 都能比较，例如 site == nil、a == b。


### 多次解包怎么写更简洁

用简写绑定配合逗号，例如 if let a, let b, let c { ... }；也可以把额外条件直接跟在后面，如 if let a, a > 0 { ... }。


### 可选链和可选绑定有什么区别

可选绑定是「取出来再用」，可选链是「沿着可选值一路访问下去，中途为 nil 就整体返回 nil」，详见《Swift 可选链》。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Swift 可选类型` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
