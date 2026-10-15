# Flutter：Flutter 调试与 DevTools

- 来源：[Flutter DevTools](https://www.runoob.com/flutter/flutter-devtools.html)
- 分类：移动开发
- 技术：Flutter
- 笔记类型：练习笔记
- 章节序号：3287

## 本章内容

本节将介绍 Flutter 的调试工具和常用调试技巧。


## Flutter DevTools 简介

Flutter DevTools 是一套用于调试和分析 Flutter 应用的工具集。


### 启动 DevTools

```text
$ flutter run
```

在运行应用后，终端会显示 DevTools 的 URL，通常是 http://127.0.0.1:9100


### 常用命令


## print 和 debugPrint


## 实例：基本调试输出


## 断言 - assert

断言用于在开发时检查条件，仅在调试模式下生效。


## 断点调试

在 VS Code 或 Android Studio 中设置断点进行调试。


### VS Code 调试

- 在代码行号左侧点击设置断点
- 按 F5 或点击调试按钮启动调试
- 使用调试工具栏控制程序执行


### 常用断点命令


## Flutter Inspector

Flutter Inspector 是 DevTools 的一部分，用于可视化和检查 Widget 树。


### 主要功能

- Widget Tree: 查看 Widget 层级结构
- Layout Explorer: 检查布局约束
- Performance Overlay: 显示性能指标


## 常见问题调试


## 实例：调试 UI 不更新

调试时常用工具：print 输出日志、Inspector 检查 Widget 树、Timeline 分析性能。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Flutter DevTools` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
