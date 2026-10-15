# TypeScript：TypeScript 特殊类型：never、void、unknown、any

- 来源：[TypeScript 特殊类型](https://www.runoob.com/typescript/ts-special-types.html)
- 分类：前端开发
- 技术：TypeScript
- 笔记类型：练习笔记
- 章节序号：3148

## 本章内容

TypeScript 有四个特殊的类型：never、void、unknown 和 any。

它们在类型系统中扮演重要角色，理解它们的区别对于编写类型安全的代码至关重要。


## 为什么需要特殊类型

TypeScript 的类型系统非常强大，除了常规的类型外，还提供了四个特殊类型来处理特定的场景。

理解这四种特殊类型的区别，能够帮助我们编写更安全、更准确的类型代码。

概念说明：never、void、unknown、any 是 TypeScript 的特殊类型，它们各自有不同的含义和使用场景。


## never 类型

never 表示永不返回的类型。通常用于抛出异常或无限循环的函数。


## 实例

运行结果：

```text
never 赋值给 number: undefined
```

重要：never 是所有类型的子类型，这意味着 never 可以赋值给任何类型，但任何类型都不能赋值给 never（除了 never 本身）。


## void 类型

void 表示没有返回值，通常用于声明没有 return 语句的函数。


## 实例

运行结果：

```text
日志: Hello
void 变量: undefined
```

说明：void 实际上和 undefined 很相似，主要用于函数的返回类型声明，表示这个函数没有返回值。


## unknown 类型

unknown 是类型安全的 any。使用 unknown 时，必须先进行类型检查才能使用。


## 实例

运行结果：

```text
字符串长度: 5
```

安全：unknown 强制要求在使用前进行类型检查，这保护了类型安全。处理未知来源的数据时，应该使用 unknown 而不是 any。


## any 类型

any 完全绕过类型检查，可以赋值为任意类型。这是 TypeScript 中最不安全的类型。


## 实例

警告：any 类型会完全绕过 TypeScript 的类型检查，应该尽量避免使用。在必须使用的情况下，要确保值的类型是正确的。


## 对比 any vs unknown

any 和 unknown 都可以接受任意类型，但安全性完全不同。

建议：处理未知类型的数据时，优先使用 unknown 而不是 any，这样能强制进行类型检查。


## never vs void

never 和 void 都用于函数返回类型，但含义完全不同。

关键区别：never 表示函数永远不会正常返回（要么抛异常，要么死循环）；void 表示函数正常执行完毕，但没有返回值。


## 实际应用：Exhaustive Check

never 类型的一个重要用途是进行穷举检查，确保所有可能的情况都被处理。


## 实例

运行结果：

```text
圆形面积: 78.54
正方形面积: 16
```

Exhaustive Check：这种模式确保当添加新的类型分支时，如果忘记在 switch 中处理，编译器会报错，因为新增的类型无法赋值给 never。


## 注意事项

- never 是子类型：never 可以赋值给任何类型，但任何类型都不能赋值给 never
- void vs undefined：在 JavaScript 中，void 和 undefined 基本等同
- unknown 需要检查：使用 unknown 类型的值前，必须进行类型检查
- 避免 any：尽量不要使用 any，优先使用 unknown

最佳实践：从高到低的类型安全程度：never > void > unknown > any。尽量使用更安全的类型。


## 总结

理解这四种特殊类型对于编写高质量的 TypeScript 代码非常重要。

- never：永不返回，用于 exhaustive check，是所有类型的子类型
- void：无返回值，用于普通没有返回值的函数
- unknown：安全的任意类型，使用前必须进行类型检查
- any：绕过所有类型检查，应该尽量避免使用

建议：编写代码时，优先使用更严格的类型。处理未知数据使用 unknown，函数无返回值使用 void，需要穷举检查时使用 never。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `TypeScript 特殊类型` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
