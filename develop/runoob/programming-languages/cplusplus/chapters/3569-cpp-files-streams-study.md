# C++：C++ 文件和流

- 来源：[C++ 文件和流](https://www.runoob.com/cplusplus/cpp-files-streams.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：学习笔记
- 章节序号：3569

## 本章内容

在前面的章节中，我们使用过 C++ 标准库中的 cin 和 cout，分别从键盘读取数据和向屏幕输出内容。

除了标准输入输出，C++ 还支持文件操作，可以将数据保存到文件中，也可以从文件中读取已有的数据。

C++ 通过 <fstream> 头文件提供文件输入输出功能，主要包含以下三个文件流类：

使用文件流时，需要包含头文件：

```html
#include <fstream>
```

如果程序还需要使用 cin、cout 等标准输入输出对象，则需要包含：

```html
#include <iostream>
```

例如，创建一个用于写入文件的对象：

```text
std::ofstream outfile("example.txt");
```

以上代码尝试打开 example.txt 文件。如果文件不存在，通常会创建新文件；如果文件已经存在，默认会清空原有内容。


## 打开文件

在读取或写入文件之前，首先需要打开文件。

C++ 可以通过文件流对象的构造函数直接打开文件，也可以先创建对象，再使用 open() 成员函数打开。

方式一：创建对象时打开文件

```text
std::ofstream outfile("example.txt");
```

方式二：使用 open() 方法

```text
std::ofstream outfile;
outfile.open("example.txt");
```

这两种方式都可以用于打开文件，第一种写法更简洁。

open() 的一种常见形式如下：

```javascript
void open(
    const char* filename,
    std::ios::openmode mode
);
```

其中：

- filename：要打开的文件名称或路径。
- mode：文件打开模式，用于指定读取、写入、追加等操作。

上述是简化后的函数声明，不同文件流类具有不同的默认打开模式。现代 C++ 也支持使用 std::string 指定文件名，C++17 起还支持 std::filesystem::path。


### 文件打开模式

C++ 提供了多种文件打开模式，可以根据需要进行选择。

多个模式可以使用按位或运算符 | 组合。

例如，以写入模式打开文件，并清空原有内容：

```text
std::ofstream outfile;
outfile.open("file.dat", std::ios::out | std::ios::trunc);
```

如果希望保留文件原有内容，并将新内容追加到末尾，可以使用：

```text
std::ofstream outfile;
outfile.open("file.dat", std::ios::app);
```

如果需要同时读取和写入文件，可以使用 fstream：

```text
std::fstream file;
file.open("file.dat", std::ios::in | std::ios::out);
```

注意：上述双向读写模式通常要求文件已经存在。如果需要创建新文件，可以根据实际需求组合写入模式，但应注意 trunc 可能清空原有内容。

默认情况下，三个文件流类通常使用以下打开模式：


### 检查文件是否打开成功

文件打开操作并不一定成功。例如，文件不存在、路径错误或者没有访问权限，都可能导致打开失败。

可以使用 is_open() 方法检查文件是否成功打开。


## 实例

```java
#include <iostream>
#include <fstream>
using namespace std;

int main()
{
    ifstream infile("example.txt");

    if (!infile.is_open()) {
        cout << "文件打开失败！" << endl;
        return 1;
    }

    cout << "文件打开成功！" << endl;

    infile.close();

    return 0;
}
```

如果当前工作目录中不存在 example.txt 文件，程序将输出：

```text
文件打开失败！
```

除了 is_open()，还可以使用 fail()、bad() 等成员函数检查流的状态。


## 关闭文件

文件使用完毕后，可以通过 close() 方法关闭文件。

其基本调用方式如下：

```text
outfile.close();
```

关闭文件时，文件流会尝试完成必要的缓冲区刷新，并解除与文件的关联。

C++ 文件流对象还具有自动资源管理机制。当局部文件流对象离开作用域并被销毁时，关联的文件也会自动关闭。

例如：

```text
{
    std::ofstream file("example.txt");
    file << "Hello C++";
} // file 离开作用域，自动关闭文件
```

因此，并不是每次都必须显式调用 close()。不过，如果需要提前关闭文件、重新打开其他文件，或者检查关闭时的错误，可以主动调用 close()。


## 写入文件

在 C++ 中，可以使用输出文件流 ofstream，通过流插入运算符 << 向文件写入数据。

使用方法与通过 cout 向屏幕输出内容类似。


## 实例

```java
#include <iostream>
#include <fstream>
using namespace std;

int main()
{
    // 创建并打开文件
    ofstream outfile("example.txt");

    if (!outfile) {
        cerr << "无法打开文件！" << endl;
        return 1;
    }

    // 向文件写入内容
    outfile << "Hello C++" << '\n';
    outfile << "欢迎学习 C++ 文件操作" << '\n';
    outfile << "数字：" << 100 << '\n';

    // 关闭文件
    outfile.close();

    if (!outfile) {
        cerr << "文件写入或关闭失败！" << endl;
        return 1;
    }

    cout << "文件写入成功！" << endl;

    return 0;
}
```

程序正常执行后，屏幕输出：

```text
文件写入成功！
```

同时，在当前工作目录下生成 example.txt 文件，内容如下：

```text
Hello C++
欢迎学习 C++ 文件操作
数字：100
```

注意：如果 example.txt 已经存在，默认使用 ofstream 打开文件时会清空原有内容。


### 追加写入文件

如果不希望清空原有内容，而是想在文件末尾增加数据，可以使用 ios::app 模式。


## 实例

```java
#include <iostream>
#include <fstream>
using namespace std;

int main()
{
    // 以追加模式打开文件
    ofstream outfile("example.txt", ios::app);

    if (!outfile) {
        cerr << "无法打开文件！" << endl;
        return 1;
    }

    outfile << "这是一行追加的内容。" << '\n';

    outfile.close();

    if (!outfile) {
        cerr << "文件写入失败！" << endl;
        return 1;
    }

    cout << "内容追加成功！" << endl;

    return 0;
}
```

程序每执行一次，就会尝试在文件末尾追加一行内容，而不会主动清空已有数据。


## 读取文件

在 C++ 中，可以使用输入文件流 ifstream 读取文件内容。

常见的读取方式包括：

- >>：按格式读取数据，通常以空白字符作为分隔。
- getline()：读取一整行文本，可以保留行内空格。
- read()：读取指定数量的字符数据，常用于二进制文件。


### 使用 >> 读取数据

下面演示如何读取文件中的两个整数。


## 实例

```java
#include <iostream>
#include <fstream>
using namespace std;

int main()
{
    // 先创建测试文件
    {
        ofstream outfile("numbers.txt");

        if (!outfile) {
            cerr << "创建文件失败！" << endl;
            return 1;
        }

        outfile << "100 200" << '\n';

        outfile.close();

        if (!outfile) {
            cerr << "写入测试文件失败！" << endl;
            return 1;
        }
    }

    ifstream infile("numbers.txt");

    if (!infile) {
        cerr << "读取文件失败！" << endl;
        return 1;
    }

    int a, b;

    if (infile >> a >> b) {
        cout << "a = " << a << endl;
        cout << "b = " << b << endl;
    } else {
        cerr << "文件数据格式错误！" << endl;
        return 1;
    }

    return 0;
}
```

执行结果：

```text
a = 100
b = 200
```

流提取运算符 >> 会根据目标数据类型读取内容，并在默认情况下跳过前导空白字符。

如果读取字符串，例如 infile >> name，遇到空格、制表符或换行符通常就会停止，因此不适合读取包含空格的完整文本行。


### 使用 getline() 逐行读取

如果需要读取包含空格的文本，可以使用 getline()。


## 实例

```java
#include <iostream>
#include <fstream>
#include <string>
using namespace std;

int main()
{
    ifstream infile("example.txt");

    if (!infile) {
        cerr << "无法打开文件！" << endl;
        return 1;
    }

    string line;

    // 逐行读取，直到文件结束或读取失败
    while (getline(infile, line)) {
        cout << line << endl;
    }

    if (infile.bad()) {
        cerr << "读取文件时发生错误！" << endl;
        return 1;
    }

    infile.close();

    return 0;
}
```

如果文件中包含以下内容：

```text
Hello C++
Welcome to C++ programming
This is a text file.
```

程序正常运行时，会逐行输出对应的文本。

getline() 默认读取到换行符为止，并将读取到的内容保存到 string 对象中，但不会将行末分隔符保存进去。

注意：当使用 cin >> 读取数字后，再使用 getline(cin, ...) 读取整行时，可能需要先处理输入缓冲区中剩余的换行符。这是因为格式化输入通常不会提取末尾的换行符。


## 读取 & 写入实例

下面通过一个完整实例，演示如何将用户输入的信息写入文件，然后重新打开文件并读取其中的内容。

程序会要求用户输入姓名和年龄，将数据保存到 afile.dat 文件中，再读取并显示到屏幕上。


## 实例

```java
#include <iostream>
#include <fstream>
#include <string>
using namespace std;

int main()
{
    string name;
    int age;

    // 获取用户输入
    cout << "Enter your name: ";
    getline(cin, name);

    cout << "Enter your age: ";

    if (!(cin >> age)) {
        cerr << "Invalid age!" << endl;
        return 1;
    }

    // 以写入模式打开文件
    ofstream outfile("afile.dat");

    if (!outfile) {
        cerr << "Cannot open file for writing!" << endl;
        return 1;
    }

    // 写入数据
    outfile << name << '\n';
    outfile << age << '\n';

    // 关闭文件并检查状态
    outfile.close();

    if (!outfile) {
        cerr << "Failed to write file!" << endl;
        return 1;
    }

    // 以读取模式重新打开文件
    ifstream infile("afile.dat");

    if (!infile) {
        cerr << "Cannot open file for reading!" << endl;
        return 1;
    }

    string readName;
    int readAge;

    // 读取姓名
    if (!getline(infile, readName)) {
        cerr << "Failed to read name!" << endl;
        return 1;
    }

    // 读取年龄
    if (!(infile >> readAge)) {
        cerr << "Failed to read age!" << endl;
        return 1;
    }

    // 输出文件内容
    cout << "Reading from the file" << endl;
    cout << "Name: " << readName << endl;
    cout << "Age: " << readAge << endl;

    infile.close();

    return 0;
}
```

当程序被编译和执行时，假设输入姓名 Zara，年龄为 9，运行结果如下：

```text
Enter your name: Zara
Enter your age: 9
Reading from the file
Name: Zara
Age: 9
```

程序执行成功后，afile.dat 文件的内容为：

```text
Zara
9
```

程序说明：

- getline(cin, name)：读取用户输入的整行姓名，支持姓名中包含空格。
- cin >> age：读取用户输入的整数年龄，并检查输入是否成功。
- ofstream：打开文件并写入姓名和年龄。
- close()：关闭文件，检查写入及关闭操作是否成功。
- ifstream：重新打开文件，读取保存的数据。
- getline(infile, readName)：从文件中读取完整的姓名。
- infile >> readAge：从文件中读取整数年龄。

这个实例采用先写入、再关闭、最后重新打开读取的方式，便于初学者理解文件输入输出过程。

如果需要在同一个文件流对象中进行读写，可以使用 fstream，但需要正确管理读取和写入位置，以及流的状态。


## 文件位置指针

文件流会维护与读写位置有关的状态，用于确定下一次从哪里读取数据，或者向哪里写入数据。

常用的文件位置操作函数包括：

其中，字母 g 来自 get，表示读取；字母 p 来自 put，表示写入。


### seekg() 和 seekp()

seekg() 和 seekp() 可以使用绝对位置，也可以使用相对于某个基准位置的偏移量。

常见的定位基准包括：

以下代码展示了常见的定位方式：


## 实例

```text
// 假设 fileObject 是已打开的文件输入流

// 定位到文件开头
fileObject.seekg(0, ios::beg);

// 从文件开头向后移动 n 个位置单位
fileObject.seekg(n, ios::beg);

// 从当前位置向后移动 n 个位置单位
fileObject.seekg(n, ios::cur);

// 从文件末尾向前移动 n 个位置单位
fileObject.seekg(-n, ios::end);

// 定位到文件末尾
fileObject.seekg(0, ios::end);
```

上述代码用于说明函数的调用方式，其中 n 为适当的偏移量。

注意：在二进制文件中，常见实现允许按字节偏移进行定位；文本模式下可能存在换行符转换或编码相关问题，不应简单地将所有文件位置都理解为可任意计算的字节索引。


### 文件位置操作实例

下面创建一个二进制文件，写入字符串 ABCDEFGHIJ，然后使用 seekg() 从指定位置读取字符。


## 实例

```java
#include <iostream>
#include <fstream>
using namespace std;

int main()
{
    // 创建二进制文件
    ofstream outfile("position.dat", ios::binary);

    if (!outfile) {
        cerr << "创建文件失败！" << endl;
        return 1;
    }

    outfile << "ABCDEFGHIJ";
    outfile.close();

    if (!outfile) {
        cerr << "写入文件失败！" << endl;
        return 1;
    }

    // 以二进制模式读取文件
    ifstream infile("position.dat", ios::binary);

    if (!infile) {
        cerr << "打开文件失败！" << endl;
        return 1;
    }

    char ch;

    // 定位到偏移量为 4 的位置
    infile.seekg(4, ios::beg);

    if (!infile.get(ch)) {
        cerr << "读取文件失败！" << endl;
        return 1;
    }

    cout << "读取的字符：" << ch << endl;

    // 返回到文件开头
    infile.seekg(0, ios::beg);

    if (!infile.get(ch)) {
        cerr << "读取文件失败！" << endl;
        return 1;
    }

    cout << "第一个字符：" << ch << endl;

    infile.close();

    return 0;
}
```

执行结果：

```text
读取的字符：E
第一个字符：A
```

因为文件位置从 0 开始计算，所以偏移量为 4 的位置对应第 5 个字符 E。

在使用 seekg() 时，还需要注意流的状态。如果之前读取已经到达文件末尾，流可能设置了错误状态，必要时应通过 clear() 清除状态后再重新定位。


### 获取文件大小

对于普通二进制文件，可以结合 seekg() 和 tellg() 获取文件长度。


## 实例

```java
#include <iostream>
#include <fstream>
using namespace std;

int main()
{
    ifstream infile("position.dat", ios::binary | ios::ate);

    if (!infile) {
        cerr << "无法打开文件！" << endl;
        return 1;
    }

    // 打开文件后，读取位置位于文件末尾
    streampos size = infile.tellg();

    if (size == streampos(-1)) {
        cerr << "获取文件大小失败！" << endl;
        return 1;
    }

    cout << "文件大小：" << size << " 字节" << endl;

    infile.close();

    return 0;
}
```

如果 position.dat 是前面示例生成的文件，包含 10 个 ASCII 字符，通常输出：

```text
文件大小：10 字节
```

在常见平台和普通文件上，二进制流末尾位置可以用于获得文件的字节长度。对于现代 C++ 项目，也可以使用 C++17 提供的 std::filesystem::file_size() 获取普通文件大小。


## 文件操作注意事项

在实际开发中，文件操作还需要注意以下几个问题：

- 检查打开结果：文件路径不存在、权限不足等原因都可能导致打开失败。
- 注意覆盖问题：默认使用 ofstream 打开已有文件通常会清空原有内容，追加数据应使用 ios::app。
- 区分文本与二进制模式：文本文件可能涉及换行符转换，处理二进制数据应使用 ios::binary。
- 检查读写结果：文件打开成功不代表后续读取或写入一定成功。
- 合理处理文件路径：相对路径通常以程序的当前工作目录为基准，而不一定是源代码所在目录。
- 注意资源管理：文件流对象离开作用域时会自动关闭文件，必要时仍可主动调用 close()。

对于普通文本文件，推荐使用 std::string 和 std::getline() 读取内容，避免使用固定长度字符数组导致输入长度受限等问题。

对于需要随机访问的二进制文件，可以结合 read()、write()、seekg() 和 seekp() 实现更灵活的文件操作。


## 复习重点

- 能说明 `C++ 文件和流` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
