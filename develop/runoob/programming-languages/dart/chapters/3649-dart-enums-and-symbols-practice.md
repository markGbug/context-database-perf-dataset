# Dart：Dart 枚举与符号

- 来源：[Dart 枚举与符号](https://www.runoob.com/dart/dart-enums-and-symbols.html)
- 分类：编程语言
- 技术：Dart
- 笔记类型：练习笔记
- 章节序号：3649

## 本章内容

枚举（enum）用于定义一组有名字的常量值，让代码更具可读性。

本章介绍 Dart 枚举的定义方式、增强枚举（带方法和属性）以及 Symbol 和 Rune 类型。


## enum 枚举定义

枚举是一种特殊的类，用于表示固定数量的常量值。

最典型的场景是表示状态、方向、颜色等有限选项。


## 实例

```text
当前状态: Status.pending
索引值: 0
所有状态: [Status.pending, Status.approved, Status.rejected, Status.cancelled]
RUNOOB 状态: Status.pending, 索引: 0
RUNOOB 状态: Status.approved, 索引: 1
RUNOOB 状态: Status.rejected, 索引: 2
RUNOOB 状态: Status.cancelled, 索引: 3
解析出的状态: Status.approved
订单待处理
```

枚举和 switch 是绝配。当你在 switch 中处理所有枚举值时，Dart 编译器会检查你是否覆盖了所有情况。这能避免遗漏分支导致的 bug。


## 增强枚举（带方法和属性）

Dart 3.0 引入了增强枚举（Enhanced Enums），允许枚举拥有字段、方法和构造函数。


## 实例

```text
RUNOOB HTTP 状态: HttpStatus.notFound
状态码: 404
消息: 资源未找到
是否成功: false
是否客户端错误: true
找到状态: 资源已创建
未知状态码: null
```

增强枚举让枚举从"命名常量集合"升级为"有行为的类型"，可以封装与该枚举相关的逻辑。

增强枚举的构造函数必须是 const，成员变量必须是 final。这是因为枚举值本身就是编译时常量。


## Symbol 类型

Symbol 代表 Dart 程序中的标识符（变量名、函数名等）。

它在日常开发中不常用，主要在反射（Reflection）和代码生成场景中使用。


## 实例

```text
Symbol 1: Symbol("runoob")
Symbol 2: Symbol("helloWorld")
sym1 == sym3: true
作者: RUNOOB
```

Symbol 在 Dart 编译后通常会被压缩（minified），所以不要依赖 Symbol("runoob").toString() 的结果来做逻辑判断。Symbol 的正确用法是通过 dart:mirrors 库进行反射操作。


## Rune 与 Unicode

Rune 是 Dart 中表示 Unicode 码点的类型。

在 Dart 中，字符串是 UTF-16 编码的序列。

对于基本多语言平面（BMP）之外的字符（如 emoji），需要使用 Rune 来处理。


## 实例

```text
字符: RUNOOB
码点列表: [82, 85, 78, 79, 79, 66]
R -> U+0052
U -> U+0055
N -> U+004E
O -> U+004F
O -> U+004F
B -> U+0042
心形: ❤
笑脸: 😀
笑脸码点: [U+1F600]
```

大部分日常开发中你不需要直接操作 Rune，字符串本身已经能很好地处理 Unicode。

Rune 主要在需要精确操作字符码点时使用，比如文本编辑器、字体渲染等底层场景。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Dart 枚举与符号` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
