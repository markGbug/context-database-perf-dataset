# TypeScript：TypeScript Symbol

- 来源：[TypeScript Symbol](https://www.runoob.com/typescript/ts-symbol.html)
- 分类：前端开发
- 技术：TypeScript
- 笔记类型：学习笔记
- 章节序号：3147

## 本章内容

Symbol 是 ES6 引入的原始数据类型，表示唯一的标识符。

在 TypeScript 中，Symbol 可以用作对象的属性键，确保属性的唯一性。

这在需要创建私有属性、避免属性名冲突等场景非常有用。


## 为什么需要 Symbol

在 JavaScript 中，对象的属性名都是字符串，有时可能会发生冲突。

Symbol 提供了创建唯一标识符的方式，每次调用 Symbol() 都会创建一个新的、唯一的值。

这在需要创建私有属性、定义唯一常量、实现迭代器等场景非常有用。

概念说明：Symbol 是 JavaScript 的原始数据类型之一，通过 Symbol() 函数创建。每个 Symbol 值都是唯一的，即使描述相同也不相等。


## 创建 Symbol

使用 Symbol() 函数创建唯一的 Symbol 值。


## 实例

运行结果：

```text
sym1 === sym2: false
sym1: Symbol(description)
```

唯一性：这是 Symbol 最重要的特性，每次调用 Symbol() 都会创建一个新值，与任何其他值都不相等。


## Symbol 作为对象属性

Symbol 可以用作对象的属性键，创建唯一的属性名。


## 实例

运行结果：

```text
普通属性: Alice
Symbol 属性: secret value
对象: {"name":"Alice"}
```

隐私：Symbol 属性不会出现在 JSON 序列化中，也不会被 for...in 遍历到，可以用来创建"私有"属性。


## 全局 Symbol 注册表

使用 Symbol.for() 访问全局注册表中的 Symbol，相同 key 会返回相同的 Symbol。


## 实例

运行结果：

```text
全局 Symbol 相等: true
Symbol key: global
```

区别：Symbol() 每次创建新的值，Symbol.for() 在全局注册表中查找或创建。


## 内置 Symbol

JavaScript 定义了一些内置的 Symbol 值，用于自定义语言行为。


## 实例

运行结果：

```text
第一个元素: 1
第二个元素: 2
对象类型: [object MyObject]
```

重要：内置 Symbol 用于自定义语言行为，如迭代器、类型转换等，是 JavaScript 高级特性的基础。


## Symbol 类型注解

在 TypeScript 中使用 Symbol 类型进行类型注解。


## 实例

类型：TypeScript 中使用 symbol 类型注解 Symbol 值。


## 注意事项

- 唯一性：每次 Symbol() 调用的值都不同
- 不可枚举：Symbol 属性不会出现在 for...in 循环中
- JSON 忽略：Symbol 属性不会被 JSON 序列化
- 全局注册：Symbol.for() 在全局注册表中共享

应用场景：Symbol 常用于创建对象的私有属性、定义唯一常量、避免属性名冲突等。


## 总结

Symbol 是 TypeScript 中重要的原始类型。

- 唯一性：每次创建的 Symbol 都不相等
- 属性键：可用作对象的唯一属性键
- 全局注册：Symbol.for() 创建/获取全局 Symbol
- 内置 Symbol：Symbol.iterator、Symbol.toStringTag 等
- 类型注解：使用 symbol 类型

建议：在需要创建唯一标识符、避免属性名冲突、或需要"私有"属性时，使用 Symbol。


## 复习重点

- 能说明 `TypeScript Symbol` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
