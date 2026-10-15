# TypeScript：TypeScript 简介

- 来源：[TypeScript 简介](https://www.runoob.com/typescript/ts-intro.html)
- 分类：前端开发
- 技术：TypeScript
- 笔记类型：练习笔记
- 章节序号：3119

## 本章内容

TypeScript 是由微软开发并开源的编程语言，它是 JavaScript 的超集，在完全兼容 JavaScript 语法的基础上，增加了可选的静态类型系统和基于类的面向对象编程能力。

TypeScript 代码最终会被编译为纯 JavaScript，可以运行在任何支持 JavaScript 的环境中，包括浏览器、Node.js 和移动端。


## 为什么需要 TypeScript

JavaScript 是一门动态类型语言，变量的类型在运行时才能确定。

这种灵活性在小型项目中表现出色，但随着项目规模扩大，问题逐渐暴露：

TypeScript 的本质目标不是取代 JavaScript，而是让大规模 JavaScript 工程变得可管理、可维护。它是 JavaScript 的"安全网"，而不是竞争对手。

看一个最直观的例子：


## 实例


## 实例


## TypeScript 与 JavaScript 的关系

TypeScript 和 JavaScript 之间的关系，可以用一句话概括：TypeScript 是 JavaScript 的超集，即所有合法的 JavaScript 代码，同时也是合法的 TypeScript 代码。

集合关系示意

JavaScript（所有 JS 代码） ⊂ TypeScript（JS + 类型系统 + 新特性） ⊂ 编译产物（标准 JavaScript，可在任意环境运行）

两者的核心差异对比：

TypeScript 支持"渐进式采用"：你不必一次性重写整个项目。可以先把 .js 改为 .ts，逐步为关键模块添加类型，现有代码照常运行。


## 核心特性

TypeScript 在 JavaScript 的基础上引入了一套完整的类型系统，以下是最常用的核心特性。


### 基础类型注解

在变量、函数参数、返回值后用冒号声明类型，这是 TypeScript 最基础的写法。


## 实例


### 接口（Interface）

接口用来描述对象的"形状"（Shape），定义对象应该具备哪些属性和方法。


## 实例


### 类型别名（Type Alias）

类型别名用 type 关键字创建，可以为任何类型定义别名，包括联合类型、交叉类型等复杂结构。


## 实例


### 泛型（Generics）

泛型允许编写可复用的组件，同时保持类型安全。可以把泛型理解为"类型的变量"——使用时再传入具体类型。


## 实例


### 枚举（Enum）

枚举用于定义一组命名常量，使代码中的"魔法数字"或"魔法字符串"变得有意义。


## 实例


### 类型推断

TypeScript 不需要为每个变量都手动标注类型，编译器会根据赋值自动推断。


## 实例

一个实用建议：函数的参数通常需要显式标注类型（因为调用方无法从参数值推断类型），而函数体内的局部变量和返回值大多数情况下依赖推断即可，不必全部手动标注。


### 类与访问修饰符

TypeScript 完整支持 ES6 的类语法，并新增了 public、private、protected、readonly 四种访问修饰符。


## 实例


### 装饰器（Decorator）

装饰器是一种元编程语法，用于在类、方法、属性上附加额外行为，常见于 Angular、NestJS 等框架。

TypeScript 5.0 已将装饰器实现为正式标准（Stage 3 提案），不再需要开启 experimentalDecorators 标志。


## 实例


## 应用领域

TypeScript 凭借其对 JavaScript 的完全兼容性，几乎可以用在所有 JavaScript 能运行的地方，并且在大型项目中带来额外收益。


### 前端 Web 开发

这是 TypeScript 使用最广泛的场景。三大主流前端框架均对 TypeScript 提供一级支持：


### 后端 Node.js 开发

TypeScript 在 Node.js 后端开发中同样普及。NestJS 是目前最流行的 TypeScript 后端框架，采用与 Angular 相近的模块化架构，内置依赖注入和装饰器支持。

此外，Deno 运行时从第一天起就原生支持 TypeScript，无需任何配置即可直接运行 .ts 文件。Bun 同样内置 TypeScript 支持。


## 后续章节

- 命令行工具与脚本
- 移动端与跨平台
- 游戏开发与图形
- 发展历史
- 起源（2010 - 2012）
- 早期版本（2013 - 2015）
- 高速成长（2016 - 2019）
- 成熟与普及（2020 - 2022）
- 现代阶段（2023 至今）
- 未来展望：用 Go 重写编译器
- TypeScript 与其他强类型语言的对比
- TypeScript 的局限性

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `TypeScript 简介` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
