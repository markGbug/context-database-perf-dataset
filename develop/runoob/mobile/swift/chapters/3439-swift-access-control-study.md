# Swift：Swift 访问控制

- 来源：[Swift 访问控制](https://www.runoob.com/swift/swift-access-control.html)
- 分类：移动开发
- 技术：Swift
- 笔记类型：学习笔记
- 章节序号：3439

## 本章内容

访问控制决定「谁可以看到、使用、继承一段代码」。

Swift 一共有六个访问级别，从最严格到最开放依次是 private、fileprivate、internal、package、public、open。

很多旧资料只讲到 public，并且把 private 说成「只能在类中访问」，这两点都不准确。

本篇把六个级别逐个讲清，并说明 open、package、private(set) 这些容易被忽略的用法。


## 六个访问级别一览

先看整体对比表，后面的每一节再逐个展开。

这里有两个容易踩坑的地方。

第一，public 不是最高级别，open 才是，而且 open 只能用于类以及类的成员。

第二，package 的可见范围比 internal 大、比 public 小，它针对的是「同一个 Swift Package 里的多个模块」。


## private：声明作用域加同文件扩展

private 是最严格的级别，但它并不等于「只能在类内部访问」。

准确的说法是：private 成员在声明所在的作用域以及同一个文件里的扩展中可见。


## 实例

```text
2
RUN****
www.runoob.com
```

可以看到，扩展里的 maskedToken() 直接读到了 token，编译完全没有问题。

常见误解：「private 只能在类中访问」是错的。Swift 4 起，private 的作用域已经扩展为「声明所在作用域 + 同文件扩展」。把类型定义和它的扩展拆到两个文件里，扩展就无法再访问 private 成员了，这时需要用 fileprivate。


## fileprivate：整个源文件可见

fileprivate 把可见范围放宽到整个 .swift 文件，同一个文件里的其他类型也能访问。


## 实例

```text
站点：www.runoob.com
```

如果上面的 site 改成 private，RunoobLogger 就访问不到了，因为两个类型是两个独立的作用域。

实际开发中，fileprivate 通常用于「同一个文件里的一组类型需要共享某个实现细节」的场景。


## internal：模块内的默认级别

不写任何修饰符时，成员就是 internal，可见范围是整个模块。

模块（module）指一个编译单元：一个 App target、一个 framework、一个 Swift Package 里的一个 target 都算一个模块。

所以「同一个模块内可见」通常就等价于「同一个 target 内可见」，跨 target 使用就需要提升到 public。

前面几节的单文件示例其实都只能验证 internal 以内的行为，跨模块的规则要用真实的 Swift Package 才能观察。


## package：同一个包内的多个模块

一个 Swift Package 里往往有多个 target，它们各自是独立模块，互相之间默认看不到对方 internal 的成员。

如果不想把内部 API 暴露成 public，又想在同包的多个模块间共享，就用 package。

下面这个包里有两个 target：库目标 RunoobKit 和可执行目标 RunoobApp。

```text
Sources/
├── RunoobKit/
│   └── RunoobKit.swift      // 库模块，对外暴露 package 级别函数
└── RunoobApp/
    └── main.swift           // 可执行模块，同包内可访问 package 成员
```


## 实例


## 实例

```text
RUNOOB
```

如果把这个包作为依赖，从另一个包里去调用 runoobInternalName()，编译会直接失败。

```text
error: cannot find 'runoobInternalName' in scope
```

也就是说，package 的边界是「包」，而 internal 的边界是「模块」。

需要特别强调的是：package 放宽的只是可见性，不包含继承权限。

一个 package 类在包内的另一个模块里依然无法被继承，仍然必须声明成 open 才行。

实现细节：编译器需要一个 -package-name 参数才能识别 package 边界。用 SwiftPM 构建时这个参数会自动传好，不需要手动配置；如果直接用 swiftc 手工编译多模块工程，就要自己加上。


## public：跨模块可见，但不能继承或重写

public 让成员在任何模块中都能被访问，是框架对外 API 的常用级别。

但它有一个关键限制：模块外的代码可以使用，却不能继承这个类，也不能重写它的成员。

```text
error: cannot inherit from non-open class 'RunoobHelper' outside of its defining module
```

这个设计是有意的：框架作者用 public 表示「你可以调用，但我不想让你改动我的行为」。


## open：跨模块可继承与重写

只有 open 才允许模块外继承类、重写方法或属性。

open 只能修饰类本身，以及类中可以被子类重写的成员；结构体、枚举、协议不能用它。

下面的包演示了三种级别在跨模块场景下的差别。


## 实例


## 实例

```text
RunoobChild
www.runoob.com
www.runoob.com
RUNOOB
```

把 RunoobBase 的 open 改成 public，上面这段继承代码就会报前面那条错误。

另一个细节是：open 类的成员如果被标记为 public，那么它在模块外仍然不可重写，只有标记为 open 的成员才可以。


## private(set)：对外只读，对内可写

访问级别可以分别控制读取和写入，写法是 private(set) 或更一般的 访问级别(set)。

它表示 getter 保持原来的级别，setter 降级到括号里的级别。


## 实例

```text
1
```

读取没问题，但外部一旦尝试赋值就会被编译器拦下。


## 实例

```text
error: cannot assign to property: 'visitCount' setter is inaccessible
```

这种写法适合「计数、状态」这类只允许内部修改、外部只读的属性，比写一个计算属性更简洁。

同理，internal(set) 表示「模块外只读、模块内可写」，fileprivate(set) 表示「文件外只读、文件内可写」。


## 为什么 Swift 没有 protected

来自 C++ 或 Java 的开发者常会问：为什么 Swift 没有 protected？

原因在于访问控制的组织维度不同。C++ 的 protected 以「类继承层次」为单位，而 Swift 的访问控制以「模块」和「文件」为单位。

Swift 大量使用值类型和协议扩展，这些都没有继承关系，protected 在这种结构下没有意义。

另外，protected 会让子类和父类产生强耦合，而 Swift 更鼓励用协议抽象、组合和模块边界来管理依赖。

需要「只给内部实现看」的成员时，Swift 的做法是用 internal 或 fileprivate 控制范围，而不是依赖继承关系。


## 构造器的可见性

构造器遵循同样的访问规则，但有一个特别容易忽略的点：隐式生成的构造器不会自动提升到 public。

一个 public 结构体，如果没写 init，它的成员逐一构造器仍然是 internal，跨模块就构造不出来。


## 实例

```text
error: 'RunoobPublicStruct' initializer is inaccessible due to 'internal' protection level
```

解决办法是显式写一个 public init，前面例子里已经这样做了。

反过来，把构造器设为 private 可以强制外部只能通过特定入口创建实例，这是单例模式的常见写法。


## 实例

```text
www.runoob.com
```

此时外部写 RunoobConfig() 会直接报错。

```text
error: 'RunoobConfig' initializer is inaccessible due to 'private' protection level
```


## 扩展的可见性

扩展本身可以带访问级别修饰符，它的作用是给扩展中所有成员设定一个默认级别。

例如 public extension 里的成员默认都是 public，不用逐个写。

扩展里的单个成员仍然可以覆盖这个默认值，但不能把级别提高到超出被扩展类型本身的可见性。


## 实例

```text
RUNOOB
```

这个例子再次说明 private 的作用域是「声明所在作用域 + 同文件扩展」，而不是「只能在声明它的那个大括号里」。

如果把这两个扩展拆到两个文件，reveal() 就访问不到 secret() 了。


## 常见问题


### 一个类型的成员可以比类型本身更开放吗

不可以。成员的最高可见性受限于它所在类型的可见性。

一个 internal 的结构体，即使把成员写成 public，实际效果仍然是 internal。


## 后续章节

- open 和 public 该怎么选
- package 和 internal 的边界怎么区分
- private(set) 会改变 getter 的级别吗
- 为什么我的 public 类在别的模块里继承不了

## 复习重点

- 能说明 `Swift 访问控制` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
