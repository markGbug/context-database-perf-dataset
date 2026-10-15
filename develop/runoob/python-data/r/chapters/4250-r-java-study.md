# R：Java 中操作 R

- 来源：[Java 中操作 R](https://www.runoob.com/r/r-java.html)
- 分类：Python / 数据科学
- 技术：R
- 笔记类型：学习笔记
- 章节序号：4250

## 本章内容

首先，在 R 中安装软件包 "Rserve" 。

如果你使用的是 RGui 可视化界面，在菜单栏的 程序包 - 安装程序包 里可以完成这个步骤。如果你使用的是纯粹的 R Console，可以使用以下命令：

```text
install.packages("Rserve", repos = "https://mirrors.ustc.edu.cn/CRAN/")
```

当 Reserve 安装完成之后，在 R 的根目录下会有一个 library 目录，在其中找到 Rserve/java 目录，然后会发现目录下有两个文件：REngine.jar 和 Rserve.jar。

这两个文件就是 Java 中的 R 接口库。

注意：Java 不能做到脱离 R 系统独立使用 R 的功能！


### 第一步 启动 Reserve

进入 R，输入以下代码已启动 Rserve：

```text
library("Rserve")
Rserve()
```

如果启动成功，R 会输出 Rserve 的路径。


### 第二步 编写 Java 程序

首先导入刚才的两个 jar 库。

导入之后，我们认识一个关键的类：RConnection, 这个类可以用于连接到 Rserve。

我们现在在 Java 中利用 R 完成一个逆矩阵运算：


## 实例

执行结果：

```text
-1.9999999999999998    1.0
1.4999999999999998    -0.49999999999999994
```

很显然，结果是正确的，但毕竟是浮点数，所以打印出来可能有些不好看，不影响对数据的使用。


## 复习重点

- 能说明 `Java 中操作 R` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
