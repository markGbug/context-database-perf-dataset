# Flutter：Flutter 本地存储

- 来源：[Flutter 本地存储](https://www.runoob.com/flutter/flutter-storage.html)
- 分类：移动开发
- 技术：Flutter
- 笔记类型：练习笔记
- 章节序号：3285

## 本章内容

本节将介绍 Flutter 中的本地存储方案，包括 SharedPreferences、文件存储和 SQLite 数据库。


## SharedPreferences - 轻量级存储

SharedPreferences 适合存储简单的键值对数据。


### 添加依赖

```text
dependencies:
  shared_preferences: ^2.0.0
```


## 实例：SharedPreferences 使用


## 文件存储

使用 path_provider 获取应用文档目录进行文件存储。


### 添加依赖

```text
dependencies:
  path_provider: ^2.0.0
```


## 实例：文件读写


## SQLite 数据库

使用 sqflite 进行 SQLite 数据库操作。


### 添加依赖

```text
dependencies:
  sqflite: ^2.0.0
  path: ^1.8.0
```


## 实例：SQLite 基本操作

数据存储方案选择：简单键值用 SharedPreferences，复杂结构用 SQLite，文件存储适合大文件。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Flutter 本地存储` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
