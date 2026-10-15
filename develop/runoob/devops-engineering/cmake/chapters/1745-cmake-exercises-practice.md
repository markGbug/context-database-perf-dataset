# CMake：CMake 实战练习

- 来源：[CMake 实战练习](https://www.runoob.com/cmake/cmake-exercises.html)
- 分类：DevOps / 工程化
- 技术：CMake
- 笔记类型：练习笔记
- 章节序号：1745

## 本章内容

本文将演示如何使用 CMake 管理一个中等复杂度的 C++ 项目，从创建项目到编译和运行的完整流程。

内容涵盖基本配置、库链接、单元测试、自定义命令以及跨平台交叉编译等高级特性。


## CMake 构建流程

下图展示了 CMake 从源码到最终可执行文件的完整构建流程：


## 项目概述

我们将构建一个包含主程序、静态库和单元测试的 C++ 项目。

库中提供数学运算功能（加法、减法、乘法），主程序调用这些功能，测试代码验证其正确性。


### 项目目录结构

```text
MyProject/
├── CMakeLists.txt          # 根构建配置（项目定义、全局设置）
├── src/
│   ├── main.cpp            # 主程序入口
│   ├── CMakeLists.txt      # src 子目录构建配置（库 + 可执行文件）
│   ├── lib/
│   │   ├── module1.cpp     # 数学模块一：加法、减法
│   │   └── module2.cpp     # 数学模块二：乘法
│   └── include/
│       └── mylib.h         # 公共头文件（函数声明）
└── tests/
    ├── test_main.cpp       # 单元测试用例
    └── CMakeLists.txt      # 测试子目录构建配置
```

Out-of-Source Build（源外构建）是 CMake 的最佳实践：所有构建产物（Makefile、目标文件、可执行文件）都放在独立的 build 目录中，不会污染源码目录。


## 创建 CMakeLists.txt 文件

CMakeLists.txt 是 CMake 的核心配置文件，采用层级结构，根目录和每个子目录各有一个。


### 根目录 CMakeLists.txt

根配置定义项目级信息，并通过 add_subdirectory 管理子目录。


## 实例


### src 目录 CMakeLists.txt

此文件定义库目标（MyLib）和可执行文件目标（MyExecutable），并建立依赖关系。


## 实例

PRIVATE 和 PUBLIC 的区别：PRIVATE 表示依赖仅当前目标需要，PUBLIC 表示依赖会传递给链接了当前目标的其他目标。


### tests 目录 CMakeLists.txt

测试配置使用 Google Test 框架，需要先查找并引入 GTest 包。


## 实例


### 自定义目标（add_custom_target）

自定义目标是一个独立的目标，不产生输出文件，用于执行特定任务。


## 实例

运行自定义目标：

```text
# 在 build 目录下执行
make run
# 或
cmake --build . --target run
```

自定义命令和自定义目标的区别：add_custom_command 附着在某个目标上，在目标构建的特定阶段触发；add_custom_target 是一个独立的目标，需要显式指定才会执行。


## 跨平台和交叉编译

CMake 的核心优势之一就是跨平台支持，可以轻松切换目标平台和架构。


### 指定目标平台

通过 CMAKE_SYSTEM_NAME 变量可以指定目标平台。

```text
# 为 Linux 平台交叉编译
cmake -DCMAKE_SYSTEM_NAME=Linux ..

# 为 Windows 平台交叉编译
cmake -DCMAKE_SYSTEM_NAME=Windows ..
```


### 使用工具链文件

对于复杂的交叉编译场景，推荐使用工具链文件集中管理所有平台相关配置。

首先创建工具链文件 toolchain.cmake：


## 实例

使用工具链文件进行构建：

```text
# 在 build 目录下执行
cmake -DCMAKE_TOOLCHAIN_FILE=../toolchain.cmake ..
cmake --build .
```

工具链文件将平台相关的编译器、链接器、库路径等配置集中管理，使得切换目标平台只需指定不同的工具链文件，无需修改 CMakeLists.txt。


## 构建类型与常用选项

CMake 支持多种构建类型，通过 CMAKE_BUILD_TYPE 变量控制。

指定构建类型：

```text
# Debug 构建
cmake -DCMAKE_BUILD_TYPE=Debug ..

# Release 构建
cmake -DCMAKE_BUILD_TYPE=Release ..
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `CMake 实战练习` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
