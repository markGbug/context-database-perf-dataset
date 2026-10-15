# Dart：Dart 接口与 Mixin

- 来源：[Dart 接口与 Mixin](https://www.runoob.com/dart/dart-interfaces-and-mixins.html)
- 分类：编程语言
- 技术：Dart
- 笔记类型：练习笔记
- 章节序号：3647

## 本章内容

虽然 Dart 只支持单继承，但通过接口和 Mixin 可以灵活地实现多重代码复用。

本章介绍如何使用 implements 实现接口、mixin 的代码复用以及 with 关键字。


## implements 实现接口

在 Dart 中，每个类都隐式定义了一个接口。

使用 implements 关键字可以让一个类实现另一个类的接口，且可以实现多个。


## 实例

```text
--- 文档: Dart 教程 ---
这是一份 Dart 入门指南
--- RUNOOB 打印结束 ---
文档 "Dart 教程" 已保存到磁盘
```

implements 和 extends 的关键区别：extends 继承父类的所有实现（方法体），而 implements 只继承接口签名，你必须重新实现所有方法。此外，extends 只能继承一个类，implements 可以实现多个接口。


### extends vs implements 对比


## 多接口实现

Dart 可以实现多个接口，这是突破单继承限制的主要方式。


## 实例

```text
RUNOOB 鸭 在天空中飞翔
RUNOOB 鸭 在水面上游泳
RUNOOB 鸭 在陆地上摇摇晃晃地走
鸭子能飞吗? true
鸭子能游吗? true
鱼能飞吗? false
```


## Mixin 代码复用

Mixin 是一种在多个类之间复用代码的机制，它解决了"多个类需要共享相同方法但又不适合继承"的问题。

使用 mixin 关键字定义一个 Mixin，使用 with 关键字将其混入到类中。


## 实例

```text
[2026-06-12 10:30:00.000] 创建用户: runoob
创建时间: 2026-06-12
[2026-06-12 10:30:00.001] 创建订单: ORD-001
[ERROR 2026-06-12 10:30:00.001] 取消订单失败: ORD-001
```

UserService 和 OrderService 来自不同的业务领域，不适合用继承来共享 Logger。

通过 Mixin，它们都能获得日志功能，而且互不影响。

Mixin 不能有构造函数，也不能被实例化。它的定位很纯粹：提供可复用的方法，不涉及状态初始化。


### Mixin 的限制条件

Mixin 可以使用 on 关键字限制它只能被特定类型的类使用。


## 实例

```text
RUNOOB 小鸟 飞起来了！
小鸟的名字: RUNOOB 小鸟
```


### class、Mixin、extends、implements 的完整组合

Dart 中一个类可以同时使用 extends、with 和 implements：


## 实例

```text
呼吸...
跑步前进！
跳起来！
RUNOOB 选手A vs 选手B: A 胜
```

完整声明顺序：class 子类 extends 父类 with Mixin1, Mixin2 implements 接口1, 接口2


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Dart 接口与 Mixin` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
