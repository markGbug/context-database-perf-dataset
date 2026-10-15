# Julia：Julia 环境安装

- 来源：[Julia 语言环境安装](https://www.runoob.com/julia/julia-environment.html)
- 分类：Python / 数据科学
- 技术：Julia
- 笔记类型：学习笔记
- 章节序号：3928

## 本章内容

Julia 语言支持以下系统：

- Windows
- macOS
- Linux
- FreeBSD

Julia 官方推荐使用 Juliaup 版本管理器安装，它会自动管理多个 Julia 版本并保持更新。

Julia 安装包下载地址为：https://julialang.org/downloads/。

Github 源码地址：https://github.com/JuliaLang/julia。

国内镜像地址：https://mirrors.tuna.tsinghua.edu.cn/julia-releases/bin/

各个系统对应的包名（以 Julia 1.10.4 为例）：

注：CPU 是 X86 还是 ARM 可以通过 uname -m 命令查看，输出 x86_64 表示 X86 架构，输出 arm64 或 aarch64 表示 ARM 架构：

```text
$ uname -m
x86_64
```


## 使用 Juliaup 安装（推荐）


### Windows 安装

Windows 下最简单的方式是从 Microsoft Store 安装 Julia，或者用 winget 命令安装：

```text
winget install --name Julia --id 9NJNWW8PVKMN -e -s msstore
```


### Linux 和 macOS 安装

在 Linux 或 macOS 上，执行以下命令安装 Juliaup 及最新稳定版 Julia：

```text
curl -fsSL https://install.julialang.org | sh
```

安装完成后重新打开终端，即可使用 julia 命令。

常用的安装器参数：

安装后可以使用 juliaup 命令管理版本：

```text
$ juliaup status          # 查看当前使用的版本
$ juliaup add 1.10        # 安装 1.10 版本
$ juliaup default 1.10    # 设置默认版本
```


## 使用二进制包安装

如果不使用 Juliaup，也可以直接下载二进制包安装。


### Windows 下安装

从 https://julialang.org/downloads/ 下载 Windows Julia 安装程序。

注：32 位 Julia 二进制文件可在 32 位和 64 位 Windows 上运行，但 64 位 Julia 二进制文件只能在 64 位 Windows (x86_64) 上运行，现在电脑基本上都是 64 位的。

运行安装程序，安装过程点击 Next 就好了。

勾选 Add Julia To PATH 自动将 Julia 添加到环境变量。

这样我们就可以在终端执行 julia 命令了。

Julia 默认安装目录类似于 C:\Users\RUNOOB\AppData\Local\Programs\Julia 1.10.4。


### Linux/FreeBSD 安装

下载 x86_64 二进制包：

```text
wget https://julialang-s3.julialang.org/bin/linux/x64/1.10/julia-1.10.4-linux-x86_64.tar.gz
```

以上是官网提供的下载地址，如果速度慢，可以采用国内镜像地址下载（注意路径中是 x64 目录）：

```text
wget https://mirrors.tuna.tsinghua.edu.cn/julia-releases/bin/linux/x64/1.10/julia-1.10.4-linux-x86_64.tar.gz
```

解压：

```text
tar zxvf julia-1.10.4-linux-x86_64.tar.gz
```

Linux/FreeBSD 二进制文件不需要安装，但需要我们的系统可以找到 julia 可执行文件，这就需要将 julia 的目录添加到系统环境中。

解压完成后将 julia 的解压目录移动到 /usr/local 目录下：

```text
sudo mv julia-1.10.4 /usr/local/
```

移动完成后我们就可以使用完整目录执行 julia 命令：

```text
$ /usr/local/julia-1.10.4/bin/julia -v
julia version 1.10.4
```

julia -v 命令用于查看版本号。

也可以将 julia 命令添加到您的系统 PATH 环境变量中，编辑 ~/.bashrc（或 ~/.bash_profile）文件，在最后一行添加以下代码：

```text
export PATH="$PATH:/usr/local/julia-1.10.4/bin/"
```

添加后执行以下命令，让环境变量立即生效：

```text
source ~/.bashrc
或
source ~/.bash_profile
```

这样我们就可以直接执行 julia 命令而不需要添加完整路径：

```text
$ julia -v
julia version 1.10.4
```


### macOS 安装

Apple Silicon（M1/M2/M3 等）芯片下载 macaarch64 包，Intel 芯片下载 mac64 包：

```text
# Apple Silicon 版本
wget https://julialang-s3.julialang.org/bin/mac/aarch64/1.10/julia-1.10.4-macaarch64.tar.gz

# Intel 版本
wget https://julialang-s3.julialang.org/bin/mac/x64/1.10/julia-1.10.4-mac64.tar.gz
```

解压：

```text
tar zxvf julia-1.10.4-macaarch64.tar.gz
```

将解压目录移动到 /usr/local 目录下：

```text
sudo mv julia-1.10.4 /usr/local/
```

将 julia 添加到 PATH 环境变量，编辑 ~/.zshrc（macOS 默认 shell 是 zsh）文件，在最后一行添加：

```text
export PATH="$PATH:/usr/local/julia-1.10.4/bin/"
```

添加后执行以下命令，让环境变量立即生效：

```text
source ~/.zshrc
```

验证安装：

```text
$ julia -v
julia version 1.10.4
```

也可以使用 Homebrew 安装：

```text
brew install julia
```


## 验证安装

安装完成后，执行 julia 命令进入交互式窗口，执行 versioninfo() 查看详细的版本信息：


## 实例


## 复习重点

- 能说明 `Julia 语言环境安装` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
