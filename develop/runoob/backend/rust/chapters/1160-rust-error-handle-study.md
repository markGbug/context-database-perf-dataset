# Rust：Rust 错误处理

- 来源：[Rust 错误处理](https://www.runoob.com/rust/rust-error-handle.html)
- 分类：后端开发
- 技术：Rust
- 笔记类型：学习笔记
- 章节序号：1160

## 本章内容

Rust 采用了一种独特的错误处理机制，没有异常（Exception），没有 try/catch。它将错误分为两类，用不同的方式处理：

- 不可恢复错误（Unrecoverable）：程序逻辑出了严重问题，使用 panic! 宏终止程序
- 可恢复错误（Recoverable）：操作可能失败但可以处理，使用 Result<T, E> 枚举

这种设计迫使开发者在编译期就处理可能的错误，而不是在运行时才发现遗漏。


## 1. 不可恢复错误：panic!

panic! 宏用于表示程序遇到了无法继续执行的严重错误。调用时会：

- 打印错误信息和发生位置
- 展开（unwind）调用栈并清理资源
- 终止程序


## 实例

运行结果：

```text
thread 'main' panicked at '发生了严重错误', src/main.rs:2:5
note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace.
```

输出的两行信息：

- 第一行：panic 的位置（文件名和行号）以及错误信息
- 第二行：提示如何查看完整的调用栈回溯


### 查看调用栈回溯（Backtrace）

设置 RUST_BACKTRACE=1 环境变量可以看到完整的调用栈，帮助定位 panic 的根源：

```text
# Linux / macOS
RUST_BACKTRACE=1 cargo run

# Windows PowerShell
$env:RUST_BACKTRACE=1; cargo run
```

回溯输出会列出从 panic 发生位置到 main 函数的完整调用链。当 panic 发生在深层调用中时，这个信息非常有用。

何时使用 panic!：代码中出现了不应该发生的逻辑错误（bug），比如访问越界、解引用空指针、违反了不可变的契约。对于外部输入导致的可预期错误，应使用 Result。


## 2. 可恢复错误：Result<T, E>

Result 是 Rust 标准库中用于表示可能失败的操作的枚举：

```html
enum Result<T, E> {
    Ok(T),    // 操作成功，包含结果值
    Err(E),   // 操作失败，包含错误信息
}
```

Rust 标准库中所有可能失败的函数都返回 Result。例如打开文件：


### 2.1 使用 match 处理 Result


## 实例


### 2.2 使用 if let 简化处理

当你只关心成功的情况时，if let 比 match 更简洁：


## 实例


### 2.3 unwrap 和 expect：快速但危险

如果你确定操作不会失败（或在原型阶段不想处理错误），可以用这两个快捷方法：


## 实例

建议：生产代码中优先使用 expect 而非 unwrap，因为自定义的错误信息能让你在 panic 时快速定位问题。更好的做法是使用 ? 运算符将错误传播给调用者。


## 3. 错误传播：? 运算符

在实际开发中，函数遇到错误时往往不想自己处理，而是将错误传播给调用者。Rust 提供了 ? 运算符来简化这一操作。


### 3.1 手动传播 vs ? 运算符

先看手动传播的写法——冗长但清晰：


## 实例

使用 ? 运算符，同样的逻辑可以简化为：


## 实例

还可以链式调用，进一步简化：

```html
fn read_file(path: &str) -> Result<String, io::Error> {
    let mut content = String::new();
    File::open(path)?.read_to_string(&mut content)?;
    Ok(content)
}
```

? 运算符的工作原理：

重要限制：? 运算符只能用在返回 Result（或 Option）的函数中。从 Rust 1.39 起，main 函数也可以返回 Result。


### 3.2 在 main 中使用 ?

默认的 main 函数返回 ()，不能使用 ?。但可以让 main 返回 Result：


## 实例


## 4. 自定义错误类型与分类处理

在实际项目中，你通常需要根据不同的错误类型做不同的处理。Rust 通过 kind() 方法实现这一点：


## 实例

运行结果（当文件不存在时）：

```text
文件不存在，请检查路径
```

io::ErrorKind 常用的变体：


## 5. 自定义错误类型

在项目中，你通常需要定义自己的错误类型来表示业务逻辑中的错误：


## 实例

第三方库推荐：在实际项目中，可以使用 thiserror 库自动派生 Display 和 From 实现，大幅减少样板代码。对于应用层代码，anyhow 库提供了便捷的 anyhow::Result 类型，适合快速开发。


## 6. Option<T>：值可能不存在

除了 Result，Rust 还有另一个重要的枚举用于处理"可能没有值"的情况——Option<T>：

```html
enum Option<T> {
    Some(T),  // 有值
    None,     // 没有值
}
```

Option 用于替代其他语言中的 null。Rust 中没有 null，任何可能为空的值都必须用 Option 包装：


## 实例

Option 与 Result 的对比：


## 小结

Rust 的错误处理哲学：错误是类型系统的一部分，而不是控制流的例外。编译器会强制你处理每一种可能的错误情况，这让你的程序在运行时更加可靠。


## 复习重点

- 能说明 `Rust 错误处理` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
