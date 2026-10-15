# Zig：Zig 环境安装

- 来源：[Zig 环境安装](https://www.runoob.com/zig/zig-setup.html)
- 分类：编程语言
- 技术：Zig
- 笔记类型：练习笔记
- 章节序号：3780

## 本章内容

在配置 Zig 编程语言的开发环境时，需要安装 Zig 编译器并设置相关的开发工具。

以下是在不同操作系统上配置 Zig 的步骤：


## 使用包管理器来安装


### Windows

Zig 在 Chocolatey 上可用：

```text
choco install zig
```

Windows (winget)

```text
winget install zig.zig
```

Windows (scoop)：

```text
scoop install zig
```


### MacOS

Homebrew 安装：

```text
brew install zig
```


### Linux

Ubuntu (snap)

稳定版本安装：

```text
snap install zig --classic --beta
```

Fedora:

```text
dnf install zig
```

FreeBSD:

```text
pkg install lang/zig
```

配置完毕后，你就可以开始使用 Zig 编程语言进行开发了。


## 源码安装

我们也可以下载源码来编译安装。

Zig 源码包下载地址：https://ziglang.org/zh/download/。

下载后，使用 tar 命令来解压：

```text
tar -xvf zig-macos-aarch64-0.13.0.tar.xz
```

然后进入源码包，进行后续的编译安装：

```text
cd zig-macos-aarch64-0.13.0
```

也可以从 Zig 的 GitHub 仓库克隆源码：

```text
git clone https://github.com/ziglang/zig.git
```


### 依赖项

- cmake >= 3.5
- gcc >= 7.0.0 或者 clang >= 6.0.0
- LLVM、Clang、LLD 开发库 == 18.x，使用相同版本的 gcc 或 clang 编译 可以使用系统包管理器安装，或者从源代码构建。


### 指令

- 在 Zig 源码目录下，创建一个 build 目录： mkdir build cd build
- 运行 cmake： cmake ..
- 构建和安装 Zig： make install

请注意 CMAKE_PREFIX_PATH 这个方便的 cmake 变量。CMake 会优先在这个位置查找 LLVM 和其他依赖项。

这些步骤将生成 stage3/bin/zig，这是由 Zig 自身构建的 Zig 编译器。


### macOS + Homebrew

对于 macOS 使用 Homebrew：

- 在 Zig 源码目录下，创建一个 build 目录： mkdir build cd build
- 运行 cmake，并启用静态 LLVM： cmake .. -DZIG_STATIC_LLVM=ON -DCMAKE_PREFIX_PATH="$(brew --prefix llvm@18);$(brew --prefix zstd)"
- 构建和安装 Zig： make install


### FreeBSD

对于 FreeBSD：

- 使用 pkg 安装必要的依赖项： sudo pkg install -qyr FreeBSD devel/llvm18 devel/cmake archivers/zstd textproc/libxml2 archivers/lzma
- 在 Zig 源码目录下，创建一个 build 目录： mkdir build cd build
- 运行 cmake，并启用静态 LLVM： cmake .. -DZIG_STATIC_LLVM=ON -DCMAKE_PREFIX_PATH="/usr/local/llvm18;/usr/local"
- 构建和安装 Zig： make install

这些步骤会在你的系统上安装 Zig 编译器。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Zig 环境安装` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
