# Dart：Dart 简介

- 来源：[Dart 简介](https://www.runoob.com/dart/dart-intro.html)
- 分类：编程语言
- 技术：Dart
- 笔记类型：学习笔记
- 章节序号：3637

## 本章内容

Dart 是由 Google 开发的一种现代化编程语言，专为构建高性能、跨平台应用而设计。

本章带你了解 Dart 的起源、设计理念以及它在前端、移动端和服务端的广泛应用场景。


## Dart 的历史与设计目标

Dart 诞生于 2011 年，最初的目标是替代 JavaScript 成为浏览器的原生脚本语言。

虽然这个目标未能实现，但 Dart 在 2017 年迎来了关键转折点——Flutter 框架的发布让 Dart 重新进入开发者视野。

Dart 的设计目标非常明确：

Dart 2.0 在 2018 年发布，标志着语言走向成熟。Dart 3.0 在 2023 年发布，进一步加强了类型系统和模式匹配等特性。


## Dart 的应用场景

Dart 的应用场景非常广泛，覆盖了从移动端到服务端的全栈开发需求。


### 移动端开发（Flutter）

这是 Dart 目前最核心的应用场景。

通过 Flutter 框架，Dart 可以构建 iOS 和 Android 双平台的原生应用，一套代码同时运行。


### Web 开发

Dart 可以编译为 JavaScript，用于构建 Web 前端应用。

AngularDart 是 Google 维护的 Dart 版 Angular 框架，适合大型 Web 项目。


### 服务端开发

通过 dart:io 库和 Shelf 等框架，Dart 也能编写高性能的服务端应用。

Google 内部有多个服务端项目使用 Dart 编写。


### 命令行工具

Dart 可以编译为独立的可执行文件，非常适合编写跨平台的 CLI 工具。


## Dart 与 JavaScript 对比

Dart 和 JavaScript 都是面向对象的语言，但 Dart 在语言设计上更加严谨。

下面从几个维度对比两者的差异：

如果你有 JavaScript 基础，学习 Dart 会非常轻松——它们的异步语法（async/await）几乎完全相同。

但 Dart 的类型系统和空安全机制会让你在大型项目中更有安全感。


## 实例

同样的功能在两种语言中的写法对比：

```text
Hello, runoob!
Hello, stranger!
```


## Dart 与 Flutter 的关系

很多人第一次接触 Dart 是因为 Flutter。

实际上，Flutter 是 Dart 的"杀手级应用"，但 Dart 本身是一门独立的通用编程语言。

Flutter 选择 Dart 的原因有以下几点：

- JIT 编译支持热重载（Hot Reload），修改代码后亚秒级看到效果，极大提升开发效率
- AOT 编译生成原生机器码，应用启动快、运行流畅，无 JavaScript Bridge 的性能损耗
- Dart 的声明式 UI与 Flutter 的 Widget 树结构天然契合
- 统一技术栈：Google 同时维护语言和框架，版本兼容性好

学习 Flutter 之前，建议先掌握 Dart 基础。理解语言特性后，Flutter 的学习曲线会平滑很多。本教程就是为这个目标准备的。


## Dart 版本发展简史

本教程基于 Dart 3.x 版本编写，所有代码示例都在 Dart 3.0 及以上版本中验证通过。


## 复习重点

- 能说明 `Dart 简介` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
