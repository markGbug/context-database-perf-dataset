# C++：C++ 标准库 <type_traits>

- 来源：[C++ <type_traits>](https://www.runoob.com/cplusplus/cpp-libs-type_traits.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：练习笔记
- 章节序号：3617

## 本章内容

<type_traits> 是 C++ 标准库中一个非常有用的头文件，它包含了一组编译时检查类型特性的工具。这些工具可以帮助开发者在编译时确定类型的特性，从而实现更安全、更灵活的代码。

<type_traits> 头文件定义了一组模板，这些模板可以用于查询和操作类型属性。这些属性包括但不限于：

- 是否是整数类型
- 是否是浮点类型
- 是否是指针类型
- 是否是引用类型
- 是否是可调用的（函数或函数指针）


## 语法

<type_traits> 中的模板通常使用 std:: 前缀，例如 std::is_integral<T>::value 用于检查类型 T 是否是整数类型。这里的 value 是一个静态常量，其值为 true 或 false。

以下是一些常用的 type_traits 功能：

基本类型判断：

- std::is_void<T>: 判断类型 T 是否为 void。
- std::is_integral<T>: 判断类型 T 是否为整型。
- std::is_floating_point<T>: 判断类型 T 是否为浮点型。
- std::is_array<T>: 判断类型 T 是否为数组类型。
- std::is_pointer<T>: 判断类型 T 是否为指针类型。
- std::is_reference<T>: 判断类型 T 是否为引用类型。
- std::is_const<T>: 判断类型 T 是否为 const 修饰。

类型修饰：

- std::remove_const<T>: 移除类型 T 的 const 修饰。
- std::remove_volatile<T>: 移除类型 T 的 volatile 修饰。
- std::remove_cv<T>: 同时移除类型 T 的 const 和 volatile 修饰。
- std::remove_reference<T>: 移除类型 T 的引用修饰。
- std::remove_pointer<T>: 移除类型 T 的指针修饰。

类型转换：

- std::add_const<T>: 为类型 T 添加 const 修饰。
- std::add_volatile<T>: 为类型 T 添加 volatile 修饰。
- std::add_cv<T>: 同时为类型 T 添加 const 和 volatile 修饰。
- std::add_pointer<T>: 为类型 T 添加指针修饰。
- std::add_lvalue_reference<T>: 为类型 T 添加左值引用修饰。
- std::add_rvalue_reference<T>: 为类型 T 添加右值引用修饰。

类型特性检测：

- std::is_same<T, U>: 判断类型 T 和 U 是否相同。
- std::is_base_of<Base, Derived>: 判断类型 Base 是否为类型 Derived 的基类。
- std::is_convertible<From, To>: 判断类型 From 是否能转换为类型 To。

条件类型：


## 实例

以下是一些使用 <type_traits> 的实例，以及它们的输出结果。


### 检查是否是整数类型


## 实例

输出结果:

```java
int is integral: 1
float is integral: 0
char is integral: 1
```


### 检查是否是浮点类型


## 实例

输出结果:

```java
int is floating_point: 0
float is floating_point: 1
double is floating_point: 1
```


### 检查是否是指针类型


## 实例

输出结果:

```java
int* is a pointer: 1
int is a pointer: 0
```


### 检查是否是引用类型


## 实例

输出结果:

```java
int& is a reference: 1
int is a reference: 0
```


### 检查是否是可调用的


## 实例

输出结果:

```java
int is callable: 0
void() is callable: 1
func is callable: 1
```

<type_traits> 是 C++ 中一个非常有用的工具，它允许开发者在编译时检查和操作类型属性。这不仅可以提高代码的安全性，还可以使代码更加灵活和可重用。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `C++ <type_traits>` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
