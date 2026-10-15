# Scala：Scala 安装

- 来源：[Scala 安装及环境配置](https://www.runoob.com/scala/scala-install.html)
- 分类：编程语言
- 技术：Scala
- 笔记类型：练习笔记
- 章节序号：3756

## 本章内容

Scala 语言可以运行在 Window、Linux、Unix、 Mac OS X 等系统上。

Scala 是基于 Java 之上，大量使用 Java 的类库和变量，使用 Scala 之前必须先安装 Java（>1.5版本）。


## Mac OS X 和 Linux 上安装 Scala


### 第一步：Java 设置

确保你本地已经安装了 JDK 1.5 以上版本，并且设置了 JAVA_HOME 环境变量及 JDK 的 bin 目录。

我们可以使用以下命令查看是否安装了 Java：

```text
$ java -version
java version "1.8.0_31"
Java(TM) SE Runtime Environment (build 1.8.0_31-b13)
Java HotSpot(TM) 64-Bit Server VM (build 25.31-b07, mixed mode)
$
```

接着，我们可以查看是否安装了 Java 编译器。输入以下命令查看：

```text
$ javac -version
javac 1.8.0_31
$
```

如果还未安装，可以参考我们的Java 开发环境配置。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Scala 安装及环境配置` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
