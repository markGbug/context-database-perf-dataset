# C++：C++ 标准库 <codecvt>

- 来源：[C++ <codecvt>](https://www.runoob.com/cplusplus/cpp-libs-codecvt.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：练习笔记
- 章节序号：3628

## 本章内容

<codecvt> 是 C++ 标准库中的一个头文件，提供了字符转换的工具。这个头文件主要包含 std::codecvt 类模板及其特化，支持字符编码之间的转换，例如从 UTF-8 到 UTF-16，或从宽字符（wchar_t）到窄字符（char）等。std::codecvt 类通常与 std::wstring_convert 类一起使用，以实现字符编码转换。


## 语法

codecvt 命名空间中的主要类和函数如下：

- codecvt_base：定义了编码转换的状态类型和错误处理方式。
- codecvt_byname：模板类，用于创建特定编码的转换器。
- codecvt_utf8、codecvt_utf16：特定编码的转换器类。


### 基本语法

```html
#include <codecvt>
#include <locale>
#include <string>

std::wstring_convert<std::codecvt_utf8_utf16<wchar_t>> converter;
std::wstring wide_string = converter.from_bytes("Hello, World!");
std::string narrow_string = converter.to_bytes(L"你好，世界！");
```


## 实例


### 示例 1：UTF-8 到 UTF-16 的转换

在这个示例中，我们将演示如何使用 codecvt 将 UTF-8 编码的字符串转换为 UTF-16 编码的宽字符串。


## 实例

输出结果：

```text
Wide string: Hello, World!
Converted string: Hello, World!
```


### 示例 2：使用 codecvt_byname 进行编码转换

在这个示例中，我们将演示如何使用 codecvt_byname 类来创建一个基于名称的编码转换器，并使用它进行转换。


## 实例

输出结果：

```text
Wide string: 你好，世界！
Converted string: 你好，世界！
```


### std::codecvt 类模板特化

std::codecvt 有多个特化版本，用于不同的字符编码转换：

- std::codecvt_utf8<wchar_t>：宽字符（wchar_t）与 UTF-8 之间的转换。
- std::codecvt_utf8_utf16<char16_t>：UTF-8 与 UTF-16 之间的转换。
- std::codecvt_utf8<char32_t>：UTF-8 与 UTF-32 之间的转换。


### std::wstring_convert 类模板

std::wstring_convert 类模板是一个辅助类，用于管理字符编码转换的生命周期和异常处理：

- to_bytes：将宽字符或其他编码的字符串转换为窄字符（字节序列）。
- from_bytes：将窄字符（字节序列）转换为宽字符或其他编码的字符串。


### 注意事项

- C++17 标准中 std::codecvt 已被弃用，建议在未来使用其他替代方案（如 ICU 库）进行字符编码转换。
- 对于跨平台应用程序，处理字符编码时应特别小心，确保在所有平台上行为一致。


### 总结

<codecvt> 提供了一套强大的工具，用于不同字符编码之间的转换，特别是 UTF-8、UTF-16 和宽字符之间的转换。虽然在 C++17 中已被弃用，但它在处理字符编码转换时仍然是一个有用的工具。了解和掌握这些工具的使用，可以帮助你编写更灵活和国际化的应用程序。如果你有特定的使用需求或问题，可以进一步讨论。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `C++ <codecvt>` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
