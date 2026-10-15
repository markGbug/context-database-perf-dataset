# Flutter：Flutter Widget 基础

- 来源：[Flutter Widget 基础](https://www.runoob.com/flutter/flutter-widget-basics.html)
- 分类：移动开发
- 技术：Flutter
- 笔记类型：学习笔记
- 章节序号：3273

## 本章内容

Widget 是 Flutter UI 的基本构建块。

在 Flutter 中，一切皆为 Widget，从简单的文本到复杂的页面布局都是由 Widget 组合而成的。


## 什么是 Widget？

Widget 是描述 UI 外观和行为的 Dart 类。每个 Flutter 应用本质上就是由 Widget 组成的树形结构，称为 Widget 树。


## 实例：最简单的 Widget 示例


## StatelessWidget - 无状态组件

StatelessWidget 是不可变的 Widget，一旦创建，其属性就不能更改。适用于显示静态内容的场景，如文本、图片、图标等。


### 基本结构


## 实例：StatelessWidget 示例


### 适用场景

- 静态文本展示
- 图片显示
- 图标展示
- 不随时间变化的布局


## StatefulWidget - 有状态组件

StatefulWidget 是可变的 Widget，可以随着内部数据变化而更新 UI。适用于需要响应用户交互或数据变化的场景。


### 基本结构


## 实例：StatefulWidget 示例


### setState 方法

在 StatefulWidget 中，如果状态发生变化，必须调用 setState 方法来通知 Flutter 重新构建 UI。

如果修改了状态但没有调用 setState，UI 不会更新。这是因为 Flutter 通过 setState 来判断是否需要重新构建 Widget。


### 适用场景

- 计数器、计时器等动态数据
- 表单输入
- 列表项的增删改
- 用户交互响应


## build 方法

每个 Widget 都必须实现 build 方法，该方法返回 Widget 树的一部分。


### 基本规则


## 实例：build 方法示例


## 常用基础 Widget


### Text - 文本显示


## 实例：Text Widget


### Icon - 图标


## 实例：Icon Widget


### Image - 图片


## 实例：Image Widget


### Button - 按钮


## 实例：按钮 Widget


## Widget 组合

Flutter 的强大之处在于可以组合 Widget。通过嵌套，一个简单的 Widget 可以构建出复杂的 UI。


## 后续章节

- 实例：组合 Widget

## 复习重点

- 能说明 `Flutter Widget 基础` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
