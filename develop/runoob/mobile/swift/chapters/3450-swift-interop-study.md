# Swift：Swift 与 Objective-C / C 互操作

- 来源：[Swift 与 Objective-C / C](https://www.runoob.com/swift/swift-interop.html)
- 分类：移动开发
- 技术：Swift
- 笔记类型：学习笔记
- 章节序号：3450

## 本章内容

Swift 从设计之初就考虑了与既有生态的共存，因此调用 Objective-C 和 C 代码几乎是零成本的。

反方向也能走通：给 Swift 的成员加上 @objc，Objective-C 就能像使用原生类一样调用它们。

与 C++ 的互操作更晚一些，需要显式打开互操作模式，而且有明确的限制。

本篇按「Swift 调用对方」和「对方调用 Swift」两个方向，把三条边界都走一遍。


## 三种互操作边界

先看整体，三条边界的开启方式和限制各不相同。

桥接头文件（bridging header）是给 App target 用的，模块映射（module map）是给框架和包用的。


## Swift 调用 Objective-C

在 Xcode 工程里第一次添加 Objective-C 文件时，Xcode 会主动询问是否创建桥接头文件。

也可以在 Build Settings 的 Objective-C Bridging Header 里手动指定一个头文件路径。

桥接头文件里 #import 进来的 Objective-C 头文件，Swift 代码可以直接使用，不需要再 import。


## 实例


## 实例


## 实例

```text
Hello, RUNOOB
```

用命令行验证时，对应的参数是 -import-objc-header。

```text
$ swiftc -swift-version 6 -import-objc-header RunoobGreeter.h \
    -o runoob_app app.swift RunoobGreeter.m -framework Foundation
$ ./runoob_app
Hello, RUNOOB
```

重要细节：头文件里的 NS_ASSUME_NONNULL_BEGIN 和 NS_ASSUME_NONNULL_END 不能省。没有它，Objective-C 的 NSString * 会被 Swift 导入成 String!，打印出来就是 Optional("Hello, RUNOOB")，容易埋下隐式解包崩溃的隐患。


## Objective-C 调用 Swift：@objc 与 -Swift.h

编译器会为每个含 Swift 代码的模块生成一个 Objective-C 头文件，名字是 模块名-Swift.h。

框架里通常是 产品名-Swift.h，命令行编译时由 -module-name 决定。

Objective-C 文件只要 #import "RunoobService-Swift.h"，就能使用 Swift 里标记了 @objc 的成员。


## 实例


## 实例

```text
$ ./runoob_objc_app
Hello, Runoob, welcome to RUNOOB
RUNOOB-1.0
```

生成的头文件里，对应的声明长这样。

```text
@interface RunoobService : NSObject
@property (nonatomic, copy) NSString * _Nonnull site;
- (NSString * _Nonnull)greet:(NSString * _Nonnull)name SWIFT_WARN_UNUSED_RESULT;
- (NSString * _Nonnull)runoobVersion SWIFT_WARN_UNUSED_RESULT;
- (nonnull instancetype)init OBJC_DESIGNATED_INITIALIZER;
@end
```

这里有一个特别容易踩的坑：生成的 -Swift.h 只包含 public 和 open 的成员。

把上面的 public 都去掉，头文件里就什么都找不到，Objective-C 端会直接报 unknown receiver。


## @objc、@objcMembers 与 dynamic

这三个关键字经常一起出现，但作用并不相同。

@objc 后面可以跟一个括号指定选择器名，这就是前面例子里 @objc(runoobVersion) 的用法。

不指定时，Swift 会把方法名转成对应的 Objective-C 选择器，参数标签的映射规则由编译器处理。

dynamic 单独使用时表示「这个成员必须动态派发」，加上 @objc dynamic 则表示「通过 Objective-C 消息机制动态派发」，这是 KVO 和 swizzling 的前提。

注意：标了 @objc 的成员，参数和返回值的类型必须能表示成 Objective-C 类型。例如把一个 Swift 结构体当作参数传进去，编译器会直接报错：instance method cannot be marked '@objc' because the type of the parameter cannot be represented in Objective-C。


## C 互操作

Swift 调用 C 和调用 Objective-C 的方式一样，通过桥接头文件或模块映射即可。


## 实例


## 实例

```text
$ swiftc -swift-version 6 -import-objc-header runoob.h -o runoob_app app.swift helper.c
$ ./runoob_app
42
14
```

反方向，把 Swift 函数导出给 C 使用，需要 @_cdecl 并指定一个 C 符号名。


## 实例


## 实例

```text
$ swiftc -swift-version 6 -parse-as-library -o runoob_app main.c lib.swift
$ ./runoob_app
42
14
```

注意 -parse-as-library 不能少，否则 Swift 会把 lib.swift 当成主文件，和 main.c 的 main 函数冲突。

C 互操作的核心是 UnsafePointer 家族，它们的语义差别很大。

不要自己持有这些指针，而是用 withUnsafe... 系列函数，在闭包内临时使用。


## 实例

```text
地址可读，值为 42
字节数：6
总和：60
```

这些函数保证指针只在闭包执行期间有效，出了闭包就不应该再使用，这样就把悬垂指针的风险降到了最低。


## 与 C++ 互操作

Swift 5.9 起支持直接调用 C++ 代码，需要打开互操作模式 -cxx-interoperability-mode。

C++ 的类型通过模块映射暴露给 Swift，写法与 C 的模块映射类似，但需要 requires cplusplus。


## 实例


## 实例


## 实例

```text
$ swiftc -swift-version 6 -cxx-interoperability-mode=default -I . -o runoob_cxx_app app.swift
$ ./runoob_cxx_app
42
8080
```

这套互操作能力很强，但边界也很清楚，有两件事做不了。

第一是不支持 C++ 异常。一个可能抛出异常的 C++ 函数在 Swift 看来就是普通函数，异常一旦跨过边界，运行时会直接终止程序。

```text
$ ./eapp
C++ exception handling detected but the Swift runtime was compiled with exceptions disabled
```

第二是不支持继承 C++ 的类和重写虚函数，Swift 无法把 C++ 类当成父类。

```text
error: inheritance from non-protocol, non-class type 'RunoobBase'
```

因此 C++ 互操作更适合「调用无状态或值语义的工具代码」，而不是把整个 C++ 类层次搬进 Swift。


## 常见问题


### 为什么 Objective-C 端找不到我的 Swift 类

先确认这个类是否写了 @objc 或 @objcMembers。

再确认它和它的成员是不是 public 或 open，生成的 -Swift.h 只包含这两个级别的成员。


### 桥接头文件和模块映射该怎么选

App target 用桥接头文件，在 Build Settings 里指定路径即可。

框架、库和 Swift Package 用模块映射，因为这类产物需要把 C 头文件作为模块的一部分导出。


### @objc 会带来性能损失吗

会有一点，因为调用走的是 Objective-C 消息派发，而不是 Swift 的静态派发。

只在确实需要给 Objective-C 使用或需要运行时特性时才加，不要无差别地给整个类加 @objcMembers。


### withUnsafePointer 返回的指针能保存下来以后用吗

不能。它只在闭包执行期间有效，闭包返回后指针就失效了。

需要长期持有内存时，应该用 UnsafeMutablePointer.allocate 手动分配并自己负责释放。


## 后续章节

- C++ 互操作需要改 C++ 代码吗

## 复习重点

- 能说明 `Swift 与 Objective-C / C` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
