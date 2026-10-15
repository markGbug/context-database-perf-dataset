# Flutter：Flutter 本地存储

- 来源：[Flutter 本地存储](https://www.runoob.com/flutter/flutter-storage.html)
- 分类：移动开发
- 技术：Flutter
- 笔记类型：学习笔记
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


## 复习重点

- 能说明 `Flutter 本地存储` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
