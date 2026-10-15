# R：R 环境安装

- 来源：[R 环境安装](https://www.runoob.com/r/r-setup.html)
- 分类：Python / 数据科学
- 技术：R
- 笔记类型：练习笔记
- 章节序号：4224

## 本章内容

R 语言的开发环境本身具备了图形开发环境，这与其他很多工程语言是不同的，所以开发环境最好安装在为桌面个人计算机设计的操作系统上（如 Windows, macOS 或 Ubuntu 桌面版 等）。

首先，我们需要下载 R 语言环境的安装包：


### Windows

- 官方地址：https://cloud.r-project.org/bin/windows/base/
- USTC 镜像：https://mirrors.ustc.edu.cn/CRAN/bin/windows/base/
- TUNA 镜像：https://mirrors.tuna.tsinghua.edu.cn/CRAN/bin/windows/base/


### Linux

- 官方地址：https://cloud.r-project.org/bin/linux/
- USTC 镜像：https://mirrors.ustc.edu.cn/CRAN/bin/linux/
- TUNA 镜像：https://mirrors.tuna.tsinghua.edu.cn/CRAN/bin/linux/


### macOS

- 官方地址：https://cloud.r-project.org/bin/macosx/
- USTC 镜像：https://mirrors.ustc.edu.cn/CRAN/bin/macosx/
- TUNA 镜像：https://mirrors.tuna.tsinghua.edu.cn/CRAN/bin/macosx/

以上的版本有可能是过时的，如果你需要最新版本，可以访问：

- 清华大学源： https://mirrors.tuna.tsinghua.edu.cn/CRAN/bin/
- 官网：https://cloud.r-project.org/bin/


## Windows 操作系统

Windows 安装很简单，下载安装包后，双击下载的安装包，开始安装向导：

注意：这里使用的操作系统是 64 位的，但现在仍有少数的计算机使用的是 32 位的操作系统，如果你的操作系统是 32 位的，请在此步骤选择"32-bit 用户安装"选项。

当我们在交互式的命令窗口输入以下代码：

```text
print("Hello, world")
```

输出结果为：

```text
"Hello, world"
```


## Linux


### Ubuntu 安装

执行以下命令安装 R 语言执行环境：

```text
# sudo apt update
# sudo apt -y upgrade
# sudo apt -y install r-base
```

安装成功后，执行 R 命令就可以进入交互式的编程窗口了：


### Centos 安装

```text
# sudo yum install R
```

输入以下命令，查看安装的版本：

```text
# R --version
```

交互式命令可以通过输入 q() 来退出：

```text
> q()
Save workspace image? [y/n/c]: y
```


## macOS 安装

macOS 安装 R 语言环境类似 Windows，下载 pkg 安装包，双击安装包打开，然后按安装向导安装：

安装成功后，执行 R 命令就可以进入交互式的编程窗口了：

交互式命令可以通过输入 q() 来退出：

```text
> q()
Save workspace image? [y/n/c]: y
```


### 脚本执行

在 R 语言中，可以在命令行中使用 Rscript 命令来执行 R 脚本文件。

Rscript 命令允许您直接从命令行运行 R 脚本，而无需打开 R 控制台。。

要使用 Rscript命令 执行 R 脚本文件，可以按照以下步骤进行操作：

创建一个 R 脚本文件，其中包含要执行的R代码。例如，将以下代码保存为 script.R 文件：


## script.R 文件代码：

打开终端或命令行界面，进入当前文件 script.R 所在目录，在命令行中使用 Rscript 命令来执行脚本文件：

```text
Rscript script.R
```

执行以上命令后，R 脚本文件将被 Rscript 解释器读取和执行。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `R 环境安装` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
