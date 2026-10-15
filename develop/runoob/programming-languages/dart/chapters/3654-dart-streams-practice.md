# Dart：Dart Stream 流

- 来源：[Dart Stream 流](https://www.runoob.com/dart/dart-streams.html)
- 分类：编程语言
- 技术：Dart
- 笔记类型：练习笔记
- 章节序号：3654

## 本章内容

Stream（流）是 Dart 中处理连续异步事件序列的机制。

如果说 Future 是一次性的异步结果，那么 Stream 就是多次的、持续不断的异步数据流。

本章介绍 Stream 的概念、await for 监听、StreamController 创建以及单订阅与广播流的区别。


## Stream 与事件序列

Stream 就像一条传送带，数据会随着时间推移一个个到来。

你不需要一次性等待所有数据，而是来一个处理一个。

Stream 的典型应用场景：


## 实例

Stream 的基本使用——listen 监听：

```text
开始监听 Stream...
RUNOOB 收到数据: 1
RUNOOB 收到数据: 2
RUNOOB 收到数据: 3
RUNOOB 收到数据: 4
RUNOOB 收到数据: 5
已取消订阅
```

listen() 返回一个 StreamSubscription 对象，你可以用它来控制订阅：


## await for 监听

除了 listen() 回调方式，还可以使用 await for 循环来消费 Stream。

await for 让 Stream 的处理逻辑像普通的 for 循环一样清晰。


## 实例

```text
开始用 await for 消费 Stream...
RUNOOB 计数: 1
RUNOOB 计数: 2
RUNOOB 计数: 3
RUNOOB 计数: 4
RUNOOB 计数: 5
Stream 消费完毕
```

await for 的特点：

- 和普通 for 循环写法相似，但每次迭代会等待下一个数据到达
- 当 Stream 关闭时，循环自动结束
- 只能在 async 函数中使用
- 如果需要中途退出，使用 break（和普通 for 循环一样）

await for 适合"需要顺序处理所有数据"的场景，如读取文件所有行。listen() 适合"需要持续响应事件"的场景，如按钮点击。两者可以互相替代，但各有擅长的领域。


## StreamController 创建 Stream

StreamController 是手动创建和控制 Stream 的工具。

你可以随时向其中添加数据、错误，或者关闭它。


## 实例

```text
RUNOOB 倒计时: 5 秒
RUNOOB 倒计时: 4 秒
RUNOOB 倒计时: 3 秒
RUNOOB 倒计时: 2 秒
RUNOOB 倒计时: 1 秒
RUNOOB 倒计时: 0 秒
倒计时结束！
```


### async* 生成器函数

如果你只需要简单地生成一个数据序列，async* 比 StreamController 更方便。


## 实例

```text
逐行读取：
  第一行
  第二行
  第三行
  RUNOOB

带错误的生成器：
  数字: 1
  数字: 2
  捕获错误: Exception: 数字 3 出错了！
```


## 单订阅 vs 广播流

Dart 的 Stream 分为两种类型：单订阅流（Single-subscription）和广播流（Broadcast）。


### 单订阅流（Single-subscription Stream）

这是默认的 Stream 类型。

它只能被一个监听者订阅，适合"从头到尾消费一次"的场景。


## 实例


### 广播流（Broadcast Stream）

广播流允许多个监听者同时订阅，适合事件广播场景。


## 实例

```text
RUNOOB 订阅者A: 收到 1
RUNOOB 订阅者B: 收到 1
RUNOOB 订阅者A: 收到 2
RUNOOB 订阅者B: 收到 2
RUNOOB 订阅者A: 收到 3
RUNOOB 订阅者B: 收到 3
RUNOOB 订阅者A: 收到 4
RUNOOB 订阅者B: 收到 4
RUNOOB 迟到的订阅者C: 收到 4
```

两种 Stream 的对比：

广播流的"迟到订阅者"只能收到订阅之后的事件，之前的事件已经错过了。这是广播流和单订阅流最重要的行为差异。


## Stream 常用转换方法

Stream 提供了一系列方法来转换和处理数据，类似于 List 的函数式方法。


## 实例

```text
翻倍:
  2
  4
  6
  8
  10
  12
偶数:
  10
  20
  30
只取前 3 个:
  RUNOOB: 1
  RUNOOB: 2
  RUNOOB: 3
跳过前 2 个:
  3
  4
  5
去重:
  1
  2
  3
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Dart Stream 流` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
