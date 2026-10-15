# Swift：Swift 环境搭建

- 来源：[Swift 环境搭建](https://www.runoob.com/swift/swift-environment.html)
- 分类：移动开发
- 技术：Swift
- 笔记类型：学习笔记
- 章节序号：3408

## 本章内容

Swift是一门开源的编程语言，该语言用于开发 OS X和 iOS 应用程序。

在正式开发应用程序前，我们需要搭建 Swift 开发环境，以便更好友好的使用各种开发工具和语言进行快速应用开发。由于Swift开发环境需要在 OS X系统中运行，因此其环境的搭建将不同于 Windows 环境，下面就一起来学习一下swift开发环境的搭建方法。

成功搭建swift开发环境的前提：

- 必须拥有一台苹果电脑。因为集成开发环境 XCode 只能运行在 OS X 系统上。
- 电脑系统必须在 OS 10.9.3 及以上。
- 电脑必须安装 Xcode 集成开发环境。


## 安装 Xcode 16

在 macOS 上开发 Apple 平台应用，Xcode 是官方唯一的完整 IDE。

打开 App Store 搜索 Xcode 安装，或者到 developer.apple.com/xcode 下载安装包。

下载完成后，双击下载的 dmg 文件安装，安装完成后我们将 Xcode 图标移动到应用文件夹。

你也可以在 App Store 中搜索 xcode 安装，如下图所示：

Xcode 16 自带的 Swift 编译器是 6.x，支持 Swift 6 语言模式，也向下兼容 Swift 5 模式。

安装完成后第一次启动需要同意许可协议并安装额外组件，这一步会占用几分钟。

验证是否安装成功，在终端执行：

```text
$ swift --version
swift-driver version: 1.148.6 Apple Swift version 6.3.3 (swiftlang-6.3.3.1.3 clang-2100.1.1.101)
Target: arm64-apple-macosx26.0
```

只要能看到 Apple Swift version 和对应的目标平台，就说明工具链已经可用。

注意：Xcode 的命令行工具需要单独激活一次。如果提示找不到 swift 命令，执行 xcode-select --install 安装命令行工具，再执行 sudo xcode-select -s /Applications/Xcode.app 指定路径。


## 第一个 Swift 程序

Xcode 安装完成后，我们就可以开始编写 Swift 代码了。

接下来我们在应用文件夹打开 Xcode，打开后在屏幕顶部选择 File => New => Playground。


## 复习重点

- 能说明 `Swift 环境搭建` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
