# CMake：CMake 基础

- 来源：[CMake 基础](https://www.runoob.com/cmake/cmake-basic.html)
- 分类：DevOps / 工程化
- 技术：CMake
- 笔记类型：学习笔记
- 章节序号：1741

## 本章内容

CMake 是一个跨平台的构建系统生成工具，用于管理 C/C++ 项目的编译过程。

通过编写 CMakeLists.txt 配置文件，你可以定义项目的构建规则、依赖关系和编译选项，CMake 会自动生成对应平台的构建文件（如 Unix 下的 Makefile 或 Windows 下的 Visual Studio 解决方案）。


## CMakeLists.txt 文件

CMakeLists.txt 是 CMake 的核心配置文件，每个 CMake 项目至少需要一个 CMakeLists.txt 文件。

CMake 通过读取文件中的指令来了解项目的结构、源文件列表和编译要求。


### 基本语法

CMakeLists.txt 由一系列 CMake 指令组成，每个指令的格式为：命令名(参数列表)。

下面是构建 CMake 项目时最常用的指令及其实例。

指定 CMake 最低版本：


## 实例

定义项目名称和语言：


## 实例

添加可执行文件：


## 实例

添加库文件：


## 实例

链接库到目标：


## 实例

设置变量：


## 实例

为目标指定头文件路径：


## 实例

设置安装规则：


## 实例

条件语句：


## 实例

自定义命令：


## 实例


### 完整实例

下面是一个完整的 CMakeLists.txt 示例，综合使用了上述多个指令。


## 实例

构建这个项目的典型命令如下：

```text
# 在项目根目录下创建 build 目录（推荐外部构建）
$ mkdir build && cd build

# 生成构建文件
$ cmake ..

# 编译项目
$ cmake --build .

# 安装到系统目录（可选）
$ cmake --install .
```


## 变量和缓存

CMake 使用变量来存储和传递配置信息，变量可以在 CMakeLists.txt 中定义和使用。

变量分为两类：普通变量和缓存变量，它们的作用域和生命周期不同。


### 普通变量

普通变量在 CMakeLists.txt 中定义，作用域为当前目录及其子目录。

普通变量在每次 CMake 运行时重新计算，不会持久化。


## 实例


### 缓存变量

缓存变量存储在 CMakeCache.txt 文件中，在多次 CMake 运行之间保持值不变。

缓存变量通常用于让用户在 CMake 配置阶段自定义构建设置，例如开关功能或指定安装路径。

缓存变量的值会持久化。如果你修改了 CMakeLists.txt 中缓存变量的默认值，需要删除 CMakeCache.txt 或重新运行 cmake 才能让新默认值生效。


## 实例

用户可以通过命令行 -D 参数修改缓存变量：

```text
# 在 cmake 命令中通过 -D 修改缓存变量
$ cmake .. -DMY_INSTALL_PATH=/opt/runoob -DENABLE_LOGGING=OFF
```


## 头文件搜索路径

在 CMake 中，有两种方式可以指定编译器查找头文件的路径：include_directories() 和 target_include_directories()。

了解两者的区别对于编写清晰、可维护的 CMake 项目非常重要。


### include_directories 与 target_include_directories 对比

两者都可以为编译器添加头文件搜索路径，但作用范围和控制粒度不同。


### PUBLIC / PRIVATE / INTERFACE 的含义

target_include_directories() 的关键优势在于可以通过可见性关键字精确控制头文件路径的传播。


## 实例


## 查找库和包

很多项目依赖外部库（如 Boost、OpenCV），CMake 提供了 find_package() 指令来自动检测和配置这些外部依赖。


## 后续章节

- find_package 指令
- 实例
- 使用查找到的库
- 使用第三方库示例
- 实例
- 注意事项

## 复习重点

- 能说明 `CMake 基础` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
