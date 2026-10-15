# Dart：Dart 开发环境搭建

- 来源：[Dart 开发环境搭建](https://www.runoob.com/dart/dart-install.html)
- 分类：编程语言
- 技术：Dart
- 笔记类型：学习笔记
- 章节序号：3638

## 本章内容

学习任何编程语言的第一步，都是在本地搭建一个可用的开发环境。

本章将带你安装 Dart SDK、配置编辑器，并运行你的第一个 Dart 程序。


### 在线体验

如果你只是想快速体验 Dart，不想在本地安装任何东西，DartPad 是最省事的选择。

DartPad 是 Dart 官方提供的在线编辑器，无需注册，打开浏览器即可编写和运行代码。

访问地址：https://dartpad.dev


### DartPad 的主要功能

- 在线编写、运行 Dart 代码，实时查看输出
- 内置多个示例程序，适合快速上手
- 支持分享代码链接，方便协作与提问
- 支持 Flutter 代码预览（可以在浏览器里运行简单的 Flutter 界面）


## 安装 Dart SDK

Dart SDK 包含了编译、运行、调试 Dart 程序所需的所有工具。

根据你的操作系统，选择对应的安装方式。


### macOS 安装

如果你使用 macOS，推荐通过 Homebrew 安装：

```text
$ brew tap dart-lang/dart
$ brew install dart
```

安装完成后，验证版本：

```text
$ dart --version
Dart SDK version: 3.5.0 (stable)
```


### Windows 安装

Windows 用户可以通过 Chocolatey 包管理器安装：

```text
C:\> choco install dart-sdk
```

或者直接访问 dart.dev/get-dart 下载安装包，双击运行安装向导。


### Linux 安装

Debian/Ubuntu 系统可以通过 apt 安装：

```text
$ sudo apt-get update
$ sudo apt-get install apt-transport-https
$ wget -qO- https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo gpg --dearmor -o /usr/share/keyrings/dart.gpg
$ echo 'deb [signed-by=/usr/share/keyrings/dart.gpg arch=amd64] https://storage.googleapis.com/download.dartlang.org/linux/debian stable main' | sudo tee /etc/apt/sources.list.d/dart_stable.list
$ sudo apt-get update
$ sudo apt-get install dart
```


### 验证安装

无论使用哪种系统，安装完成后都可以通过以下命令确认 SDK 正常工作：

```text
$ dart --version
$ dart --help
```

如果能看到版本号和帮助信息，说明安装成功。


## 使用 DartPad 在线编辑器

如果你暂时不想安装任何软件，DartPad 是最快的上手方式。

DartPad 是 Google 官方提供的在线 Dart 编辑器，无需注册，打开即用。

访问地址：https://dartpad.dev

DartPad 的特点：

DartPad 非常适合快速验证语法和分享代码片段。但对于完整的项目开发，还是建议配置本地 IDE 环境。


## 配置 VS Code

VS Code 是目前最流行的 Dart 开发编辑器，配合官方插件可以实现极佳的开发体验。


### 安装步骤

第一步，确保已安装 VS Code（可从 code.visualstudio.com 下载）。

第二步，打开 VS Code，进入扩展商店（快捷键 Cmd+Shift+X 或 Ctrl+Shift+X）。

第三步，搜索并安装 Dart 扩展（发布者为 Dart Code）。

安装 Dart 扩展时会自动安装 Flutter 扩展（如果检测到 Flutter SDK）。如果你后续要学习 Flutter，建议同时安装 Flutter 扩展。


### 验证配置

安装完成后，在 VS Code 中新建一个文件，命名为 hello.dart。

输入以下代码，如果看到语法高亮和代码提示，说明配置成功。


## 实例


### 运行代码

在 VS Code 中运行 Dart 代码有三种方式：

```text
$ dart run hello.dart
Hello, RUNOOB!
```


### 其他 IDE 选择


## Dart 项目结构初探

除了单文件运行，Dart 还支持标准化的项目结构。

通过 dart create 命令可以快速创建一个 Dart 项目骨架：

```text
$ dart create my_first_app
```

生成的目录结构如下：

```text
my_first_app/
├── bin/
│   └── my_first_app.dart    # 程序入口文件
├── lib/
│   └── my_first_app.dart    # 库代码（可复用）
├── test/
│   └── my_first_app_test.dart # 测试文件
├── pubspec.yaml              # 项目配置文件（依赖管理）
├── analysis_options.yaml     # 静态分析规则
└── README.md
```

各目录的用途说明：

进入项目目录，运行项目：

```text
$ cd my_first_app
$ dart run
```

```text
Hello world: my_first_app!
```

对于学习基础语法阶段，我们主要使用单文件模式。当你开始写自己的小项目时，再使用 dart create 创建标准项目结构。


## 复习重点

- 能说明 `Dart 开发环境搭建` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
