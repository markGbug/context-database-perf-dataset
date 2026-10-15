# CMake：CMake 构建流程

- 来源：[CMake 构建流程](https://www.runoob.com/cmake/cmake-build-flow.html)
- 分类：DevOps / 工程化
- 技术：CMake
- 笔记类型：学习笔记
- 章节序号：1742

## 本章内容

CMake 的构建流程分为几个主要步骤，从创建构建目录到执行编译，再到清理和重新配置。

整个过程围绕 CMakeLists.txt 配置文件展开，CMake 读取配置后生成适合当前平台的构建文件。


## 构建流程概览

一个完整的 CMake 构建流程包含以下五个关键步骤，每一步都有其特定的作用和命令。


## 构建流程详解

下面详细说明每个步骤的具体操作和常用选项。


### 创建构建目录

CMake 推荐使用 Out-of-source（源码外）构建方式，即将构建文件放在源代码目录之外的独立目录中。

这种方式可以保持源代码目录的整洁，同时支持同一份源码配置多个不同的构建方案（如 Debug 和 Release 并存）。

始终使用 Out-of-source 构建方式。直接在源码目录中运行 cmake 会污染项目结构，生成的中间文件难以清理，也不便于切换构建类型。

创建构建目录：

```text
# 在项目根目录下创建 build 目录
mkdir build
```

进入构建目录：

```text
# 切换到构建目录，后续所有 cmake 命令在此执行
cd build
```


### 生成构建文件

在构建目录中运行 CMake，读取源代码目录中的 CMakeLists.txt，生成适合当前平台的构建系统文件。

CMake 支持多种构建系统生成器，如 Unix Makefiles、Ninja、Visual Studio、Xcode 等。

基本用法——生成默认构建文件：

```text
# .. 指向包含 CMakeLists.txt 的源代码目录
cmake ..
```

指定生成器：

使用 -G 参数可以指定要生成的构建系统类型。

```text
# 使用 Ninja 作为构建系统（速度比 Make 更快）
cmake -G "Ninja" ..
```

指定构建类型：

使用 -DCMAKE_BUILD_TYPE 参数设置编译优化级别和调试信息。

```text
# 四种常见的构建类型：Debug / Release / RelWithDebInfo / MinSizeRel
cmake -DCMAKE_BUILD_TYPE=Release ..
```

检查配置结果：

CMake 会输出配置过程中的详细信息，包括检测到的编译器、找到的库、定义的选项等。

如果没有错误，构建系统文件将被生成到当前构建目录中。

如果配置过程中出现错误（如找不到指定的库），CMake 会中止并输出错误信息。解决错误后，重新运行 cmake 命令即可继续。


### 编译和构建

构建文件生成后，就可以执行实际的编译和链接过程了。

不同的构建系统使用不同的编译命令，你也可以使用 CMake 提供的通用构建命令。

推荐方式——使用 CMake 通用构建命令：

```text
# 无论底层使用哪种构建系统，该命令都能正确编译
cmake --build .
```

构建特定目标：

```text
# 只编译指定的目标（如某个可执行文件或库）
cmake --build . --target MyExecutable
```

使用 Makefile 构建系统：

```text
# 编译所有目标
make

# 使用多核并行编译（-j 参数指定并行任务数）
make -j$(nproc)

# 编译特定目标
make MyExecutable
```

使用 Ninja 构建系统：

```text
# Ninja 自动并行编译，无需手动指定 -j
ninja

# 编译特定目标
ninja MyExecutable
```

使用 Visual Studio：

如果生成了 Visual Studio 工程文件，可以打开 .sln 解决方案文件，在 IDE 中选择生成解决方案。

```text
# 也可以使用 MSBuild 命令行工具编译
msbuild MyProject.sln /p:Configuration=Release
```


### 清理构建文件

构建过程中生成的中间文件（.o、.obj 等）和目标文件可以通过清理操作删除，释放磁盘空间。

使用 CMake 通用清理命令：

```text
cmake --build . --target clean
```

使用 Makefile：

```text
make clean
```

使用 Ninja：

```text
ninja clean
```

手动清理：

```text
# 删除构建目录中的所有文件，保留源代码目录不变
rm -rf build/*
```

最简单彻底的清理方式是直接删除整个 build 目录，然后重新创建并运行 cmake。这比单独执行 clean 更可靠，因为 clean 目标可能未正确定义。


### 重新配置和构建

当你修改了 CMakeLists.txt 文件或调整了项目设置后，需要重新运行 CMake 配置并重新编译。

重新配置：

```text
# CMake 会自动检测变更的文件，只重新生成受影响的部分
cmake ..
```

重新编译：

```text
# 编译系统会自动识别哪些源文件发生了变更，只重新编译改动的部分
cmake --build .
```

大多数情况下，修改 CMakeLists.txt 后直接运行 cmake --build . 即可。构建系统会自动检测到 CMakeLists.txt 的变更并重新运行 cmake 配置步骤。


## 构建系统对比

CMake 支持生成多种构建系统文件，以下是三种最常用构建系统的对比。


## 注意事项

始终使用 Out-of-source 构建。在源码目录中运行 cmake 会生成大量中间文件，污染版本控制。将 build 目录添加到 .gitignore 中是最佳实践。

优先使用 cmake --build . 命令。这个命令是跨平台的通用构建入口，无论底层是 Make、Ninja 还是 MSBuild 都能正确工作。在脚本和 CI 环境中尤其推荐使用。

构建类型影响性能和调试体验。Debug 模式包含调试符号且不优化，适合开发；Release 模式启用优化且去除调试信息，适合生产部署。不要用 Debug 模式测试性能，也不要用 Release 模式调试代码。

遇到奇怪的构建错误时，删除 build 目录重来。CMake 的缓存有时会保留过期的配置信息，导致难以排查的错误。删除整个 build 目录并重新 cmake 是最快的排查方式。


## 复习重点

- 能说明 `CMake 构建流程` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
