# Dart：Dart 单元测试

- 来源：[Dart 单元测试](https://www.runoob.com/dart/dart-unit-testing.html)
- 分类：编程语言
- 技术：Dart
- 笔记类型：练习笔记
- 章节序号：3656

## 本章内容

单元测试是保证代码质量的基础手段。

它验证每个最小功能单元（通常是函数或方法）的行为是否符合预期。

本章介绍 Dart 的 test 包使用、test() 测试用例编写、expect 断言以及 group() 分组测试。


## test 包的安装与配置

Dart 官方提供了 test 包来编写和运行测试。

首先在 pubspec.yaml 中添加依赖：

```text
# 文件路径：pubspec.yaml
dev_dependencies:
  test: ^1.24.0
```

然后运行以下命令安装：

```text
$ dart pub get
```

测试文件通常放在项目的 test/ 目录下，文件名以 _test.dart 结尾。

一个典型的项目结构：

```text
my_project/
├── lib/
│   └── calculator.dart       # 被测试的代码
├── test/
│   └── calculator_test.dart  # 测试文件
└── pubspec.yaml
```


## 编写 test() 测试用例

test() 函数是编写测试用例的基本单元。

它接收两个参数：测试描述（字符串）和测试函数体。


## 实例

被测试的代码（lib/calculator.dart）：


## 实例

测试文件（test/calculator_test.dart）：

运行测试：

```text
$ dart test
```

```text
00:00 +6: All tests passed!
```


## expect 断言

expect() 是测试中最核心的函数，它验证实际值是否满足某个条件。

基本语法：expect(actual, matcher)。


### 常用 Matcher


## 实例

各种 Matcher 的实际应用：

```text
00:00 +1: All tests passed!
```


### 测试异常


## 实例

```text
00:00 +2: All tests passed!
```

测试异常时，需要将可能抛异常的代码包装在匿名函数中（() => code），而不是直接调用。如果直接写 expect(divide(10, 0), throwsException)，divide 会立即抛出异常，expect 根本没机会执行。


## 分组测试 group()

group() 用于将相关的测试用例组织在一起，让测试结构更清晰。


## 实例

```text
00:00 +12: All tests passed!
```

group() 可以嵌套，创建层次化的测试结构。

这让测试报告更易读，也方便快速定位失败的测试。

一个好的分组策略是按"被测试的模块/类/方法"来组织。这样当某个测试失败时，你能立即知道是哪个功能出了问题。


### setUp 和 tearDown

setUp 在每个 test 之前运行，tearDown 在每个 test 之后运行。

它们用于准备测试环境和清理资源。


## 实例

```text
  数据库已连接
  [setUp] 准备测试环境
  数据库已断开
  [tearDown] 清理测试环境
  数据库已连接
  [setUp] 准备测试环境
  数据库已断开
  [tearDown] 清理测试环境
  数据库已连接
  [setUp] 准备测试环境
  数据库已断开
  [tearDown] 清理测试环境
00:00 +3: All tests passed!
```

注意输出中 setUp 和 tearDown 的执行顺序——每个 test 前后都会执行一次。

setUp 和 tearDown 确保每个测试从一个干净的状态开始，不受其他测试的影响。这是测试独立性的关键保证。


## 异步测试

Dart test 包原生支持异步测试。

测试函数可以返回 Future，框架会自动等待 Future 完成。


## 实例

```text
00:00 +4: All tests passed!
```


## 运行测试的常用命令


## 测试最佳实践

测试不是负担，而是保险。你写的测试越多，重构时就越有信心。当一个测试失败时，你不需要猜是哪里出了问题——测试会精确地告诉你。


## 本章小结

本章介绍了 Dart 单元测试的完整流程：test 包的安装、test() 测试用例的编写、expect 断言的使用、group() 分组组织、setUp/tearDown 环境管理以及异步测试。

单元测试是专业开发者的必修课，养成写测试的习惯会让你的代码质量持续提升。


## 全教程总结

恭喜你完成了 Dart 编程语言的入门学习！

让我们回顾一下这 21 章的学习路径：

掌握了这些内容，你已经具备了使用 Dart 进行日常开发的能力。

下一步可以深入学习 Flutter 框架，将 Dart 知识应用到移动端和 Web 端的 UI 开发中。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Dart 单元测试` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
