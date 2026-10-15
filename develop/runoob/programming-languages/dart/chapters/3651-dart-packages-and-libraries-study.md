# Dart：Dart 包与库管理

- 来源：[Dart 包与库管理](https://www.runoob.com/dart/dart-packages-and-libraries.html)
- 分类：编程语言
- 技术：Dart
- 笔记类型：学习笔记
- 章节序号：3651

## 本章内容

当项目规模增长时，将代码拆分为多个文件和模块是必不可少的。

本章介绍 Dart 的包管理系统 pub、依赖配置文件 pubspec.yaml、import/export 语法以及如何创建自定义库。


## pubspec.yaml 配置

pubspec.yaml 是每个 Dart 项目的核心配置文件，声明了项目的元数据和依赖。

一个典型的 pubspec.yaml 文件结构如下：


## 实例

版本号的写法说明：

^ 符号（caret）是 Dart 的默认版本约束方式。^1.1.0 等价于 >=1.1.0 <2.0.0。这意味着可以自动升级次版本和补丁版本，但不能升级主版本（主版本升级可能包含破坏性变更）。


### 安装依赖

```text
$ dart pub get           # 安装依赖
$ dart pub upgrade       # 升级依赖到最新兼容版本
$ dart pub outdated      # 查看哪些依赖有更新
```


## pub.dev 查找依赖

pub.dev 是 Dart 和 Flutter 的官方包仓库，类似于 npm（JavaScript）或 PyPI（Python）。

你可以在 https://pub.dev 上搜索和浏览数以万计的 Dart 包。

常用的第三方包举例：


## 实例

添加 http 包并使用：


## import 导入语法

import 用于在一个 Dart 文件中引入其他库的代码。

Dart 支持多种导入方式，每种适用于不同的场景。


### 导入 Dart 内置库


## 实例

```text
圆周率: 3.141592653589793
2 的 10 次方: 1024
解析后的 JSON: {name: runoob, age: 10}
用户名: runoob
```


### 导入第三方包


## 实例


### 导入本地文件


## 实例


### import 的修饰符


## 实例

各种导入修饰符的实际用法：

```text
sin(0) = 0.0
cos(0) = 1.0
π = 3.141592653589793
sqrt(16) = 4.0
max(3, 7) = 7
```

show 和 hide 不只是为了便利——它们也是代码质量的工具。使用 show 可以让依赖关系更清晰：你能一眼看出这个文件使用了库中的哪些符号。


## export 导出语法

export 用于将其他库的公开 API 重新暴露出去，主要用于创建聚合库。

假设你有以下文件结构：

```text
lib/
├── my_package.dart          # 入口文件（聚合导出）
├── src/
│   ├── models/
│   │   └── user.dart        # User 类
│   ├── services/
│   │   └── api_service.dart # API 服务
│   └── utils/
│       └── helpers.dart     # 工具函数
```


## 实例

使用 export 创建聚合库入口：

这样使用者只需要导入一个文件：


## 实例


## 自定义库的创建

创建一个自定义库不需要特殊语法——每个 Dart 文件就是一个库。

但你可以使用 library 关键字明确声明库名，以及使用 part/part of 拆分大型库。


### 使用 library 声明库名


## 实例


### 使用 part 拆分大型库

当一个库的代码太长时，可以用 part 将其拆分为多个物理文件，但它们在逻辑上仍然属于同一个库。


## 实例

主文件声明 part：


## 实例

part 文件声明 part of：

part/part of 在现代 Dart 开发中不常用，多数团队更倾向于使用 import/export 来组织代码。part 的缺点是 part 文件之间共享所有私有成员，破坏了封装性。除非有明确需求，否则推荐使用 import/export。


## Dart 核心库速览

dart:core 是自动导入的，你不需要写 import 'dart:core' 就能使用 int、String、List、Map 等基础类型。


## 复习重点

- 能说明 `Dart 包与库管理` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
