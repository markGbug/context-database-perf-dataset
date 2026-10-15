# Flutter：Flutter StatelessWidget vs StatefulWidget 深入理解

- 来源：[Flutter StatelessWidget](https://www.runoob.com/flutter/flutter-stateless-stateful.html)
- 分类：移动开发
- 技术：Flutter
- 笔记类型：练习笔记
- 章节序号：3274

## 本章内容

理解 StatelessWidget 和 StatefulWidget 的区别是 Flutter 开发的基础。

本节将深入分析这两种 Widget 的使用场景和内部工作机制。


## 核心区别

Flutter 中有两种主要类型的 Widget，它们的根本区别在于是否能持有可变状态。


## StatelessWidget 详解

StatelessWidget 适合用于不随时间变化的内容。一旦创建，其所有属性都是 final 的，不可修改。


### 使用场景

- 显示静态文本、图片、图标
- 展示数据列表（数据源来自父 Widget）
- 不包含用户交互的布局容器
- 表单中的只读展示部分


## 实例：StatelessWidget 完整示例


## StatefulWidget 详解

StatefulWidget 适合用于需要响应用户交互或数据变化的场景。它由两部分组成：Widget 本身（不可变）和 State 对象（可变）。


### 使用场景

- 计数器、计时器等动态数据
- 表单输入
- 动画控制
- 网络请求状态展示
- 用户交互响应


### State 对象生命周期


## 实例：StatefulWidget 完整示例


## setState 的正确使用

在 StatefulWidget 中，必须通过 setState 来通知 Flutter 状态已更改。


### 正确用法


## 实例：正确的 setState 用法


### 错误用法


## 实例：错误的 setState 用法

setState 会在下一次帧绘制时触发 build 方法的重新调用。

频繁调用 setState 或在 build 方法中调用 setState 都可能导致性能问题。


## 如何选择

在开发时，应该根据实际需求选择合适的 Widget 类型：


### 选择 StatelessWidget 当

- Widget 的外观不依赖于任何可变状态
- 所有需要的数据都通过构造函数从父 Widget 传入
- Widget 不需要响应用户交互
- 追求最佳性能


### 选择 StatefulWidget 当

- Widget 需要维护内部状态
- 需要响应用户输入（点击、滑动等）
- 需要响应数据变化（如网络请求返回）
- 需要控制动画


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Flutter StatelessWidget` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
