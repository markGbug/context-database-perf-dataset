# C：C 标准库 <stdbool.h>

- 来源：[C 标准库 <stdbool.h>](https://www.runoob.com/cprogramming/c-standard-library-stdbool-h.html)
- 分类：编程语言
- 技术：C
- 笔记类型：练习笔记
- 章节序号：3531

## 本章内容

在 C99 标准之前，C 语言中通常使用整数类型（如 int）来表示布尔值。例如，0 表示假，非零值（通常是 1）表示真。这种方式虽然可行，但缺乏直观性和类型安全性。为了解决这个问题，C99 标准引入了 stdbool.h 头文件，定义了布尔类型和相关宏。

<stdbool.h> 是 C 语言中的一个标准头文件，定义了布尔类型及其相关的常量。它使得 C 语言的布尔类型（bool）变得更加明确和可用，避免了使用整数（如 0 或 1）来表示布尔值的传统做法。

stdbool.h 头文件定义了以下内容：

- bool：布尔类型，用于声明布尔变量。
- true：表示真值的宏，通常定义为 1。
- false：表示假值的宏，通常定义为 0。
- __bool_true_false_are_defined：一个宏，用于指示 true 和 false 是否已定义。

这些宏的定义如下：

```text
#define bool _Bool
#define true 1
#define false 0
#define __bool_true_false_are_defined 1
```

bool 是 _Bool 类型的别名。

_Bool 是 C99 标准中引入的原生类型，表示一个布尔值。_Bool 类型只能保存 0 或 1，因此适合用来存储逻辑值。

```html
#include <stdbool.h>

_Bool is_valid = 1;  // 也可以直接使用 _Bool 类型
```

要在 C 程序中使用布尔类型和相关宏，首先需要引入 <stdbool.h> 头文件：

```html
#include <stdbool.h>

bool is_raining = true;
bool is_sunny = false;
```


### 实例

以下是一个使用 <stdbool.h> 的简单示例：


## 实例

输出结果：

```text
The system is ready.
The task is not finished.
isReady: 1
isFinished: 0
```


### bool 类型

使用 bool 类型定义布尔变量：


## 实例

以上实例中，flag 是一个布尔类型的变量，初始值为 true。判断 flag 是否为 true，然后打印相应的消息。


### true 和 false 宏

true 和 false 是预定义的宏，分别对应布尔值 1 和 0，可以直接在条件判断中使用：


## 实例


### 与 if 和 while 等语句配合使用

布尔类型在 if、while、for 等控制结构中很有用：


## 实例

这里，while 循环会继续执行，直到 condition 变为 true。


### 布尔类型与整数的兼容性

尽管 bool 类型本身是一个专门的类型，但在底层实现上，它通常依赖于整数类型（通常为 int）。因此，true 可以被认为是 1，而 false 则是 0。

但是，在编程时应该避免将布尔值与普通整数混用，尽量保持类型的清晰性和可读性。


## 实例

虽然上述代码会正确执行，但不推荐使用，因为它混合了布尔值和整数类型，容易让代码变得难以理解。


### 布尔类型的优势

- 可读性：使用 bool 类型使得程序的意图更加明确，比起使用 int 类型代表真或假，bool 类型能够清晰地表明该变量只用来表示布尔值。
- 标准化：<stdbool.h> 提供了一个标准的方式来处理布尔值，避免了使用宏或整数类型来表示布尔值的复杂性。
- 类型安全：与 int 类型不同，bool 类型专门用于逻辑判断，减少了类型不匹配的问题。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `C 标准库 <stdbool.h>` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
