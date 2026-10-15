# TypeScript：TypeScript 基本结构

- 来源：[TypeScript 基本结构](https://www.runoob.com/typescript/typescript-basic-structure.html)
- 分类：前端开发
- 技术：TypeScript
- 笔记类型：练习笔记
- 章节序号：3124

## 本章内容

TypeScript 程序的基本结构可以分为几个部分，每个部分都有特定的作用。

以下是 TypeScript 程序的常见组成部分：

- 声明部分：包括类型声明、接口声明等。
- 变量声明：包括 let, const 和 var 的使用。
- 函数声明：包括普通函数和箭头函数。
- 类声明：用于定义类及其成员。
- 接口与类型别名：描述类型的结构。
- 模块化：通过 import 和 export 组织代码。
- 类型断言：强制类型转换。
- 泛型：使代码具备更多的复用性。
- 注释：增加代码的可读性。
- 类型推断：自动推断类型。
- 类型守卫：缩小类型范围。
- 异步编程：支持 async/await。
- 错误处理：通过 try/catch 进行错误捕捉。

以上几个部分共同构成了 TypeScript 程序的基本结构，并为开发者提供了强大的类型检查、代码结构和可维护性。


## 1. 声明部分（Declarations）

类型声明：TypeScript 是一种静态类型的语言，可以通过类型声明来定义变量、函数、类等的类型。类型声明可以帮助代码更具可维护性和可读性。


## 实例

接口声明：用于定义对象的结构，包括对象的属性和方法。


## 实例


## 2. 变量声明（Variable Declarations）

在 TypeScript 中，可以使用 let, const, 和 var 来声明变量。推荐使用 let 和 const，var 用法不再推荐。


## 实例


## 3. 函数声明（Function Declarations）

函数声明：TypeScript 允许声明带有类型注解的函数，包括参数类型和返回值类型。


## 实例

箭头函数：TypeScript 同样支持 ES6 的箭头函数，使用简洁的语法来声明函数。


## 实例


## 4. 类声明（Class Declarations）

TypeScript 提供对面向对象编程的支持，允许定义类和类的方法、属性。


## 实例


## 5. 接口与类型别名（Interfaces & Type Aliases）

接口（Interface）：用于描述对象的形状，接口可以继承和扩展。


## 实例

类型别名（Type Alias）：允许为对象类型、联合类型、交叉类型等定义别名。


## 实例


## 6. 模块和导入导出（Modules & Imports/Exports）

TypeScript 支持模块化编程，可以使用 import 和 export 来组织代码。

导出：


## 实例

导入：


## 实例


## 7. 类型断言（Type Assertions）

在某些情况下，TypeScript 无法推断出一个变量的准确类型，开发者可以使用类型断言来强制指定类型。


## 实例


## 8. 泛型（Generics）

泛型允许在定义函数、接口或类时不指定具体类型，而是使用占位符，让用户在使用时传入具体类型。泛型能够增加代码的复用性和类型安全性。


## 实例


## 9. 注释（Comments）

注释在 TypeScript 程序中用于解释代码的作用、思路等，增加代码的可读性。

单行注释：


## 实例

多行注释：


## 实例


## 10. 类型推断（Type Inference）

TypeScript 在某些情况下会自动推断变量的类型。例如，在声明变量并赋值时，TypeScript 会推断出该变量的类型。


## 后续章节

- 实例
- 11. 类型守卫（Type Guards）
- 实例
- 12. 异步编程（Asynchronous Programming）
- 实例
- 13. 错误处理（Error Handling）
- 实例

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `TypeScript 基本结构` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
