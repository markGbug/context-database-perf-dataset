# Dart：Dart 异常处理

- 来源：[Dart 异常处理](https://www.runoob.com/dart/dart-exception-handling.html)
- 分类：编程语言
- 技术：Dart
- 笔记类型：学习笔记
- 章节序号：3650

## 本章内容

异常是程序运行时发生的错误事件。

良好的异常处理能让程序在遇到错误时优雅地降级，而不是直接崩溃。

本章介绍 Dart 中的 try/catch/finally、throw 抛出异常、on 捕获指定类型以及 rethrow 重新抛出。


## try / catch / finally 基础

try 块中放置可能抛出异常的代码，catch 块捕获并处理异常，finally 块无论是否异常都会执行。


## 实例

```text
捕获到异常: IntegerDivisionByZeroException
RUNOOB 异常: RangeError (index): Invalid value: Not in inclusive range 0..2: 10
堆栈信息:
#0      List.[] (dart:core-patch/growable_array.dart:264)
#1      main (file:///...)
...
尝试执行操作...
出错: IntegerDivisionByZeroException
清理资源完成（finally 总是执行）
```

finally 块最适合用于资源清理，比如关闭文件、释放数据库连接等。即使 try 或 catch 中有 return 语句，finally 仍然会执行。


## throw 抛出异常

使用 throw 关键字可以主动抛出异常。

Dart 允许抛出任何对象作为异常（不仅仅是 Exception 的子类），但最佳实践是抛出 Exception 或 Error 的子类。


## 实例

```text
InvalidAgeException: 无效的年龄: -5（年龄必须在 0 到 150 之间）
InvalidAgeException: 无效的年龄: 200（年龄必须在 0 到 150 之间）
年龄 25 验证通过
RUNOOB 错误: Invalid argument(s): 除数不能为 0
```

Exception 和 Error 的区别：Exception 是可预期的、程序可以处理的错误（如网络超时、文件不存在）；Error 是不可预期的、通常表示程序 bug 的问题（如类型错误、空指针）。你的代码应该捕获 Exception 而非 Error。


## on 捕获指定类型

on 关键字可以按异常类型进行捕获，让错误处理更精细。


## 实例

```text
RUNOOB 错误: 不能除以零
操作结束

--- 测试不同的操作 ---
divide_by_zero -> 除零异常
parse_error -> 格式异常
out_of_range -> 范围异常
```

on 和 catch 的排列顺序很重要：Dart 会按照从上到下的顺序匹配异常类型。更具体的异常类型应该放在前面，更通用的放在后面。如果把 catch (e) 放在最前面，后面的 on 就永远不会被执行。


## rethrow 重新抛出

有时你需要在捕获异常后做一些处理（如记录日志），然后让异常继续向上传播。

rethrow 关键字用于重新抛出当前捕获的异常，保留原始堆栈信息。


## 实例

```text
控制器层: 处理请求
  服务层: 调用数据库操作
  正在连接数据库...
  [日志] 数据库操作异常: Exception: RUNOOB 数据库连接失败
控制器层捕获到异常
错误信息: Exception: RUNOOB 数据库连接失败
给用户返回: "服务暂时不可用，请稍后重试"

--- rethrow vs throw e 的区别 ---
使用 throw e（丢失原始堆栈）...
捕获: FormatException: 原始异常
堆栈指向这里（不是原始位置）:
...
```

rethrow 和 throw e 的区别很关键：rethrow 保留原始异常的全部堆栈信息，方便定位问题根源；throw e 会重置堆栈，从当前位置重新开始。在记录日志后需要继续传播异常时，请使用 rethrow。


## 异常处理的最佳实践


## 复习重点

- 能说明 `Dart 异常处理` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
