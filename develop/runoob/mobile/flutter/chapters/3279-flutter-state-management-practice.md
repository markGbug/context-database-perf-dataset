# Flutter：Flutter 状态管理

- 来源：[Flutter 状态管理](https://www.runoob.com/flutter/flutter-state-management.html)
- 分类：移动开发
- 技术：Flutter
- 笔记类型：练习笔记
- 章节序号：3279

## 本章内容

状态管理是 Flutter 开发中的核心概念。

本节将介绍 Flutter 内置的状态管理方式，包括 setState、Provider 和 ChangeNotifier。


## 什么是状态管理

状态管理是指管理应用中数据的变化和 UI 更新的机制。当数据发生变化时，UI 需要相应更新，这就是状态管理要解决的问题。


## 本地状态 - setState

对于简单的本地状态，使用 StatefulWidget 和 setState 就足够了。


## 实例：计数器示例


## Provider 状态管理

Provider 是 Flutter 官方推荐的状态管理方案之一，适合管理跨组件共享的状态。


### 安装 Provider

在 pubspec.yaml 中添加依赖：

```text
dependencies:
  provider: ^6.0.0
```


### ChangeNotifier 模式


## 实例：Provider + ChangeNotifier


### 多 Provider 组合


## 实例：多 Provider 使用


## 状态提升 - Lifting State Up

当多个子组件需要共享状态时，可以将状态提升到最近的公共父组件。


## 实例：状态提升

状态管理的选择取决于应用规模：简单应用使用 setState，中型应用使用 Provider，复杂应用可以考虑 Riverpod、BLoC 或 GetX 等方案。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Flutter 状态管理` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
