# Dart：Dart 控制流

- 来源：[Dart 控制流](https://www.runoob.com/dart/dart-control-flow.html)
- 分类：编程语言
- 技术：Dart
- 笔记类型：练习笔记
- 章节序号：3642

## 本章内容

控制流决定了程序中的代码按照什么顺序执行。

本章介绍 Dart 中的条件判断（if/else、switch）和循环语句（for、while），以及 break 与 continue 的使用。


## if / else / else if 条件判断

if 语句是最基本的控制流结构，它根据条件决定是否执行某段代码。


## 实例

基本的 if 判断：

```text
RUNOOB 恭喜，你及格了！
继续加油
等级：B
```

Dart 的条件表达式必须是 bool 类型。不能像 JavaScript 那样用 0、''、null 等作为条件——这些写法在 Dart 中会直接报编译错误。


### if 语句的嵌套

if 语句内部可以再嵌套 if，处理更复杂的逻辑。


## 实例

```text
欢迎回来，runoob
```

嵌套层次过多会降低可读性，建议不超过 3 层。

如果逻辑确实复杂，可以考虑用提前返回（return）或拆分函数来简化。


## 实例

用提前返回替代深层嵌套：

```text
你没有管理权限
欢迎回来，管理员 runoob
```


## switch / case 多分支选择

当一个变量有多个固定的可能值时，switch 比 if-else if 更清晰。


## 实例

```text
一周过半了
```

Dart 的 switch 不会自动"穿透"（fall-through），每个非空的 case 必须以 break、return、throw 或 continue 结尾。如果想实现穿透效果，使用 continue 配合标签（label）。


### switch 表达式（Dart 3.0+）

Dart 3.0 引入了 switch 表达式，可以直接产出值，写法更简洁。


## 实例

```text
RUNOOB 心情: 干劲十足
```

switch 表达式要求覆盖所有可能的情况，编译器会帮你检查是否有遗漏。


## for 循环

for 循环是最常用的循环结构，适合在知道循环次数时使用。


### 标准 for 循环


## 实例

```text
RUNOOB 第 1 次循环
RUNOOB 第 2 次循环
RUNOOB 第 3 次循环
RUNOOB 第 4 次循环
RUNOOB 第 5 次循环
j = 0
j = 1
j = 2
```


### for-in 循环（遍历集合）

for-in 是遍历 List、Set 等集合最简洁的方式。


## 实例

```text
RUNOOB 水果: 苹果
RUNOOB 水果: 香蕉
RUNOOB 水果: 橙子
RUNOOB 水果: 葡萄
```


### forEach 方法

List 和 Set 还提供了 forEach 方法，使用回调函数处理每个元素。


## 实例

```text
RUNOOB 分数: 85 -> 及格
RUNOOB 分数: 92 -> 及格
RUNOOB 分数: 78 -> 及格
RUNOOB 分数: 60 -> 及格
```


## while 与 do-while 循环

while 循环在每次迭代前检查条件，适合循环次数不确定的场景。


## 实例

```text
RUNOOB 倒计时: 3
RUNOOB 倒计时: 2
RUNOOB 倒计时: 1
发射！
```

do-while 与 while 的区别是：它至少会执行一次循环体，因为条件在最后才检查。


## 实例

```text
RUNOOB 至少执行一次，num = 0
循环结束，num = 1
```

do-while 保证循环体至少执行一次，即使条件一开始就不满足。这在"先尝试再判断"的场景中很有用，比如读取用户输入直到有效。


### while vs for：如何选择


## break 与 continue

break 用于立即退出整个循环，continue 用于跳过当前迭代进入下一轮。


## 实例

```text
检查: Alice
检查: Bob
检查: runoob
找到 RUNOOB 了！
---分隔线---
RUNOOB 第 1 次
RUNOOB 第 2 次
RUNOOB 第 4 次
RUNOOB 第 5 次
```


### 带标签的 break 与 continue

在嵌套循环中，标签可以让你跳出指定的外层循环。


## 实例

```text
i=1, j=1
i=1, j=2
i=1, j=3
i=2, j=1
i=2, j=2
找到目标，退出外层循环
循环结束
```

标签（label）应该谨慎使用。大多数情况下，将嵌套循环逻辑提取为独立的函数，用 return 来退出会更清晰。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Dart 控制流` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
