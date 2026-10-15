# CMake：CMake 构建实例

- 来源：[CMake 构建实例](https://www.runoob.com/cmake/cmake-build-demo.html)
- 分类：DevOps / 工程化
- 技术：CMake
- 笔记类型：练习笔记
- 章节序号：1743

## 本章内容

本文通过一个完整的 C++ 项目示例，演示如何使用 CMake 从零开始构建一个包含可执行文件和库文件的项目。

示例项目包含一个主程序和一个自定义库，覆盖了 CMake 构建的完整生命周期。


## 项目准备

在开始构建之前，先创建项目文件并了解项目结构。


### 项目结构

示例项目包含一个主程序源文件、一个库源文件和一个库头文件，目录结构如下：

```text
MyProject/
├── CMakeLists.txt          # CMake 配置文件
├── src/
│   ├── main.cpp            # 主程序源文件
│   └── mylib.cpp           # 库源文件
└── include/
    └── mylib.h             # 库头文件
```


### CMakeLists.txt 配置文件

在 MyProject 根目录下创建 CMakeLists.txt 文件，编写以下内容：


## 实例

配置文件中每条指令的作用如下：

每个 add_executable 和 add_library 都定义了一个构建目标（Target）。目标的概念是 CMake 的核心——后续的 target_include_directories、target_link_libraries 等指令都是围绕目标来组织的。


## 构建步骤详解

有了 CMakeLists.txt 之后，按以下六个步骤完成项目的构建和运行。

整体流程概览：


### 创建 CMakeLists.txt 文件

在 MyProject 根目录下创建 CMakeLists.txt 文件，内容已在上一节的配置说明中给出。

这是整个 CMake 构建的起点，所有构建规则都定义在这个文件中。


### 创建构建目录

为了保持源代码目录的整洁，推荐使用 Out-of-source 构建方式——在项目根目录下创建一个独立的构建目录。

打开终端，进入 MyProject 目录：

```text
# 创建构建目录
mkdir build

# 进入构建目录（后续所有操作都在此目录执行）
cd build
```

将 build 目录添加到 .gitignore 文件中，避免将编译产物提交到版本控制系统。


### 配置项目

在构建目录中运行 CMake，生成适合当前平台的构建系统文件（如 Makefile）。

.. 指向包含 CMakeLists.txt 的源代码目录。

```text
# 在 build 目录中运行 CMake 配置
cmake ..
```

CMake 会输出配置结果，显示检测到的编译器和配置状态。如果一切正常，你会看到类似以下输出：

```text
-- The CXX compiler identification is GNU 11.4.0
-- Detecting CXX compiler ABI info - done
-- Configuring done
-- Generating done
-- Build files have been written to: /path/to/MyProject/build
```

如果配置过程中出现错误（如缺少编译器或 CMake 版本过低），CMake 会中止并输出具体错误原因。解决对应问题后重新运行 cmake .. 即可。


### 编译项目

构建文件生成后，使用对应的构建命令编译项目。

默认情况下 CMake 在类 Unix 系统上生成 Makefile，因此可以直接使用 make 命令。

```text
# 在 build 目录中编译项目
make
```

编译完成后，build 目录中会生成可执行文件 MyExecutable 和库文件 libMyLib.a。

你也可以使用跨平台的通用构建命令：

```text
# cmake --build . 会自动调用正确的底层构建工具
cmake --build .
```


### 运行可执行文件

编译成功后，在构建目录中直接运行生成的可执行文件。

```text
# 运行编译生成的可执行文件
./MyExecutable

# 预期输出示例
Hello from RUNOOB! This is MyLib speaking.
```


### 清理构建文件

清理操作会删除编译过程中生成的中间文件（.o 文件等）和目标文件，释放磁盘空间。

使用 make clean 命令：

```text
# 删除编译产生的中间文件和目标文件
make clean
```

手动删除构建目录：

如果没有定义清理规则，可以直接删除整个构建目录。

```text
# 回到项目根目录，删除 build 目录
cd ..
rm -rf build
```

删除整个 build 目录是最彻底的清理方式。下次构建时只需重新执行 mkdir build && cd build && cmake .. && make 即可从头开始。


## 注意事项

确保源文件路径正确。add_executable 和 add_library 中的源文件路径是相对于 CMakeLists.txt 所在目录的。如果路径写错，CMake 配置阶段不会报错，但编译时会提示找不到文件。

目标名称区分大小写。MyLib 和 mylib 是不同的目标。target_link_libraries 中引用的目标名必须与 add_library 定义的目标名完全一致。

修改 CMakeLists.txt 后需要重新配置。如果只修改了源文件，直接 make 即可；但如果修改了 CMakeLists.txt（如添加新文件、更改编译选项），需要重新运行 cmake .. 或直接运行 cmake --build .（它会自动检测配置变更）。

初次使用建议从简单项目开始。先用单个可执行文件跑通整个构建流程，再逐步添加库、外部依赖和自定义编译选项。一次加太多东西会让排查错误变得困难。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `CMake 构建实例` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
