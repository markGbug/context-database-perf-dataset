# Swift：Swift some 与 any

- 来源：[Swift some 与 any](https://www.runoob.com/swift/swift-opaque-types.html)
- 分类：移动开发
- 技术：Swift
- 笔记类型：学习笔记
- 章节序号：3442

## 本章内容

在 Swift 里，some P 和 any P 都可以表示「某个遵循协议 P 的类型」，但它们的含义完全不同。

some 是不透明类型：对外隐藏具体类型，但编译器知道它是唯一确定的一种类型。

any 是存在类型：运行时可以装任何遵循 P 的类型，代价是失去静态类型信息。

本文基于 Swift 6.x，示例可直接运行。


## 为什么需要这两种写法

先看一个共同的需求：函数返回的东西只要满足某个协议即可，具体类型不想暴露。

Swift 提供了两条路，一条是 some，一条是 any，它们解决的是不同问题。

下面分别展开。


## 不透明返回类型 some

在返回类型前写 some 协议名，就表示「我返回一个遵循该协议的类型，但具体是哪个类型不告诉你」。

调用者只能使用协议里声明的成员，看不到具体类型，也就无法依赖实现细节。


## 实例

运行结果：

```text
圆面积：12.5664
静态类型是 RunoobCircle
```

注意最后一行的输出：type(of:) 返回的仍然是真实的 RunoobCircle。

因为 some 隐藏的是编译期静态类型，运行时对象本身还是那个具体类型，只是你在代码里写不出它的名字。


### 同一个函数只能返回一种类型

some 要求函数所有返回语句的底层类型完全一致，否则编译报错。


## 实例

编译报错：

```javascript
error: function declares an opaque return type 'some RunoobShape',
but the return statements in its body do not have matching underlying types
note: return statement has underlying type 'RunoobCircle'
note: return statement has underlying type 'RunoobSquare'
```

这种「可能返回多种类型」的需求，正是 any 的用武之地。


## 存在类型 any

写 any 协议名 就得到一个可以存放任意遵循者的「盒子」，盒子在运行时会记住里面到底是什么类型。

同一个变量可以先装圆、再装方，数组里也能混放不同类型。


## 实例

运行结果：

```text
面积：3.1416
面积：9.0000
总面积：35.4159
元素个数：3
```

shapes 数组里同时有圆和方，用 some 是做不到的。

注意：从 Swift 5.7 起，写协议类型时必须显式加 any，例如 any RunoobShape。只写 RunoobShape 会得到一个警告，提示你改用 any 或泛型。


## some 与 any 的选择

两者不是替代关系，而是各有适用场景。判断标准很简单：调用点是否需要同时处理多种具体类型。

经验法则：能用泛型就用泛型，需要隐藏实现就用 some，确实需要运行时多态才用 any。

SwiftUI 里的 var body: some View 就是典型的不透明类型用法：每个视图的 body 返回一种具体视图，但对外只暴露 View 协议。


## 主关联类型

带关联类型的协议，可以在协议名后的尖括号里声明「主关联类型」，之后就能把关联类型直接写在类型表达式里。

Collection 的主关联类型是 Element，所以可以写 Collection<Int>。


## 实例

运行结果：

```text
10
元素个数：5
第一个元素：1
元素个数：3
去重后个数：3
```

自定义协议也能声明主关联类型，只要在协议名后用尖括号标出即可。


## 实例

运行结果：

```text
7
```

遵循者必须让 Item 与约束里的 Int 一致，否则编译器会报「类型不相等」。


## 常见问题

最后回答几个实际编码中容易卡住的问题。


### some 能不能用在属性上

可以用于计算属性，比如 var body: some View；但不能用来声明存储属性，因为存储属性需要确切的类型和内存布局。


### any 会不会有性能问题

会有一定开销。存在类型需要装箱，方法调用走动态派发；如果在热点代码里频繁调用，应优先考虑泛型或 some。


### any 里怎么拿回具体类型

用 as? 向下转型，判断成功后再访问具体类型独有的成员，详见《Swift 类型转换》。


### 为什么 SwiftUI 的 body 要用 some 而不是 any

因为每个视图的 body 只返回一种具体视图类型，用 some 可以避免装箱、走静态派发，同时不把实现细节暴露给使用者。


## 复习重点

- 能说明 `Swift some 与 any` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
