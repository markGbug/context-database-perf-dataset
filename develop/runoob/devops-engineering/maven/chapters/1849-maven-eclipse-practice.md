# Maven：Maven Eclipse

- 来源：[Maven Eclipse](https://www.runoob.com/maven/maven-eclipse.html)
- 分类：DevOps / 工程化
- 技术：Maven
- 笔记类型：练习笔记
- 章节序号：1849

## 本章内容

Eclipse 提供了一个很好的插件 m2eclipse ，该插件能将 Maven 和 Eclipse 集成在一起。

在最新的 Eclipse 中自带了 Maven，我们打开，Windows->Preferences，如果会出现下面的画面：

下面列出 m2eclipse 的一些特点：

- 可以在 Eclipse 环境上运行 Maven 的目标文件。
- 可以使用其自带的控制台在 Eclipse 中直接查看 Maven 命令的输出。
- 可以在 IDE 下更新 Maven 的依赖关系。
- 可以使用 Eclipse 开展 Maven 项目的构建。
- Eclipse 基于 Maven 的 pom.xml 来实现自动化管理依赖关系。
- 它解决了 Maven 与 Eclipse 的工作空间之间的依赖，而不需要安装到本地 Maven 的存储库（需要依赖项目在同一个工作区）。
- 它可以自动地从远端的 Maven 库中下载所需要的依赖以及源码。
- 它提供了向导，为建立新 Maven 项目，pom.xml 以及在已有的项目上开启 Maven 支持。
- 它提供了远端的 Maven 存储库的依赖的快速搜索。


### 在 Eclipse 中导入一个 Maven 的项目

- 打开 Eclipse
- 选择 File > Import > option
- 选择 Maven Projects 选项。点击 Next 按钮。
- 选择项目的路径，即使用 Maven 创建一个项目时的存储路径。假设我们创建了一个项目： consumerBanking. 通过 Maven 构建 Java 项目 查看如何使用 Maven 创建一个项目。
- 点击 Finish 按钮。

现在，你可以在 Eclipse 中看到 Maven 项目。

看一下 consumerBanking 项目的属性，你可以发现 Eclipse 已经将 Maven 所依赖的都添加到了它的构建路径里了。

好了，我们来使用 Eclipse 的编译功能来构建这个 Maven 项目。

- 右键打开 consumerBanking 项目的上下文菜单
- 选择 Run 选项
- 然后选择 maven package 选项

Maven 开始构建项目，你可以在 Eclipse 的控制台看到输出日志。

```text
[INFO] Scanning for projects...
[INFO] -------------------------------------------------------------------
[INFO] Building consumerBanking
[INFO]
[INFO] Id: com.companyname.bank:consumerBanking:jar:1.0-SNAPSHOT
[INFO] task-segment: [package]
[INFO] -------------------------------------------------------------------
[INFO] [resources:resources]
[INFO] Using default encoding to copy filtered resources.
[INFO] [compiler:compile]
[INFO] Nothing to compile - all classes are up to date
[INFO] [resources:testResources]
[INFO] Using default encoding to copy filtered resources.
[INFO] [compiler:testCompile]
[INFO] Nothing to compile - all classes are up to date
[INFO] [surefire:test]
[INFO] Surefire report directory:
C:\MVN\consumerBanking\target\surefire-reports

-------------------------------------------------------
 T E S T S
-------------------------------------------------------
Running com.companyname.bank.AppTest
Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.047 sec

Results :

Tests run: 1, Failures: 0, Errors: 0, Skipped: 0

[INFO] [jar:jar]
[INFO] -------------------------------------------------------------------
[INFO] BUILD SUCCESSFUL
[INFO] -------------------------------------------------------------------
[INFO] Total time: 1 second
[INFO] Finished at: Thu Jul 12 18:18:24 IST 2012
[INFO] Final Memory: 2M/15M
[INFO] -------------------------------------------------------------------
```

现在，右键点击 App.java， 选择 Run As 选项。选择 As Java App

你将看到如下结果：

```text
Hello World!
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Maven Eclipse` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
