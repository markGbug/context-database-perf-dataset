# Kotlin：Kotlin 多平台与 Kotlin/JS、Native

- 来源：[Kotlin 多平台与 Kotlin/JS、Native](https://www.runoob.com/kotlin/kotlin-multiplatform.html)
- 分类：移动开发
- 技术：Kotlin
- 笔记类型：学习笔记
- 章节序号：3401

## 本章内容

Kotlin 不只能编译成 JVM 字节码，还能编译成 JavaScript、WebAssembly 和原生机器码。

Kotlin Multiplatform（简称 KMP）就是在这套多后端能力之上，让同一份业务逻辑在多个平台上复用。


## Kotlin 的四个后端

所谓后端，指的是把 Kotlin 源码翻译成哪种目标代码的那一部分编译器。

目前一共有四个后端，它们共享同一套语言前端，所以语法和标准库用起来基本一致。

四个后端共用同一套语言规则，但标准库中与平台相关的部分不同。

例如文件读写、线程、时间这些 API，各平台的实现完全不一样，这也是多平台项目要分 source set 的原因。


## Kotlin/JVM

Kotlin/JVM 是最成熟、使用最广的后端，编译产物就是标准的 JVM 字节码。

它能直接调用 Java 库，也可以用反射、注解处理器、字节码框架这些 JVM 生态的工具。

默认目标是 JVM 1.8 字节码，可以通过 jvmTarget 调高，Kotlin 2.2.20 起支持到 JDK 25。


## 实例

Android 本质上也是 Kotlin/JVM，只是换成了 Android 的编译链和运行时。


## Kotlin/JS

Kotlin/JS 把 Kotlin 编译成 JavaScript，产物可以直接在浏览器或 Node.js 里运行。

从 Kotlin 1.9 起，旧的 Legacy 后端被移除，IR 后端是唯一选择。

在 IR 后端下，Kotlin 的顶层声明默认不会被导出，必须显式加 @JsExport 才能从 JavaScript 调用。


## 实例

编译之后，JavaScript 侧就可以从模块里导入这些函数。


## 实例

运行输出结果为：

```text
你好，RUNOOB
```

提示：external 声明只描述 JS 侧已有的 API，不产生任何代码。如果写了一个 external 函数但 JS 侧并不存在，编译能通过，运行时才会报错。Kotlin 2.x 更推荐用 external 声明和 @JsModule，尽量少用 dynamic 类型。

Gradle 里声明 Kotlin/JS 目标的方式如下，browser() 表示运行目标是浏览器。


## 实例


## Kotlin/Native

Kotlin/Native 把 Kotlin 直接编译成机器码，产物是原生可执行文件或动态库，不需要虚拟机。

它支持的平台包括 iOS、macOS、Linux、Windows，以及 Android NDK 和 wasm32。


### 闭世界编译模型

闭世界意味着编译器在编译期就能看到程序用到的全部代码。

正因为如此，Kotlin/Native 可以做彻底的死代码消除，二进制体积小、启动快，但代价是失去了动态能力。

Kotlin/Native 的内存模型在 Kotlin 1.7.20 起换成了新的并发模型，对象不再需要冻结，跨线程共享的限制也随之取消。

旧的内存管理器在 Kotlin 1.9.20 起被移除。


### cinterop 与 C 库互操作

cinterop 工具能读取 C 头文件，自动生成对应的 Kotlin 绑定。

使用时需要提供一个 .def 文件描述头文件位置和生成的包名。


## 实例

对应的 .def 文件内容如下，只有三行。

```text
# 文件路径：src/nativeInterop/cinterop/runoob.def
headers = runoob.h
package = runoob
```

生成绑定后，Kotlin 代码就像调用普通函数一样调用 C 函数。


## 实例

运行输出结果为：

```text
C 库版本：1
runoob_add(3, 4) = 7
```


### 与 Objective-C / Swift 互操作

在 Apple 平台上，Kotlin/Native 可以直接和 Objective-C 互相调用，Swift 则通过生成的 framework 使用 Kotlin 代码。

Kotlin 类会被导出为 Objective-C 类，suspend 函数会自动映射成带完成回调的方法。


## 实例

Swift 侧 import 生成的 framework 之后就能直接使用。


## 实例

在 Xcode 控制台中的输出结果为：

```text
你好，RUNOOB
```

Kotlin 2.0 起还提供了实验性的 @ObjCName 注解，可以自定义暴露给 Objective-C / Swift 的名字，避免命名冲突。


## Kotlin/Wasm

Kotlin/Wasm 把 Kotlin 编译成 WebAssembly，目标是在浏览器里获得接近原生的执行速度。

它从 Kotlin 1.9.20 起进入 Beta，提供两个目标：wasmJs 面向浏览器，wasmWasi 面向 WASI 运行时。

和 Kotlin/JS 相比，Wasm 的优势在于性能更接近机器码，而且能利用 WasmGC 直接操作宿主对象。


## 实例

注意：Kotlin/Wasm 目前仍是 Beta，编译器和标准库 API 可能变化。生产项目如果只需要在浏览器跑 Kotlin，Kotlin/JS 更稳妥；追求性能且能接受实验性特性时再考虑 Wasm。


## expect 与 actual

多平台代码的核心机制是 expect 和 actual。

在共享代码里用 expect 声明「这里有这么一个东西」，各平台再用 actual 给出具体实现。

编译到某个平台时，编译器会用该平台的 actual 替换掉 expect。


## 实例

JVM 平台给出自己的实现。


## 实例

JavaScript 平台给出另一份实现。


## 实例

在 JVM 平台写一个入口把两者打印出来。


## 实例

在 JVM 上运行时输出结果如下。

```text
欢迎使用 Kotlin 多平台，当前平台：Kotlin/JVM
isDesktop = true
```

提示：expect class 与 actual class 也支持，但 Kotlin 2.0 起编译器会给出 Beta 状态的警告，可以用 -Xexpect-actual-classes 抑制。能用 expect 函数或接口解决的场景，优先不要用 expect 类。


## KMP 项目结构与 source set

KMP 项目把代码按平台划分到不同的 source set 里，共享的放在 common，平台专属的放在各自目录。

典型的目录结构如下。

```text
runoob-multiplatform/
├── build.gradle.kts              # 根构建脚本，声明目标平台
├── settings.gradle.kts
├── gradle/
│   └── libs.versions.toml        # 版本目录，集中管理依赖版本
└── src/
    ├── commonMain/kotlin/        # 所有平台共享的代码
    │   └── Platform.kt
    ├── commonTest/kotlin/        # 共享测试
    ├── jvmMain/kotlin/           # 仅 JVM 平台
    ├── jsMain/kotlin/            # 仅 Kotlin/JS
    ├── nativeMain/kotlin/        # 所有 Kotlin/Native 目标共享
    └── iosMain/kotlin/           # 仅 iOS 目标
```

常见的 source set 及其作用如下表。

nativeMain、appleMain、iosMain 这些中间层由默认层级模板自动生成，Kotlin 1.9.20 起默认启用。

构建脚本里声明目标平台和依赖。


## 实例

多平台项目从 Kotlin 1.3 起进入稳定阶段，现在 Android、iOS、桌面、后端的共享逻辑都用它来组织。

提示：不要把 UI 代码也塞进 commonMain。KMP 的定位是共享业务逻辑、网络、数据模型和存储，界面部分通常交给 Compose Multiplatform 或各平台自己的 UI 框架。


## 后续章节

- 常见问题
- commonMain 里为什么不能用 java.util
- Kotlin/Native 为什么不能用反射
- @JsExport 加了但 JS 还是拿不到
- expect 和 actual 的签名必须完全一致吗
- Kotlin/JS 和 Kotlin/Wasm 怎么选

## 复习重点

- 能说明 `Kotlin 多平台与 Kotlin/JS、Native` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
