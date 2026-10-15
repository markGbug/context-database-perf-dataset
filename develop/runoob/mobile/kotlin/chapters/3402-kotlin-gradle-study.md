# Kotlin：Kotlin Gradle 构建

- 来源：[Kotlin Gradle 构建](https://www.runoob.com/kotlin/kotlin-gradle.html)
- 分类：移动开发
- 技术：Kotlin
- 笔记类型：学习笔记
- 章节序号：3402

## 本章内容

Gradle 是目前 Kotlin/JVM 项目使用最广泛的构建工具，它负责编译源码、管理第三方依赖、运行测试和打包产物。

本章节从零开始搭建一个 Kotlin Gradle 项目，讲清 build.gradle.kts 的写法、依赖配置的区别以及常用命令。


## 为什么用 Gradle

写几个 Kotlin 文件用 kotlinc 编译就够了，但真实项目远不止编译这一件事。

你需要引入第三方库、区分主代码和测试代码、把项目拆成多个模块、在打包时生成不同环境的产物，这些工作手工完成既繁琐又容易出错。

Gradle 把这些工作变成可重复执行的「任务」，一条命令就能完成。

与 Maven 相比，Gradle 使用 Kotlin DSL 或 Groovy DSL 编写配置，配置文件本身就是代码，可以写循环、条件判断和自定义函数，灵活性更高。

Kotlin 官方文档和 Android 官方文档都以 Gradle 作为默认构建方案，新项目基本不需要再考虑其他选择。


## 项目目录结构

Gradle 遵循「约定优于配置」，源码放在固定的目录里，不需要额外声明路径。

一个标准的 Kotlin/JVM 项目结构如下，源码集（source set）分为 main 和 test 两部分。

```text
runoob-demo/
├── build.gradle.kts          # 构建脚本，声明插件、依赖、任务
├── settings.gradle.kts       # 项目名与子模块声明
├── gradle.properties         # 可选，构建参数与 JVM 参数
├── gradlew                   # Linux/macOS 下的 Gradle Wrapper 脚本
├── gradlew.bat               # Windows 下的 Gradle Wrapper 脚本
├── gradle/wrapper/           # Wrapper 的 jar 与版本配置
└── src
    ├── main/kotlin/          # 主源码集，参与最终产物
    │   └── com/runoob/Main.kt
    └── test/kotlin/          # 测试源码集，不进入最终产物
        └── com/runoob/MainTest.kt
```

Kotlin 源码的扩展名是 .kt，包名 com.runoob 对应目录 src/main/kotlin/com/runoob。

使用 IntelliJ IDEA 新建 Kotlin 项目时，IDE 会自动生成这套结构，你只需要关注 src 目录和两个构建脚本。

提示：务必使用项目自带的 gradlew 而不是系统安装的 gradle 命令。gradlew 会锁定构建工具版本，保证团队里每个人、每台机器上的构建结果一致。


## build.gradle.kts 最小配置

构建脚本是项目的核心，下面这份配置已经能完成编译、运行和测试。

文件路径：build.gradle.kts。


## 实例

配套的项目名声明写在 settings.gradle.kts 里，Gradle 启动时会最先执行它。


## 实例

主程序文件放在 src/main/kotlin/com/runoob/Main.kt。


## 实例

执行 run 任务即可看到输出。

```text
$ ./gradlew run

> Task :run
Hello, Runoob!
网站：www.runoob.com

BUILD SUCCESSFUL in 1s
```

脚本里每个配置块的作用可以对照下表理解。


## 依赖管理

依赖配置的关键不是「写哪一行」，而是理解每个配置的可见性和传递规则。

同一份依赖，声明在不同的配置里，能看到的源码集和能否传递给下游模块完全不同。

implementation 与 api 的区别只有在多模块项目中才显现，单模块项目里两者效果相同。

一个模块用 implementation 引入的库，下游模块在编译时看不到，因此上游升级或更换这个库时不会破坏下游代码。

只有当下游代码必须直接使用某个库的类型时，才用 api 把它暴露出去。


## 实例

依赖坐标的格式是「group:name:version」三段式，版本号必须写全，否则 Gradle 无法解析。

还有一个 compileOnly 配置，用于只在编译期可见、运行时由容器提供的库，例如 servlet-api。

注意：旧资料里常见的 compile 配置已经在 Gradle 7.0 中移除，请改用 implementation 或 api。看到 compile 就应该替换。


## 插件与版本管理

插件决定了项目能做什么，Kotlin 项目最核心的插件就是 kotlin("jvm")。

它提供 Kotlin 编译任务、标准库依赖以及 kotlin 扩展配置，版本号必须与你的 Kotlin 版本一致。

当项目变大、依赖变多时，把版本号散落在各个 build.gradle.kts 里会很难维护。

Gradle 提供了版本目录（Version Catalog），把版本集中写在 gradle/libs.versions.toml 中。


## 实例

有了版本目录，构建脚本就能写成下面这样，不再出现任何硬编码的版本号。


## 实例

Kotlin 插件与 Gradle 版本之间存在兼容关系，升级时建议先查官方兼容性表，不要随意跳版本。


## 常用任务与命令

Gradle 的一切工作都以任务（task）为单位，任务名可以直接写在 gradlew 后面执行。

下面这些任务覆盖了日常开发的绝大部分场景。

执行 build 任务时会依次编译、测试、打包，输出信息里能看到每个任务的执行情况。

```text
$ ./gradlew build

> Task :compileKotlin
> Task :compileJava NO-SOURCE
> Task :processResources
> Task :classes
> Task :jar
> Task :compileTestKotlin
> Task :test
> Task :check
> Task :build

BUILD SUCCESSFUL in 3s
```

在 Windows 下把 ./gradlew 换成 gradlew.bat 即可，其余参数完全一致。

提示：任务名支持缩写，只要前缀唯一，./gradlew cK 就等价于 ./gradlew compileKotlin。不确定缩写是否唯一时，还是写全称更稳妥。


## 多模块项目简述

当项目规模变大，把所有代码放在一个模块里会拖慢构建速度，也不利于复用。

多模块项目用一个根项目管理若干子模块，每个子模块有自己的 build.gradle.kts。

先在 settings.gradle.kts 中声明要包含哪些模块。


## 实例

子模块通过 project 函数互相依赖，冒号前缀写法是 Gradle 的标准写法。


## 实例

根目录的 build.gradle.kts 通常只用来统一配置所有子模块，例如统一 JDK 版本和仓库地址。


## 实例

多模块项目的目录结构与单模块类似，只是每个模块各有一套 src 目录。

```text
runoob-multi/
├── settings.gradle.kts
├── build.gradle.kts
├── app/
│   ├── build.gradle.kts
│   └── src/main/kotlin/...
├── core/
│   ├── build.gradle.kts
│   └── src/main/kotlin/...
└── data/
    ├── build.gradle.kts
    └── src/main/kotlin/...
```


## 与 Maven 对比

Maven 出现得更早，生态成熟，配置格式固定；Gradle 更灵活，构建速度更快。

两者都能完成 Kotlin 项目的构建，选择哪一个取决于团队习惯和项目需求。

如果你维护的是已有的 Maven 项目，不必为了用 Kotlin 而迁移构建工具，kotlin-maven-plugin 同样可以编译 Kotlin。

新项目则建议直接使用 Gradle，尤其是涉及 Android 或多平台时。


## 常见问题

下面这些问题在初次接触 Gradle 时最容易遇到。


### gradlew 和 gradle 有什么区别

gradlew 是项目自带的 Wrapper 脚本，它会下载并使用 gradle/wrapper/gradle-wrapper.properties 中指定版本的 Gradle。

gradle 是你系统里安装的全局命令，版本可能与项目要求不一致，因此始终优先使用 gradlew。


### 依赖下载很慢或者失败

默认从 Maven 中央仓库下载，国内网络可能较慢，可以在 repositories 中换成镜像仓库。


## 实例


### 编译报错说找不到 Kotlin 标准库

检查 plugins 块里是否声明了 kotlin("jvm") 插件，插件会自动把 kotlin-stdlib 加入依赖，不需要手动写。


### JDK 版本不匹配

推荐用 kotlin { jvmToolchain(17) } 统一指定 JDK，Gradle 会自动查找或下载对应版本。

如果不想让 Gradle 下载 JDK，也可以在本机安装后通过 org.gradle.java.installations.paths 指定路径。


## 复习重点

- 能说明 `Kotlin Gradle 构建` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
