# Swift：Swift Package Manager（包管理）

- 来源：[Swift 包管理](https://www.runoob.com/swift/swift-package-manager.html)
- 分类：移动开发
- 技术：Swift
- 笔记类型：学习笔记
- 章节序号：3449

## 本章内容

Swift Package Manager（简称 SwiftPM 或 SPM）是 Swift 官方的依赖管理与构建工具。

它负责三件事：描述一个包由哪些代码组成、从远端拉取依赖、把代码编译成库或可执行文件。

它已经集成进 Swift 工具链和 Xcode，不需要额外安装，是当前管理 Swift 项目依赖的首选方式。


## SwiftPM 的核心概念

在动手之前，先把几个术语对应到实际的目录和文件上。

最容易混淆的是「目标」和「产品」：目标是内部怎么组织代码，产品是外部能用什么。

一个目标可以不出现在任何产品里（纯内部实现），一个产品也可以由多个目标组成。


## 创建一个包

SwiftPM 自带脚手架命令，可以直接生成标准目录结构。

```text
$ swift package init --type executable --name RunoobCLI
Creating executable package: RunoobCLI
Creating Package.swift
Creating .gitignore
Creating Sources
Creating Sources/RunoobCLI/RunoobCLI.swift
Creating Tests/
Creating Tests/RunoobCLITests/
Creating Tests/RunoobCLITests/RunoobCLITests.swift
```

生成的结构非常固定，源文件放在 Sources 下，测试放在 Tests 下。

```text
RunoobCLI/
├── Package.swift
├── Sources/
│   └── RunoobCLI/
│       └── RunoobCLI.swift
└── Tests/
    └── RunoobCLITests/
        └── RunoobCLITests.swift
```

--type 支持多种模板，最常用的是 library、executable 和 empty，分别对应库、可执行程序和空包。

此外还有 tool（带命令行参数解析的可执行程序）、macro（宏包）、build-tool-plugin 等模板。

不指定名字时，SwiftPM 会使用当前目录名作为包名。


## Package.swift 结构

清单文件本身就是一个 Swift 源文件，用 PackageDescription 提供的类型来描述包。

第一行的 swift-tools-version 是必须的，它决定清单文件能用哪些 API。


## 实例

常用参数的含义如下。

注意：不声明 platforms 时，SwiftPM 会按工具链支持的最低系统版本编译。如果代码里用到了较新的 API（例如 Synchronization 模块），一定要显式声明 platforms，否则会收到「API 在更低系统版本上不可用」的报错。


## 库目标与可执行目标

库目标用 .target 声明，里面放可复用的代码，不能有顶层可执行语句。

可执行目标用 .executableTarget 声明，必须提供 main 入口，可以用 @main 标注，也可以把文件命名为 main.swift。

两个目标之间的依赖通过 dependencies 参数声明，写的是目标名。


## 实例


## 实例

可执行目标导入了库目标，就能直接使用 RunoobSite。

注意库目标里的类型和成员都写了 public，否则跨模块不可见，这是 SwiftPM 多目标项目最常见的报错来源。


## 依赖管理与版本约束

在 dependencies 数组里用 .package 声明依赖，版本约束的写法有多种。

下面是一个同时使用远端依赖和本地依赖的例子。


## 实例

依赖解析的结果会写进 Package.resolved 文件，它记录了每个依赖被解析到的确切版本。

这个文件应该提交到版本库，这样团队里所有人以及 CI 都能拿到完全一致的依赖版本。


## 常用命令

日常开发中真正高频的只有少数几个命令。

下面是前面那个包的真实构建输出，其中省略了部分编译进度行，以及因机器而异的耗时数字。

```text
$ swift build
Building for debugging...
[5/9] Emitting module RunoobCore
[6/9] Compiling RunoobCore RunoobCore.swift
[7/11] Compiling RunoobCLI RunoobCLI.swift
[9/11] Linking RunoobCLI
Build complete!
```

运行可执行目标时，如果代码有改动会先自动编译。

```text
$ swift run RunoobCLI
Build of product 'RunoobCLI' complete!
RUNOOB (www.runoob.com)
```

swift package describe 适合用来确认依赖和目标的解析结果，尤其是依赖没被正确引用时。

```text
$ swift package describe
Name: RunoobKit
Path: /Users/runoob/RunoobKit
Tools version: 6.0
Dependencies:
Platforms:
    Name: macos
    Version: 14.0

Products:
    Name: RunoobCore
    Type:
        Library:
            automatic
    Targets:
        RunoobCore

    Name: RunoobCLI
    Type:
        Executable: nil
    Targets:
        RunoobCLI

Targets:
    Name: RunoobCore
    Type: library
    Path: Sources/RunoobCore
```

测试目标用 swift test 运行，输出中会逐个列出用例的通过或失败情况。


## 实例

这里用的是 Swift 官方新的 Testing 框架，Xcode 16 与新版工具链都自带，不再需要 XCTest。


## 与 Xcode 集成

Xcode 对 SwiftPM 是一等公民支持，几种用法都很直接。

双击 Package.swift，或者用 File > Open 打开包所在目录，Xcode 会把它当成一个工程，自动列出每个可执行目标对应的 scheme。

在已有的 App 工程里，用 File > Add Package Dependencies 可以直接按仓库地址添加依赖，Xcode 会帮你把版本约束写进工程配置。

添加后，Xcode 会把远端依赖缓存到本地，之后离线也能构建。

提示：在 Xcode 里编辑 Package.swift 时，如果改了目标结构但左侧列表没更新，用 File > Packages > Reset Package Caches 重置一次即可。


## 常见问题


### 库目标里的类型为什么在别的目标里用不了

检查是否漏写了 public。

每个目标都是独立模块，默认的 internal 级别只在模块内可见，跨目标必须提升到 public 或 open。


### swift-tools-version 应该写多少

写你的工具链支持的最低版本即可，它决定了清单文件能用的 API。

写得太高，旧工具链无法打开这个包；写得太低，用不了新参数。


### Package.resolved 要提交到版本库吗

对于可执行程序和 App，应该提交，用来保证所有人的依赖版本一致。

对于被广泛依赖的库，一般也建议提交，避免解析结果在不同环境漂移。


### 为什么 swift run 找不到我的目标

确认目标是用 .executableTarget 声明的，并且名字拼写一致。

只声明了 .target 的库目标不能被 swift run 运行。


### 本地路径依赖和远端依赖可以混用吗

可以，两者都写在 dependencies 数组里。

本地路径依赖常用于多包协同开发，发布前再换成带版本号的远端依赖。


## 复习重点

- 能说明 `Swift 包管理` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
