# NumPy：NumPy 安装

- 来源：[NumPy 安装](https://www.runoob.com/numpy/numpy-install.html)
- 分类：Python / 数据科学
- 技术：NumPy
- 笔记类型：学习笔记
- 章节序号：3979

## 本章内容

Python 官网上的发行版是不包含 NumPy 模块的。

我们可以使用以下几种方法来安装。


## 使用 pip 安装

安装 NumPy 最简单的方法就是使用 pip 工具：

```text
pip3 install numpy
```

这里使用的是 Python3，如果你用的是 Python2 可以用 pip install numpy 安装在。

默认情况使用国外线路，国外太慢，我们使用清华的镜像就可以:

```text
pip3 install numpy -i https://pypi.tuna.tsinghua.edu.cn/simple
```


## 使用 conda 安装

如果使用的是 Anaconda 环境，可以使用 conda 来安装 NumPy：

```text
conda install numpy
```

通过 conda 安装的 NumPy 通常会带有一些优化的数学库（如 Intel MKL），可以提高性能。

更多 conda 命令的相关内容可以参考：Anaconda 教程。


## 从源代码安装

如果需要从源代码安装 NumPy，可以在 NumPy 官方 GitHub 仓库下载源码：https://github.com/numpy/numpy，进入解压后的目录并执行以下命令：

```text
python setup.py install
```


## 安装验证

无论使用哪种方式安装完成后，可以通过以下代码令验证 NumPy 是否安装成功：


## 实例

如果安装成功，会输出正确的版本号信息：

```text
1.26.4
```


## 使用已有的发行版本

对于许多用户，尤其是在 Windows 上，最简单的方法是下载以下的 Python 发行版，它们包含了所有的关键包（包括 NumPy，SciPy，matplotlib，IPython，SymPy 以及 Python 核心自带的其它包）：

- Anaconda: 免费 Python 发行版，用于进行大规模数据处理、预测分析，和科学计算，致力于简化包的管理和部署。支持 Linux, Windows 和 Mac 系统。
- Enthought Canopy: 提供了免费和商业发行版。持 Linux, Windows 和 Mac 系统。
- Python(x,y): 个适用于科学计算和数据分析的 Python 发行版，专门为 提供了 Spyder IDE 等工具，适合进行科学计算的开发工作。
- WinPython: 另一个免费的 Python 发行版，包含科学计算包与 Spyder IDE。支持 Windows。
- Pyzo: 基于 Anaconda 的免费发行版本及 IEP 的交互开发环境，超轻量级。 支持 Linux, Windows 和 Mac 系统。


## 复习重点

- 能说明 `NumPy 安装` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
