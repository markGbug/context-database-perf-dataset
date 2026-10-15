# Rust：Rust 简介

- 来源：[Rust 简介](https://www.runoob.com/rust/rust-intro.html)
- 分类：后端开发
- 技术：Rust
- 笔记类型：学习笔记
- 章节序号：1142

## 本章内容

Rust 是一门由 Mozilla Research 主导开发的系统级编程语言，以内存安全、零成本抽象和无畏并发为核心设计目标。

Rust 诞生于 2006 年，最初是 Mozilla 员工 Graydon Hoare 的个人项目，后于 2009 年由 Mozilla 正式赞助并组建团队开发。

Rust 的设计初衷是解决 C/C++ 在系统编程中长期存在的痛点：内存安全问题（空指针、悬垂指针、缓冲区溢出）和并发编程的复杂性（数据竞争、死锁）。

Rust 的设计哲学是「在编译期消灭 bug」——通过强大的类型系统和所有权机制，让编译器帮你检查出内存错误和数据竞争，而不是等到运行时才发现问题。

Rust 语言吉祥物是一只名叫 Ferris 的螃蟹，亲切可爱，代表 Rust 社区友好、包容的文化。

Rust 的关键设计目标可以归纳为以下几点：


## Rust 语言的发展历史

Rust 从个人项目到全球广泛采用的系统语言，走过了近二十年的发展历程。

2021 年 Rust 基金会的成立是一个里程碑事件。AWS、Google、华为、微软和 Mozilla 五家科技巨头共同承诺保障 Rust 的长期独立发展，消除了社区对「单一公司主导」的担忧。

Rust 采用六周一个稳定版本的发布节奏，同时通过Edition机制（每 3 年左右发布一次）处理不兼容的语言变更。同一个项目可以混合使用不同 Edition 的 crate，编译器保证向后兼容。


## Rust 语言的核心特性

Rust 的特性集合围绕「安全、高效、实用」三个维度展开。以下逐一拆解 Rust 最核心的语言特性。


### 所有权系统（Ownership）

所有权是 Rust 最独特、最重要的特性。它在编译期管理内存，无需垃圾回收器，也无需手动 malloc/free。

所有权有三大规则：

代码层面的直观感受：当变量被赋值给另一个变量时，所有权发生转移（move），原变量失效。


## 实例

所有权系统是 Rust 学习曲线的「陡坡」。初学者常常与编译器「战斗」，但一旦理解，你会发现那些被编译器拦截的错误，在 C/C++ 中可能就是致命的运行时 bug。


### 模式匹配（Pattern Matching）

Rust 的 match 表达式极其强大，编译器会穷尽性检查所有情况，确保不会遗漏任何分支。


## 实例


### 枚举与 Option/Result

Rust 的枚举（enum）可以携带数据，配合 match 使用能实现安全且表达力强大的控制流。

标准库中的 Option<T> 和 Result<T, E> 是两个最核心的枚举类型，分别处理「可能为空」和「可能出错」的场景——Rust 没有 null 和异常。


## 实例

Rust 没有 null 值，也没有 try-catch 异常机制。Option 和 Result 是编译期强制处理的——如果你忘记检查，代码无法通过编译。这从根本上消灭了空指针异常和未捕获异常。


### 零成本抽象

Rust 的高阶特性（迭代器、闭包、泛型）在编译后与手写的底层循环完全等价，不产生额外运行时开销。

这意味着你可以用类似函数式的风格写代码，同时获得和 C 一样的高性能。


## 实例


### 无畏并发（Fearless Concurrency）

Rust 的类型系统和所有权规则在编译期杜绝数据竞争。Send 和 Sync trait 自动标记类型是否可以安全地在线程间传递或共享。

如果你试图在多线程中共享非线程安全的数据，编译器会直接报错——而不是等到线上运行时才出现诡异的并发 bug。


## 实例


### Cargo：一体化的构建工具

Cargo 是 Rust 的官方包管理器和构建系统，集成了依赖管理、编译、测试、文档生成和发布功能。

对比 C/C++ 生态中需要手动配置 CMake/Makefile 和包管理器的分散体验，Cargo 提供了「开箱即用」的一体化体验。

cargo check 是开发中非常有用的命令。它只检查语法和类型，不生成可执行文件，速度比 cargo build 快很多。大多数 IDE 的 Rust 插件在保存文件时都会自动执行 cargo check。


## Rust 语言的应用领域

Rust 凭借内存安全和高性能的优势，正在多个领域迅速扩展。


### 系统编程与高性能服务端

这是 Rust 的「主场」——适合需要极致性能且对内存安全有高要求的场景。异步运行时 Tokio 和 Web 框架 Actix Web、Axum 在高并发场景中表现卓越。


### WebAssembly

Rust 是编译到 WebAssembly 的最佳语言之一。它的零成本抽象和无 GC 特性让 Wasm 产物体积小、性能高。

前端框架 Yew 和 Leptos 允许用 Rust 编写 SPA 应用。Figma、Cloudflare Workers 等都在生产环境中重度使用 Rust + Wasm。


### 嵌入式与 IoT

Rust 的 no_std 模式允许在没有操作系统的裸机上运行，适合 MCU、传感器等资源受限设备。

RTIC（实时中断驱动并发框架）和 Embassy（异步嵌入式框架）是嵌入式 Rust 的代表项目。


### CLI 工具

Rust 编译为独立二进制文件且性能优异，造就了大量明星 CLI 工具：


### 区块链与 Web3

Rust 在区块链领域有重要地位。Solana 链的核心用 Rust 编写，Sui、Aptos、Polkadot（Substrate） 等新公链也均以 Rust 为主要开发语言。


### 数据库与数据基础设施

高性能数据库和数据处理系统是 Rust 的优势领域：TiKV（分布式 KV 存储，TiDB 的存储层）、SurrealDB、Polars（DataFrame 库）、Databend（云数据仓库）等均使用 Rust 构建。


### 操作系统与基础设施

Rust 已进入 Linux 内核（6.1+），Google 在 Android 中使用 Rust 重写蓝牙和 Wi-Fi 栈，微软也在 Windows 内核中使用 Rust 重写部分组件。

业余项目方面，Redox OS 是一个完全用 Rust 从头编写的类 Unix 操作系统。


## 快速开始

Rust 官方提供了极其方便的安装工具 rustup，一条命令搞定编译器、包管理器和文档。


### 安装 Rust

```text
# Unix/macOS
$ curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

# 验证安装
$ rustc --version
rustc 1.85.0 (4d91de4e4 2025-02-17)

$ cargo --version
cargo 1.85.0
```


### 第一个 Rust 程序

使用 Cargo 创建项目是最推荐的方式，它会自动生成标准的项目结构。

```text
# 创建新项目
$ cargo new hello_runoob
     Created binary (application) `hello_runoob` package

# 项目结构
hello_runoob/
├── Cargo.toml     # 项目元数据和依赖配置
└── src/
    └── main.rs    # 程序入口文件
```

Cargo.toml 是项目的配置文件，类似于 Node.js 的 package.json：


## 后续章节

- 实例
- 实例
- 基础语法概览
- 变量与可变性
- 实例
- 基本数据类型
- 控制流程
- 实例
- 函数
- 实例
- 结构体与 impl 块
- 实例
- 常用示例
- 构建 HTTP API 服务
- 实例
- 文件批量处理工具

## 复习重点

- 能说明 `Rust 简介` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
