# Kotlin：Kotlin 命令行编译与 REPL

- 来源：[Kotlin 使用命令行编译](https://www.runoob.com/kotlin/kotlin-command-line.html)
- 分类：移动开发
- 技术：Kotlin
- 笔记类型：学习笔记
- 章节序号：3367

## 本章内容

不装 IDE 也能写 Kotlin，官方提供的 kotlinc 编译器足以完成编译、打包和运行。

本文介绍 kotlinc 的安装、常用参数、交互式 REPL，以及 .kts 脚本模式。


## 安装 kotlinc

kotlinc 是 Kotlin 的命令行编译器，随 Kotlin 发行版一起分发。

不同系统有不同的安装方式，选一种即可，安装完成后命令会加入 PATH。

SDKMAN! 是最省心的方式，安装和切换版本都很方便。

```text
$ curl -s https://get.sdkman.io | bash
$ source "$HOME/.sdkman/bin/sdkman-init.sh"
$ sdk install kotlin

Downloading: kotlin 2.2.0
In progress...
Installing: kotlin 2.2.0
Done installing!

Setting kotlin 2.2.0 as default.
```

手动下载时请打开官方发布页，选择最新版本，不要照抄旧教程里写死的旧版本号。

下载地址：https://github.com/JetBrains/kotlin/releases/latest

解压后在环境变量中把 kotlinc/bin 目录加进 PATH 即可。

```text
$ export PATH="$PATH:/opt/kotlinc/bin"

# 把上面这行写进 ~/.zshrc 或 ~/.bashrc，重启终端后永久生效
```

注意：Kotlin 2.2 运行需要 JDK 8 及以上。安装 kotlinc 前先执行 java -version 确认 JDK 已就绪。


## 验证安装

安装完成后，用 -version 参数确认版本信息。

```text
$ kotlinc -version
info: kotlinc-jvm 2.2.0 (JRE 17.0.11+9)
```

输出中的 kotlinc-jvm 表示当前是 JVM 后端，括号里是运行编译器所用的 JRE 版本。

如果提示 command not found，说明 PATH 没有配置正确。


## 编译并运行第一个程序

先准备一个最简单的源文件，文件名必须与扩展名 .kt 一致。


## 实例

用下面的命令编译成可直接运行的 jar 包。

```text
$ kotlinc hello.kt -include-runtime -d hello.jar
$ java -jar hello.jar

Hello, Runoob!
欢迎来到 www.runoob.com
```

第一条命令把源码编译并打包，第二条命令用 JVM 运行生成的 jar。


## -d 与 -include-runtime 参数

这两个参数是命令行编译时最常用的，理解它们能避免「jar 包运行报错找不到类」的问题。

不带 -include-runtime 时，jar 里只有你自己的类，运行时需要额外把标准库放到 classpath 上。

只编译不打包时，把 -d 指向一个目录。

```text
$ kotlinc hello.kt -d out

$ ls out
HelloKt.class        # 顶层 main 函数所在的类，由文件名加 Kt 构成
```

类文件名规则很重要：hello.kt 里的顶层声明会编译进 HelloKt 类。


## 运行生成的 jar

打包成 jar 之后，用 java -jar 运行即可。

```text
$ kotlinc hello.kt -include-runtime -d hello.jar
$ java -jar hello.jar

Hello, Runoob!
欢迎来到 www.runoob.com
```

如果编译时漏掉 -include-runtime，运行会报 NoClassDefFoundError: kotlin/jvm/internal/Intrinsics。

这时要么重新打包，要么在 java 命令中手动把标准库加到 classpath。

```text
$ java -cp hello.jar:kotlin-stdlib.jar HelloKt
```

Windows 下 classpath 的分隔符是分号，Linux 与 macOS 用冒号。


## 编译成库

如果这份代码是给别人调用的工具库，就不该把运行时打进去，否则会和调用方的标准库冲突。

这种情况下不加 -include-runtime，生成一个纯类的 jar。


## 实例

编译成库并用 kotlin 命令运行，kotlin 命令会自动带上标准库。

```text
$ kotlinc Site.kt -d site.jar
$ kotlin -classpath site.jar com.runoob.SiteKt

欢迎访问 菜鸟教程（www.runoob.com）
```

-classpath 也可以简写成 -cp，后面跟 jar 路径或目录。

如果要被 Java 代码调用，直接把这个 jar 加入 Java 项目的 classpath 即可。


## REPL 交互式解释器

直接输入 kotlinc 不带任何参数，就会进入交互式解释器 REPL。

REPL 是 Read-Eval-Print Loop 的缩写，输入一行、立即执行一行，非常适合验证语法。

```text
$ kotlinc
Welcome to Kotlin version 2.2.0 (JRE 17.0.11+9)
Type :help for help, :quit for quit
>>> val siteName = "菜鸟教程"
>>> println("欢迎访问 $siteName")
欢迎访问 菜鸟教程
>>> println("网址：www.runoob.com".uppercase())
网址：WWW.RUNOOB.COM
>>> :quit
```

输入 :quit 或按 Ctrl+D 退出 REPL。

REPL 中变量会一直保留，可以连续使用之前定义过的值。

提示：REPL 每次只编译你输入的那一段，所以不能写完整的多行类定义，复杂代码还是写进 .kt 文件更合适。


## 脚本模式与 .kts 文件

Kotlin 还支持脚本模式，源文件扩展名是 .kts，顶层代码会被直接执行。

脚本不需要写 main 函数，写法和 Python 脚本类似。


## 实例

用 -script 参数运行脚本文件。

```text
$ kotlinc -script hello.kts

Hello, 菜鸟教程!
站点地址：www.runoob.com
名称长度：4
```

脚本模式也支持从命令行接收参数，通过 args 数组访问。


## 实例

```text
$ kotlinc -script greet.kts 菜鸟教程

你好，菜鸟教程！欢迎访问 www.runoob.com
```

如果本机已经用 SDKMAN! 安装过 Kotlin，还可以直接给脚本加执行权限，用 #!/usr/bin/env kotlinc -script 作为 shebang 行。


## 常用选项

下面这张表汇总了 kotlinc 最常用的参数，日常开发基本够用。

-Werror 在 CI 流水线里很有用，能防止带警告的代码被合并。


## 常见问题

命令行编译遇到的报错大多和路径、classpath 有关。


### error: could not find or load main class

说明 java -jar 找错了入口类，或者打包时漏掉了 -include-runtime。

先执行 jar tf hello.jar 查看 jar 内是否包含 kotlin 目录。


### warning: classpath entry points to a non-existent location

classpath 里写了不存在的路径，检查 jar 文件名和相对路径是否正确。


### 编译速度慢

每次调用 kotlinc 都要启动一次 JVM，脚本量大时建议改用 Gradle 增量编译。


### 中文在终端显示乱码

确认终端编码为 UTF-8，Windows 下可以执行 chcp 65001 切换代码页。


## 复习重点

- 能说明 `Kotlin 使用命令行编译` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
