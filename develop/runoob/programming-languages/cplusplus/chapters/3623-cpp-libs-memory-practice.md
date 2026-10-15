# C++：C++ 内存管理库 <memory>

- 来源：[C++ <memory>](https://www.runoob.com/cplusplus/cpp-libs-memory.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：练习笔记
- 章节序号：3623

## 本章内容

<memory> 是 C++ 标准库中的一个头文件，它包含了用于动态内存管理的模板和函数。

在 C++ 中，内存管理是一个重要的概念。动态内存管理允许程序在运行时分配和释放内存，这在处理不确定大小的数据结构时非常有用。然而，不正确的内存管理可能导致内存泄漏、野指针等问题。

<memory> 头文件提供了智能指针等工具，帮助开发者更安全地管理动态内存。


### 智能指针

智能指针是 <memory> 头文件中的核心内容。它们是 C++11 引入的特性，用于自动管理动态分配的内存。智能指针的主要类型有：

- std::unique_ptr：独占所有权的智能指针，同一时间只能有一个 unique_ptr 指向特定内存。
- std::shared_ptr：共享所有权的智能指针，多个 shared_ptr 可以指向同一内存，内存在最后一个 shared_ptr 被销毁时释放。
- std::weak_ptr：弱引用智能指针，用于与 shared_ptr 配合使用，避免循环引用导致的内存泄漏。


## 实例


### 使用 std::unique_ptr


## 实例

输出结果：

```text
Doing something
```


### 使用 std::shared_ptr


## 实例

输出结果：

```text
Doing something
Doing something
```


### 使用 std::weak_ptr

std::weak_ptr 通常不单独使用，而是与 std::shared_ptr 结合使用，以解决循环引用问题。


## 实例

在这个例子中，node1 和 node2 形成了循环引用。由于 prev 是 weak_ptr，当 node1 和 node2 的 shared_ptr 被销毁时，它们指向的内存也会被正确释放。


## 分配器

分配器是 <memory> 中的另一重要部分。

分配器用于为容器分配内存，标准库的所有容器都使用分配器来处理内存分配。


### std::allocator

std::allocator 是标准分配器，提供了基本的内存分配和释放功能。


## 实例


## 其他内存管理工具


### std::align

std::align 用于调整指针的对齐方式，以确保所分配内存满足特定对齐要求。


## 实例

<memory> 头文件是 C++ 标准库中处理动态内存管理的重要部分。

通过使用智能指针，如 unique_ptr、shared_ptr 和 weak_ptr，开发者可以更安全、更有效地管理内存，避免常见的内存管理错误。希望这篇文章能帮助初学者更好地理解和使用 C++ 的 <memory> 头文件。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `C++ <memory>` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
