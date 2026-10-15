# TypeScript：TypeScript 教程

- 来源：[TypeScript 教程](https://www.runoob.com/typescript/ts-tutorial.html)
- 分类：前端开发
- 技术：TypeScript
- 笔记类型：学习笔记
- 章节序号：3118

## 本章内容

TypeScript 是 JavaScript 的一个超集，支持 ECMAScript 6 标准（ES6 教程）。

TypeScript 由微软开发的自由和开源的编程语言，在 JavaScript 的基础上增加了静态类型检查的超集。

TypeScript 设计目标是开发大型应用，它可以编译成纯 JavaScript，编译出来的 JavaScript 可以运行在任何浏览器上。


## 为什么选择 TypeScript

TypeScript 是由 Microsoft 开发的开源编程语言，它是 JavaScript 的超集。

TypeScript 通过添加可选的静态类型、接口、枚举等特性，大大增强了 JavaScript 的开发体验。


### TypeScript 的主要优势

- 静态类型检查：在编译时发现类型错误，减少运行时错误
- 强大的 IDE 支持：智能代码补全、导航和重构
- 更好的代码可读性：类型本身就是最好的文档
- 现代 JavaScript 特性：支持 ES6+ 语法，如箭头函数、模块、类等
- 渐进式迁移：可以逐步将现有 JavaScript 项目迁移到 TypeScript


### TypeScript 工作原理

TypeScript 不能直接在浏览器中运行，它需要先编译为 JavaScript。这个编译过程会检查类型错误，并将 TypeScript 特有的语法转换为纯 JavaScript。

TypeScript 编译器 (tsc) 在编译过程中进行类型检查，如果发现类型错误会报错并阻止编译。编译成功后生成纯 JavaScript 代码，可以在任何浏览器或 Node.js 环境中运行。


## 语言特性

TypeScript 是对 JavaScript 的类型增强扩展，在保持原有语法兼容的基础上，引入了更强的类型系统和工程能力。


### 核心增强能力（TypeScript 独有）


### 来自 ES2015 的语法支持（向下兼容）

TypeScript 同时支持并向下编译 ECMAScript 2015 的核心特性：


## JavaScript 与 TypeScript 的区别

TypeScript 是 JavaScript 的超集，扩展了 JavaScript 的语法，因此现有的 JavaScript 代码可与 TypeScript 一起工作无需任何修改，TypeScript 通过类型注解提供编译时的静态类型检查。

TypeScript 可处理已有的 JavaScript 代码，并只对其中的 TypeScript 代码进行编译。


## 第一个 TypeScript 实例

以下实例我们使用 TypeScript 来输出 Hello World!:


## 实例

```javascript
const hello : string = "Hello World!"
console.log(hello)
```


## 复习重点

- 能说明 `TypeScript 教程` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
