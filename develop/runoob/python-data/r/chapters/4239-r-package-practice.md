# R：R 包

- 来源：[R 包](https://www.runoob.com/r/r-package.html)
- 分类：Python / 数据科学
- 技术：R
- 笔记类型：练习笔记
- 章节序号：4239

## 本章内容

包是 R 函数、实例数据、预编译代码的集合，包括 R 程序，注释文档、实例、测试数据等。

R 语言相关的包一般存储安装目录下对 "library" 目录，默认情况在 R 语言安装完成已经自带来一些常用对包，当然我们也可以在后期自定义添加一些要使用的包。

R 语言完整的相关包可以查阅：https://cran.r-project.org/web/packages/available_packages_by_name.html

接下来我们主要介绍如何安装 R 语言的包。


### 查看 R 包的安装目录

我们可以使用以下函数来查看 R 包的安装目录：


## 实例


### 查看已安装的包

我们可以使用以下函数来查看已安装的包：

```text
library()
```

输出结果如下：

```text
base                    The R Base Package
boot                    Bootstrap Functions (Originally by Angelo Canty
                        for S)
class                   Functions for Classification
cluster                 "Finding Groups in Data": Cluster Analysis
                        Extended Rousseeuw et al.
codetools               Code Analysis Tools for R
compiler                The R Compiler Package
datasets                The R Datasets Package
foreign                 Read Data Stored by 'Minitab', 'S', 'SAS',
                        'SPSS', 'Stata', 'Systat', 'Weka', 'dBase', ...
graphics                The R Graphics Package
grDevices               The R Graphics Devices and Support for Colours
                        and Fonts
grid                    The Grid Graphics Package
KernSmooth              Functions for Kernel Smoothing Supporting Wand
                        & Jones (1995)
lattice                 Trellis Graphics for R
MASS                    Support Functions and Datasets for Venables and
                        Ripley's MASS
```


### 查看已载入的包

我们可以使用以下函数来查看编译环境已载入的包：


## 实例


## 安装新包

安装新包可以使用 install.packages() 函数，格式如下：

```text
install.packages("要安装的包名")
```

我们可以直接设置包名，从 CRAN 网站上获取包，如下实例我们载入 XML 包：

```text
# 安装 XML 包
install.packages("XML")
```

或者我们可以直接在 CRAN 上下载相关包，直接在本地安装：

```text
install.packages("./XML_3.98-1.3.zip")
```

我们国内一般建议大家使用国内镜像，以下实例使用中国科学技术大学源进行安装：

```text
# 安装 XML 包
install.packages("XML", repos = "https://mirrors.ustc.edu.cn/CRAN/")
```

CRAN (The Comprehensive R Archive Network) 镜像源配置文件之一是 .Rprofile (linux 下位于 ~/.Rprofile )。

在文末添加如下语句:

```text
options("repos" = c(CRAN="https://mirrors.tuna.tsinghua.edu.cn/CRAN/"))
```

打开 R 即可使用该 CRAN 镜像源安装 R 软件包。


### 使用包

新安装的包需要先载入 R 编译环境中才可以使用，格式如下：

```text
library("包名")
```

以下实例载入 XML 包：

```text
library("XML")
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `R 包` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
