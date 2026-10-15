# CMake：CMake 高级特性

- 来源：[CMake 高级特性](https://www.runoob.com/cmake/cmake-advanced-features.html)
- 分类：DevOps / 工程化
- 技术：CMake
- 笔记类型：学习笔记
- 章节序号：1744

## 本章内容

掌握 CMake 基础之后，高级特性可以帮助你更灵活地管理复杂项目的构建配置。

本文涵盖自定义模块、多配置构建、高级包查找、自定义构建步骤、跨平台交叉编译以及目标属性配置六大主题。

整体内容概览：


## 自定义 CMake 模块和脚本

当多个 CMakeLists.txt 中需要重复同样的逻辑时，将这些逻辑封装成自定义模块可以大幅减少代码冗余。

自定义模块和脚本的本质是将常用的 CMake 函数、宏和配置提取到独立文件中，供多个项目复用。


### 自定义 CMake 模块

自定义模块是一个以 .cmake 为扩展名的文件，其中定义了可被 include 加载的 CMake 函数和宏。

创建步骤：

自定义模块示例——MyModule.cmake：


## 实例

在 CMakeLists.txt 中加载并使用模块：


## 实例

CMAKE_MODULE_PATH 是 CMake 查找模块文件时的搜索路径列表。CMake 会先在内置模块路径中查找，找不到时再到 CMAKE_MODULE_PATH 指定的路径中查找。


### 使用自定义 CMake 脚本

自定义脚本与模块类似，但通常用于执行配置操作而非定义可复用的函数。

脚本可以直接用 include() 加载，CMake 会按顺序执行其中的每一条指令。

创建脚本文件 config.cmake：


## 实例

在 CMakeLists.txt 中调用脚本：

```text
# 使用绝对路径加载脚本
include(${CMAKE_SOURCE_DIR}/config.cmake)
```


## 构建配置和目标

CMake 支持在同一个项目中管理多种构建配置（如 Debug 和 Release），并定义多个构建目标。


### 多配置生成器

不同的 CMake 生成器对配置的处理方式不同。

像 Visual Studio 和 Xcode 这样的多配置生成器允许在同一个构建目录中切换 Debug/Release，而 Unix Makefiles 等单配置生成器需要在配置阶段就确定构建类型。

在 CMakeLists.txt 中设置默认配置：

```text
# 仅对单配置生成器生效，多配置生成器会忽略此变量
set(CMAKE_BUILD_TYPE "Release" CACHE STRING "Build type")
```

CMAKE_BUILD_TYPE 只对单配置生成器有效。如果使用 Visual Studio，请通过 cmake --build . --config Release 或在 IDE 中切换配置。


### 构建目标

一个 CMake 项目中可以定义多个构建目标，每个目标独立配置编译选项和链接依赖。

这让你可以在一次构建中产出多个可执行文件或多个库。


## 实例


## 高级查找和配置

除了基本的 find_package 用法外，CMake 还支持指定组件、精确控制版本和通过配置文件模板传递构建信息。


### find_package 高级用法

COMPONENTS 关键字允许你只查找库中的特定子模块，而非整个包。

这对于像 Boost 这样的大型库非常重要——按需引入可以避免链接不需要的组件。


## 实例

指定搜索路径（适用于非标准安装位置）：

```text
# 方式一：通过变量指定根目录
cmake .. -DBOOST_ROOT=/path/to/custom/boost

# 方式二：在 CMakeLists.txt 中预先设置
set(BOOST_ROOT "/path/to/custom/boost")
find_package(Boost REQUIRED COMPONENTS filesystem)
```


### 配置文件与构建选项

configure_file() 指令可以将 CMake 变量的值注入到代码文件中，实现在编译时传递配置信息。

这在需要将版本号、构建时间等信息编译进程序时非常实用。

创建配置模板文件 config.h.in：


## 实例

在 CMakeLists.txt 中配置并生成头文件：


## 实例

在源文件中使用生成的配置：

```text
// 在 main.cpp 中包含生成的配置文件
#include "config.h"

std::cout << "RUNOOB Version: " << RUNOOB_VERSION << std::endl;
std::cout << "Build Type: " << RUNOOB_BUILD_TYPE << std::endl;
```


## 生成自定义构建步骤

除了标准的编译和链接，CMake 允许你在构建过程中插入自定义操作，例如代码生成、资源复制和构建后通知。


### 自定义命令

add_custom_command() 用于定义一个自定义命令，它会在某个文件需要更新时执行。

这个指令的核心概念是依赖驱动——只有当 OUTPUT 文件不存在或 DEPENDS 文件更新时，命令才会执行。


## 实例

构建阶段触发命令——在链接完成后执行：


## 实例


### 自定义目标

add_custom_target() 定义一个不产生输出文件的构建目标，通常用于将多个自定义命令组织在一起。

除非使用 ALL 关键字，否则自定义目标不会在默认构建中执行，需要显式指定目标名。


## 实例

add_custom_command 和 add_custom_target 的区别：前者定义一个「如何生成文件」的规则，由依赖关系触发；后者定义一个「做什么事」的动作目标，需要显式调用或在 ALL 时自动执行。


## 跨平台和交叉编译

CMake 的核心优势之一就是跨平台支持——同一份 CMakeLists.txt 可以在不同操作系统和架构上生成对应的构建文件。


### 跨平台构建

CMake 会自动检测当前平台的编译器和系统环境，生成匹配的构建文件。

你也可以通过变量显式指定目标平台信息。


## 后续章节

- 交叉编译
- 实例
- 目标属性和配置
- 目标属性
- 实例
- 自定义编译和链接选项
- 实例
- 注意事项

## 复习重点

- 能说明 `CMake 高级特性` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
