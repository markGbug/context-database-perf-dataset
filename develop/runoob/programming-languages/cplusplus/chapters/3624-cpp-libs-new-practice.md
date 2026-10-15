# C++：C++ 内存管理库 <new>

- 来源：[C++ <new>](https://www.runoob.com/cplusplus/cpp-libs-new.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：练习笔记
- 章节序号：3624

## 本章内容

C++ 是一种功能强大的编程语言，它提供了丰富的标准库来帮助开发者更高效地编写代码。

在 C++ 中，<new> 是一个非常重要的头文件，它包含了用于动态内存分配的函数和异常类型。

动态内存分配允许程序在运行时请求内存，这在处理不确定大小的数据结构时非常有用。

<new> 头文件定义了以下几个关键组件：

- new 运算符：用于动态分配内存。
- delete 运算符：用于释放动态分配的内存。
- nothrow 运算符：用于在内存分配失败时不抛出异常。
- std::bad_alloc 异常：当内存分配失败时抛出。


## 语法


### 使用 new 运算符

new 运算符用于在堆上分配内存。其基本语法如下：

```html
<code class="language-cpp">pointer new (type [, initializer]);</code>
```

- pointer 是指向分配的内存的指针。
- type 是要分配的对象的类型。
- initializer 是一个可选的初始化表达式。


### 使用 delete 运算符

delete 运算符用于释放之前使用 new 分配的内存。其基本语法如下：

```html
<code class="language-cpp">delete pointer;</code>
```

- pointer 是之前使用 new 分配的内存的指针。


## 实例

动态分配单个对象:


## 实例

输出结果：

```text
Value: 10
```

动态分配数组:


## 实例

输出结果：

```text
Array[0]: 0
Array[1]: 2
Array[2]: 4
Array[3]: 6
Array[4]: 8
Array[5]: 10
Array[6]: 12
Array[7]: 14
Array[8]: 16
Array[9]: 18
```

使用 nothrow 避免异常:


## 实例

输出结果：

```text
Memory allocation failed. // 或者 Memory allocation succeeded. 取决于系统内存情况
```


### 异常处理

当使用 new 运算符分配内存失败时，C++ 会抛出一个 std::bad_alloc 异常。

开发者可以通过 try-catch 块来捕获并处理这个异常。


## 实例

输出结果：

```text
Exception caught: std::bad_alloc // 如果内存分配失败
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `C++ <new>` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
