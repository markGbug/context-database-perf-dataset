# Zig：Zig 基本语法

- 来源：[Zig 基本语法](https://www.runoob.com/zig/zig-basic-syntax.html)
- 分类：编程语言
- 技术：Zig
- 笔记类型：学习笔记
- 章节序号：3781

## 本章内容

Zig 是一种新的编程语言，设计简单、高效，并且直接与 C 语言兼容。

下面是一些 Zig 的基本语法介绍，帮助你快速上手。

Zig 代码文件的后缀名为 .zig。


## 第一个 Zig 程序

我们先来看看 Zig 的 "Hello, World!" 程序。

我们先来初始化一个 zig 项目：

```text
mkdir hello-world
cd hello-world
zig init
```

然后在该项目下创建 hello.zig 文件，代码如下：


## 实例（hello.zig 文件）

代码解析：

1、导入标准库：

```javascript
const std = @import("std");
```

这行代码导入了 Zig 的标准库，类似于 C 语言中的 #include <stdio.h>。

2、定义 main 函数：

```text
pub fn main() !void
```

pub 关键字表示这个函数是公开的，fn 关键字用于定义函数，main 是函数的入口点。返回类型 !void 表示该函数不返回值，但可能返回一个错误（! 前缀表示错误联合类型）。

3、获取标准输出：

```javascript
const stdout = std.io.getStdOut().writer();
```

通过标准库获取标准输出的 writer，后续调用其方法写入内容。

4、打印 "Hello, World!"：

```text
try stdout.print("Hello, World!\n", .{});
```

print 方法将格式化字符串写入标准输出，.{} 是空的参数列表。try 关键字会在发生错误时将错误向上传播给调用者。

这个程序展示了 Zig 语言的一些基本特性，比如函数定义、标准库的使用和错误处理。

如果只是运行单个文件，可以直接使用：

```text
zig run hello.zig
```

如果想编译为可执行文件，使用：

```text
zig build-exe hello.zig
```

编译完成后在终端中运行：

```text
./hello
```

这将输出：

```text
Hello, World!
```


## 标识符

在 Zig 语言中，标识符是用来命名变量、函数、类型等的名称。

以下是一些关于 Zig 标识符的规则和特性：

- 字母和数字：标识符可以包含字母（A-Z 和 a-z）、数字（0-9）和下划线（_）。
- 开头字符：标识符必须以字母或下划线开头，不能以数字开头。
- 大小写敏感：Zig 是一种区分大小写的语言，这意味着 Variable 和 variable 是两个不同的标识符。
- 关键字和保留字：一些特定的单词在 Zig 中是保留的，不能用作标识符。例如 fn（函数）、struct（结构体）、if（条件语句）等。
- 命名约定：Zig 官方推荐以下约定： camelCase（小驼峰）：用于变量名和函数名。例如 myVariable、calculateSum。 PascalCase（大驼峰）：用于类型名和命名空间。例如 Point、ArrayList。 SCREAMING_SNAKE_CASE：用于编译时已知的常量（comptime 常量）。例如 MAX_SIZE。
- 可选类型：Zig 语言中有一个特殊的类型 ?T，表示一个类型为 T 的可选值。这在处理可能为空的值时非常有用。
- 编译时常量：在标识符前使用 comptime 关键字，可以表示该标识符是一个编译时常量。
- 错误类型：使用 error 关键字可以定义错误类型，例如： pub fn openFile(path: []const u8) !void { // ... }
- 类型后缀：在类型名称后使用 _t 后缀是 C 语言的习惯，在 Zig 中也可以这样做，但不是必需的。


## 保留关键词

以下是 Zig 语言的一些保留关键词：


## 基本语法


### 1. 变量与常量

在 Zig 中，变量使用 var 关键字定义，常量使用 const 关键字定义。

```javascript
const x: i32 = 10;  // 定义一个整数常量 x，值为 10
var y: f64 = 3.14;  // 定义一个浮点数变量 y，值为 3.14
```


### 2. 函数

函数使用 fn 关键字定义，并指定返回类型。

```javascript
const std = @import("std");

fn add(a: i32, b: i32) i32 {
    return a + b;
}

pub fn main() !void {
    const result = add(3, 4);
    const stdout = std.io.getStdOut().writer();
    try stdout.print("Result: {}\n", .{result});
}
```


### 3. 条件语句

使用 if 和 else 来实现条件逻辑。

```javascript
const std = @import("std");

pub fn main() !void {
    const stdout = std.io.getStdOut().writer();
    const number = 10;
    if (number > 0) {
        try stdout.print("Number is positive\n", .{});
    } else {
        try stdout.print("Number is not positive\n", .{});
    }
}
```


### 4. 循环

Zig 支持 while 和 for 循环。

```java
const std = @import("std");

pub fn main() !void {
    const stdout = std.io.getStdOut().writer();

    // while 循环，: (i += 1) 是每次迭代后执行的更新表达式
    var i: i32 = 0;
    while (i < 5) : (i += 1) {
        try stdout.print("i: {}\n", .{i});
    }

    // for 循环，遍历数组
    const array = [5]i32{ 1, 2, 3, 4, 5 };
    for (array) |item| {
        try stdout.print("item: {}\n", .{item});
    }
}
```


### 5. 结构体

Zig 使用 struct 来定义结构体。

```java
const std = @import("std");

const Point = struct {
    x: i32,
    y: i32,
};

pub fn main() !void {
    const stdout = std.io.getStdOut().writer();
    const p = Point{ .x = 10, .y = 20 };
    try stdout.print("Point: ({}, {})\n", .{ p.x, p.y });
}
```


### 6. 错误处理

Zig 使用错误枚举类型和 try / catch 关键字进行错误处理。

```javascript
const std = @import("std");

const FileError = error{
    FileNotFound,
};

fn readFile(path: []const u8) !void {
    // 模拟一个可能失败的操作
    if (std.mem.eql(u8, path, "invalid")) {
        return FileError.FileNotFound;
    }
    // 其他操作...
}

pub fn main() !void {
    const stdout = std.io.getStdOut().writer();

    readFile("invalid") catch |err| {
        switch (err) {
            FileError.FileNotFound => {
                try stdout.print("Error: File not found\n", .{});
            },
            else => return err,
        }
        return;
    };

    try stdout.print("File read successfully\n", .{});
}
```

代码解析：

- catch |err|：捕获错误并绑定到变量 err。
- switch (err)：对错误类型进行匹配，分别处理不同的错误情形。
- else => return err：对未预期的错误直接向上传播，不静默忽略。
- 如果 readFile 执行成功（没有触发 catch），则继续执行后面的打印语句。


## 复习重点

- 能说明 `Zig 基本语法` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
