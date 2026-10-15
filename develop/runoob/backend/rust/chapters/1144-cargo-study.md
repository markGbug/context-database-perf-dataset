# Rust：Cargo 教程

- 来源：[Cargo 教程](https://www.runoob.com/rust/cargo-tutorial.html)
- 分类：后端开发
- 技术：Rust
- 笔记类型：学习笔记
- 章节序号：1144

## 本章内容

在 Rust 开发中，几乎所有的项目都是使用 Cargo 来进行管理和构建的，因为它提供了便捷的工作流程和强大的功能，使得 Rust 开发变得更加高效和可靠。


### Cargo 是什么

Cargo 是 Rust 的官方构建系统和包管理器。它主要有两个作用：

主要有两个作用：

- 项目管理：Cargo 用于创建、构建和管理 Rust 项目。通过 Cargo，你可以轻松地创建新项目，管理项目的依赖关系，并执行项目的构建、运行和测试等操作。
- 包管理器：Cargo 还充当了 Rust 的包管理器。它允许开发者在项目中引入和管理依赖项（如第三方库），并确保这些依赖项的版本管理和兼容性。

Cargo 主要特性和功能：

- 依赖管理：Cargo 通过 Cargo.toml 文件管理项目的依赖，这个文件列出了项目所需的所有外部库以及它们的版本。
- 构建系统：Cargo 使用 Rust 编译器（rustc）来构建项目，它会自动处理依赖的编译和链接。
- 包注册表：Cargo 与 crates.io 这个 Rust 社区的包注册表交互，允许开发者搜索、添加和管理第三方库。
- 构建配置：通过 Cargo.toml 和 Cargo.lock 文件，Cargo 允许开发者配置构建选项，如编译器选项、特性（features）和目标平台。
- 项目模板：Cargo 提供了创建新项目的模板，可以通过 cargo new 命令快速启动新项目。
- 测试：Cargo 提供了一个简单的命令 cargo test 来运行项目的单元测试。
- 基准测试：Cargo 支持使用 cargo bench 命令进行基准测试。
- 发布：通过 cargo publish 命令，开发者可以将他们的库发布到 crates.io 上，供其他开发者使用。
- 自定义构建脚本：Cargo 允许使用自定义的构建脚本来处理更复杂的构建需求。
- 多目标项目：Cargo 支持在一个项目中定义多个目标，如可执行文件、库、测试和基准测试。
- 跨平台构建：Cargo 支持跨多个平台构建 Rust 程序，包括 Windows、macOS、Linux 以及各种嵌入式系统。
- 构建缓存：为了加快构建速度，Cargo 使用构建缓存来存储编译后的依赖。
- 离线工作：Cargo 支持在没有互联网连接的情况下工作，它会自动使用本地缓存的依赖。
- 插件系统：Cargo 允许开发者编写插件来扩展其功能。
- 环境变量：Cargo 支持通过环境变量来覆盖默认的构建和运行行为。


### Cargo 功能

Cargo 除了创建工程以外还具备构建（build）工程、运行（run）工程等一系列功能，构建和运行分别对应以下命令：

- cargo new <project-name>：创建一个新的 Rust 项目。
- cargo build：编译当前项目。
- cargo run：编译并运行当前项目。
- cargo check：检查当前项目的语法和类型错误。
- cargo test：运行当前项目的单元测试。
- cargo update：更新 Cargo.toml 中指定的依赖项到最新版本。
- cargo --help：查看 Cargo 的帮助信息。
- cargo publish：将 Rust 项目发布到 crates.io。
- cargo clean：清理构建过程中生成的临时文件和目录。


### 在 VSCode 中配置 Rust 工程

Cargo 是一个不错的构建工具，如果使 VSCode 与它相配合那么 VSCode 将会是一个十分便捷的开发环境。


## 复习重点

- 能说明 `Cargo 教程` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
