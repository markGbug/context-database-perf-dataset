# Go：Go 简介

- 来源：[Go 简介](https://www.runoob.com/go/go-intro.html)
- 分类：后端开发
- 技术：Go
- 笔记类型：练习笔记
- 章节序号：0845

## 本章内容

Go（又称 Golang）是 Google 开发的一种开源编程语言，设计目标是让开发者能够高效地构建简单、可靠且高性能的软件。

Go 语言诞生于 2007 年，由 Google 的三位资深工程师——Robert Griesemer、Rob Pike 和 Ken Thompson 联合设计，并于 2009 年正式开源发布。

Go 的设计初衷是解决 Google 内部面临的大规模软件开发痛点：C++ 编译太慢、Java 运行时太臃肿、脚本语言性能不足。三位设计者希望创造一门兼具编译型语言的性能和动态语言的开发效率的编程语言。

Go 语言吉祥物是一只名为 Gopher 的土拨鼠，象征着 Go 社区的务实与活力。

Go 语言的关键设计目标可以归纳为以下几点：


### Go 诞生要解决的三个核心问题


### Go 的核心设计哲学

Go 的官方口号是 Simple, Fast, Reliable，这三个词概括了它全部的设计取舍。

Go 刻意保持语言规范的精简。整个语言规范只有约 60 页，关键字仅有 25 个（相比之下 C++ 有 80+ 个关键字），这意味着一个有经验的开发者在一两天内就能掌握语法全貌，之后将精力集中在业务逻辑上。


## Go 语言的发展历史

Go 语言的发展历程并非一蹴而就，下面梳理了从立项到如今的关键时间节点。

Go 1.0 发布时，核心团队做出了一个重大承诺：后续所有 1.x 版本的 Go 均保持向后兼容。这意味着十年前编写的 Go 代码，在今天的最新编译器中依然可以直接编译运行。


## Go 语言的核心特性

Go 的设计哲学决定了它的特性集合——精简而强大。以下逐一拆解 Go 最核心的语言特性。


### 原生并发：Goroutine 与 Channel

并发是 Go 语言最引人注目的特性。Goroutine 是一种比操作系统线程轻量得多的执行单元——每个 Goroutine 的初始栈大小仅为约 2 KB，而操作系统线程通常在 1 MB 以上。

你可以在一台普通机器上同时运行数十万个 Goroutine，这是传统线程模型无法做到的。

Channel（通道）是 Goroutine 之间的通信管道，遵循 Go 的并发哲学：

不要通过共享内存来通信，而要通过通信来共享内存。（Don't communicate by sharing memory; share memory by communicating.）

一个简单的 Goroutine 与 Channel 示例：


## 实例


### 静态类型与类型推断

Go 是静态类型语言，所有变量类型在编译时即确定。但与 C/Java 不同的是，Go 支持类型推断——编译器可以自动推导变量类型，开发者无需反复声明类型名。

这种设计在保持类型安全的同时，让代码写起来像动态语言一样简洁。


## 实例


### 快速编译

Go 的编译速度极快，大型项目（几十万行代码）也能在几秒内完成编译。

这得益于 Go 精心设计的依赖分析机制：只编译实际被引用的包，且消除了 C/C++ 中头文件重复解析的开销。


### 内置垃圾回收（GC）

Go 使用并发三色标记-清扫算法实现自动垃圾回收。GC 与用户代码并发执行，暂停时间通常在微秒级别，不会对服务响应时间产生明显影响。

开发者无需手动管理内存，同时又能获得接近 C 语言的运行时性能。


### 丰富的标准库

Go 的标准库覆盖了现代开发的大部分需求，无需引入第三方依赖即可完成常见任务。下表列出了最常用的标准库包：


### 跨平台编译

Go 编译器支持交叉编译，在任意平台上编译出其他目标平台的可执行文件。只需设置 GOOS 和 GOARCH 两个环境变量即可。

```text
# 在 macOS 上编译 Linux 可执行文件
$ GOOS=linux GOARCH=amd64 go build -o app-linux main.go

# 在 Linux 上编译 Windows 可执行文件
$ GOOS=windows GOARCH=amd64 go build -o app.exe main.go
```

编译产物是独立的二进制文件，目标机器无需安装 Go 运行时或任何依赖，直接运行即可。


## Go 语言的应用领域

Go 凭借高性能、易部署和原生并发的优势，在以下领域得到了广泛采用。


### 云原生与基础设施

Go 是现代云原生技术栈的事实标准语言。几乎所有知名的云原生项目均使用 Go 编写。


### 微服务与 API 开发

Go 凭借极低的内存占用和出色的并发处理能力，成为构建微服务的理想选择。一个简单的 HTTP 服务仅需几 MB 内存即可运行。

常用的 Go Web 框架包括 Gin、Echo、Fiber 等，它们在性能基准测试中通常大幅领先其他语言的同类框架。


### CLI 工具开发

Go 编译为单个二进制文件的特性，使其成为 CLI 工具开发的首选。用户无需安装任何运行时，下载一个文件即可使用。

知名项目包括：Hugo（静态网站生成器）、fzf（模糊搜索工具）、gh（GitHub CLI）和 kubectl（Kubernetes 命令行工具）。


### 网络编程与分布式系统

Go 标准库中的 net 包提供了完善的网络编程支持，goroutine 模型天然适配高并发网络服务（如代理服务器、消息队列、游戏服务器）。gRPC 框架的 Go 实现也是分布式系统中服务间通信的主流方案。


### 区块链

Go 在区块链领域也有重要应用。go-ethereum（Geth） 是以太坊最主流的客户端实现，Hyperledger Fabric 的核心组件也使用 Go 编写。


### AI 与机器学习（新兴领域）

虽然 Python 仍是 AI/ML 领域的主导语言，但 Go 正逐步进入这一领域。Ollama（本地大模型运行工具）和 LangChainGo 等项目的兴起，展示了 Go 在 AI 基础设施和 LLM 应用开发中的潜力。


## 快速开始

从零搭建 Go 开发环境只需三步：安装、配置、写代码。


### 安装 Go

访问 go.dev/dl 下载对应平台的安装包。macOS 用户也可通过 Homebrew 安装。

```text
# macOS (Homebrew)
$ brew install go

# 验证安装
$ go version
go version go1.24.0 darwin/arm64
```


### 第一个 Go 程序

创建项目目录并编写经典的 Hello World 程序。


## 实例

运行方式有两种：直接执行（不产生二进制文件）或编译后执行。

```text
# 方式一：直接运行（开发调试时常用）
$ go run main.go
Hello, RUNOOB!
欢迎来到 Go 语言的世界

# 方式二：编译为二进制文件后执行（生产部署时常用）
$ go build -o hello main.go
$ ./hello
Hello, RUNOOB!
欢迎来到 Go 语言的世界
```


### Go Modules 初始化

对于正式项目，建议使用 Go Modules 管理依赖。模块名通常使用仓库路径（如 GitHub 地址），以便他人引用。

```text
# 初始化 Go Module
$ mkdir my-go-project && cd my-go-project
$ go mod init github.com/runoob/my-go-project
go: creating new go.mod: module github.com/runoob/my-go-project

# go.mod 文件内容
module github.com/runoob/my-go-project

go 1.24
```


## 后续章节

- 基础语法概览
- 变量与常量
- 实例
- 控制流程
- 实例
- 函数
- 实例
- 结构体与方法
- 实例
- 接口
- 实例
- 常用示例
- 构建 HTTP 服务器
- 实例
- 并发 Worker 池
- 实例

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Go 简介` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
