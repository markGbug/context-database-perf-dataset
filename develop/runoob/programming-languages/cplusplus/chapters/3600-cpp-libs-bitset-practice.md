# C++：C++ 标准库 <bitset>

- 来源：[C++ <bitset>](https://www.runoob.com/cplusplus/cpp-libs-bitset.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：练习笔记
- 章节序号：3600

## 本章内容

在 C++ 编程中，<bitset> 是标准库的一部分，它提供了一种方式来操作固定大小的位集合。

位集合是一个由位（bit）组成的数组，每个位可以是 0 或 1。

<bitset> 提供了一种高效的方式来存储和操作二进制数据，特别适合需要位级操作的场景，如标志位管理、位掩码操作等。

bitset 是一个模板类，其模板参数定义了位集合的大小。例如，bitset<32> 表示一个包含 32 位的位集合。


### 语法

以下是使用 bitset 的基本语法：

```html
#include <bitset>

// 声明一个大小为N的bitset
std::bitset<N> b;

// 初始化bitset
b = std::bitset<N>(value);

// 访问位集合中的单个位
bool bit = b[i];
```


### std::bitset 的基本用法

std::bitset 是一个模板类，用于表示固定大小的二进制位序列。它的模板参数是位数（N），表示二进制序列的长度。

定义 std::bitset：

```text
std::bitset<8> bits;  // 定义一个 8 位的二进制序列
```

初始化 std::bitset：

- 默认初始化：所有位为 0。
- 从整数初始化：将整数转换为二进制。
- 从字符串初始化：将字符串解析为二进制。


## 实例


### 常用成员函数

std::bitset 提供了丰富的成员函数来操作二进制位。

访问和修改位:

- operator[]：访问或修改某一位。
- set()：将某一位或所有位设置为 1。
- reset()：将某一位或所有位设置为 0。
- flip()：翻转某一位或所有位。


## 实例

查询位信息:

- count()：返回 1 的个数。
- size()：返回位数。
- test(pos)：检查某一位是否为 1。
- all()：检查是否所有位都为 1。
- any()：检查是否有任何一位为 1。
- none()：检查是否所有位都为 0。


## 实例

转换为其他类型:

- to_ulong()：将 std::bitset 转换为 unsigned long。
- to_ullong()：将 std::bitset 转换为 unsigned long long。
- to_string()：将 std::bitset 转换为字符串。


## 实例


### 位操作

std::bitset 支持常见的位操作，如按位与、按位或、按位异或和按位取反。

- &：按位与
- |：按位或
- ^：按位异或
- ~：按位取反


## 实例


## 实例

基本使用:


## 实例

输出结果：

```text
Initial bitset: 11001010
Bit at position 3: 0
Modified bitset: 11001011
Flipped bitset: 00110110
```

位操作:


## 实例

输出结果：

```text
Bitwise AND: 10100000
Bitwise OR: 11111010
Bitwise XOR: 01111010
Bitwise NOT: 01010101
```

循环遍历位集合:


## 实例

输出结果：

```text
10101010
```

bitset 是C++标准库中一个非常有用的工具，它允许程序员以一种直观和高效的方式处理位级数据。通过上述实例，我们可以看到如何声明、初始化、访问、修改以及进行位操作。这些功能在处理二进制数据或需要进行位级控制的场合非常有用。


### 注意事项

- std::bitset 的大小是固定的，在编译时确定。
- 如果位数超过 unsigned long 或 unsigned long long 的位数，to_ulong() 和 to_ullong() 会抛出 std::overflow_error 异常。
- std::bitset 不支持动态调整大小，如果需要动态位集，可以考虑 std::vector<bool>。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `C++ <bitset>` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
