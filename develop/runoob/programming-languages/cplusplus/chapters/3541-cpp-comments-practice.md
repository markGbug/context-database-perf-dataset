# C++：C++ 注释

- 来源：[C++ 注释](https://www.runoob.com/cplusplus/cpp-comments.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：练习笔记
- 章节序号：3541

## 本章内容

程序的注释是解释性语句，您可以在 C++ 代码中包含注释，这将提高源代码的可读性。所有的编程语言都允许某种形式的注释。

C++ 支持单行注释和多行注释。注释中的所有字符会被 C++ 编译器忽略。

C++ 注释一般有两种：

- // - 一般用于单行注释。
- /* ... */ - 一般用于多行注释。

注释以 // 开始，直到行末为止。例如：


## 实例

```java
#include <iostream>
using namespace std;

int main() {
  // 这是一个注释
  cout << "Hello World!";
  return 0;
}
```

也可以放在语句后面：


## 实例

```java
#include <iostream>
using namespace std;

int main()
{
   cout << "Hello World!"; // 输出 Hello World!

   return 0;
}
```

当上面的代码被编译时，编译器会忽略 // 这是一个注释 和 // 输出 Hello World!，最后会产生以下结果：

```text
Hello World!
```

C++ 注释以 /* 开始，以 */ 终止。例如：

```java
#include <iostream>
using namespace std;

int main() {
    /* 这是注释 */

    /* C++ 注释也可以
     * 跨行
     */
    cout << "Hello World!";
    return 0;
}
```

在 /* 和 */ 注释内部，// 字符没有特殊的含义。在 // 注释内，/* 和 */ 字符也没有特殊的含义。因此，您可以在一种注释内嵌套另一种注释。例如：

```text
/* 用于输出 Hello World 的注释

cout << "Hello World"; // 输出 Hello World

*/
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `C++ 注释` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
