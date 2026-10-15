# Kotlin：Kotlin 环境搭建

- 来源：[Kotlin 环境搭建](https://www.runoob.com/kotlin/kotlin-environment.html)
- 分类：移动开发
- 技术：Kotlin
- 笔记类型：练习笔记
- 章节序号：3365

## 本章内容

写 Kotlin 代码之前，需要先准备一个能编译和运行它的环境。

本文介绍五种常见方式，从最省事的在线运行到正式项目的 Gradle、Maven 与 Android Studio 配置。


## 五种运行方式对比

不同方式适合不同阶段，先看一张对比表再决定从哪里开始。

注意：Kotlin 2.2 要求 JDK 8 及以上。旧教程里写的「JDK 1.6」早已不受支持，按那个版本配置会直接报错。


## 在线运行

如果只想马上试一行代码，在线工具是最快的方式，连 JDK 都不用装。

官方 Playground 地址是 play.kotlinlang.org，打开就能编辑并运行。

把下面的代码粘贴进去，点击 Run 即可看到输出。


## 实例

输出结果如下。

```text
Hello, 菜鸟教程!
网址：www.runoob.com
```

菜鸟教程的在线工具同样可以运行 Kotlin，适合边看教程边验证代码。

在线工具的缺点是没法安装依赖、不能调试，只适合做语法练习。


## IntelliJ IDEA

本地学习最推荐 IntelliJ IDEA，它是 JetBrains 自家的 IDE，对 Kotlin 的支持最完整。

下载 Community 社区版即可，个人学习完全免费，功能足够日常使用。

下载地址：https://www.jetbrains.com/idea/download/

使用说明：https://www.runoob.com/kotlin/kotlin-setup.html

安装完成后按下面的步骤新建项目。

第一步，打开 IDEA，点击 New Project，在左侧语言列表中选择 Kotlin。

第二步，填写项目名称，例如 kotlin-demo，并确认 Build system 选择 IntelliJ。

第三步，选择 JDK 版本。JDK 8 及以上都可以，建议使用 JDK 17 或 JDK 21 这类长期支持版本。

第四步，在 src/main/kotlin 目录上右键，新建 Kotlin 文件 Main.kt，写入代码后点击行号旁的绿色三角运行。


## 实例

控制台会输出下面这一行。

```text
项目创建成功，目标站点：www.runoob.com
```

IDEA 的 Kotlin 插件已内置，无需单独安装，新建 Kotlin 文件后会自动识别语法。

提示：如果新建项目时提示找不到 JDK，到 File 菜单下的 Project Structure 里指定本机 JDK 的安装目录即可。


## Gradle 项目

Gradle 是目前 Kotlin/JVM 项目最主流的构建工具，只需要一个配置文件就能拉齐依赖与编译任务。

Kotlin 2.2 使用 Kotlin DSL 编写构建脚本，文件名为 build.gradle.kts。


## 实例

再补一个 settings.gradle.kts，声明项目名，Gradle 才能正确识别根项目。


## 实例

推荐的标准目录结构如下，源码统一放在 src/main/kotlin 下。

```text
kotlin-demo/
├── build.gradle.kts
├── settings.gradle.kts
└── src
    └── main
        └── kotlin
            └── com
                └── runoob
                    └── Main.kt
```

主类文件内容如下，注意包名要和目录结构一致。


## 实例

在项目根目录执行下面的命令，Gradle 会自动下载依赖、编译并运行。

```text
$ ./gradlew run

> Task :run
Hello, Runoob!
教程站点：www.runoob.com

BUILD SUCCESSFUL in 3s
```

Windows 下把 ./gradlew 换成 gradlew.bat 即可。


## Maven 项目

如果团队已有 Maven 体系，也可以用 Maven 构建 Kotlin 项目，核心是引入 kotlin-maven-plugin。

在项目根目录创建 pom.xml，内容如下。


## 实例

源码放在 src/main/kotlin/com/runoob/Main.kt，执行下面的命令编译并运行。

```text
$ mvn compile
$ mvn exec:java -Dexec.mainClass=com.runoob.MainKt

Hello, Runoob!
教程站点：www.runoob.com
```

如果使用 exec:java 报错，需要在 pom.xml 里额外配置 exec-maven-plugin 插件。


## Android Studio

Android Studio 基于 IntelliJ IDEA，内置 Kotlin 支持，是开发 Android 应用的标准工具。

新建项目时选择 Empty Activity 模板，向导会自动生成 Kotlin DSL 的构建脚本。

现代写法使用 plugins { } 块声明插件，旧版的 Groovy 写法已经过时。


## 实例

对应的 Gradle 插件版本在项目根目录的 build.gradle.kts 中统一声明。


## 实例

注意：旧资料里的 apply plugin: 'kotlin-android' 是 Groovy 写法，现在依然能跑但已不推荐，新项目请统一使用 Kotlin DSL 的 plugins { } 块。


## Eclipse

Kotlin 官方早已停止维护 Eclipse 插件，不建议在新项目中使用。

Kotlin Eclipse 环境搭建：https://www.runoob.com/kotlin/kotlin-eclipse-setup.html

提示：如果你正在用 Eclipse，可以换成 IntelliJ IDEA 社区版或 Android Studio，两者都免费且开箱支持 Kotlin。


## 常见问题

下面几个问题是环境搭建阶段最常遇到的。


### 提示 Unsupported class file major version

这是 JDK 版本与 Gradle 或 Kotlin 插件版本不匹配导致的。

先确认 java -version 输出的版本不低于 8，再检查 Gradle 版本是否支持该 JDK。


### Gradle 下载依赖很慢

国内网络访问 Maven 中央仓库较慢时，可以在 build.gradle.kts 的 repositories 块中追加国内镜像仓库。


### IDEA 提示 Kotlin 插件版本过低

在 Settings 的 Plugins 页面搜索 Kotlin，点击 Update 升级到与编译器一致的版本。


### 中文输出乱码

确认源文件使用 UTF-8 编码，并在 Gradle 中设置 tasks.withType<JavaCompile> { options.encoding = "UTF-8" }。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Kotlin 环境搭建` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
