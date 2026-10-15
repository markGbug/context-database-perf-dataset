# OpenCV：OpenCV 安装

- 来源：[OpenCV 安装](https://www.runoob.com/opencv/opencv-install.html)
- 分类：AI / 智能开发
- 技术：OpenCV
- 笔记类型：概念卡
- 章节序号：0447

## 本章内容

在使用 OpenCV 之前，首先需要在你的开发环境中安装它。

安装 OpenCV 的方法取决于你使用的操作系统以及开发语言，我们以 Python 环境下的安装为例，因为 Python 是 OpenCV 最常用的编程语言之一。


## 1、安装 OpenCV（Python 版）


### pip 安装

安装 OpenCV（Python 版）前提条件：

- 安装了 Python（建议使用 Python 3.x 版本）。
- 安装了 pip（Python 包管理工具）。

使用以下命令验证是否安装：

```text
python3 -V
pip -V
```

如果还未安装 Python 参考：Python 环境搭建。

注意：Python 2.7.9 + 或 Python 3.4+ 以上版本都自带 pip 工具。

使用 pip 安装 OpenCV 是最简单和直接的方法，你只需要在命令行中输入以下命令：

```text
pip install opencv-python
```

该命令会自动从 PyPI（Python 包索引）下载并安装 OpenCV 的 Python 版本。

如果需要额外的模块（例如 contrib 模块），可以安装 opencv-contrib-python：

```text
pip install opencv-contrib-python
```

这个版本包含了更多 OpenCV 的模块和功能，适合需要深度学习、物体识别等复杂任务的开发者。

opencv-python 和 opencv-contrib-python 包是 OpenCV 的不同版本，它们分别包含了核心模块和扩展模块，一般来说，opencv-contrib-python 包含更多功能，适合需要高级应用的用户。

如果安装速度慢，可以切换 pip 源（例如使用清华源）：

```text
pip install opencv-python -i https://pypi.tuna.tsinghua.edu.cn/simple
```

安装完成后，可以通过以下代码验证 OpenCV 是否安装成功：


## 实例

如果输出了 OpenCV 的版本号（例如 4.8.0），说明安装成功。


### 2、通过 Anaconda 安装（推荐用于数据科学和深度学习开发）

如果你使用 Anaconda 来管理 Python 环境，可以通过以下命令轻松安装 OpenCV：

首先，创建一个新的虚拟环境（可选）：

```text
conda create -n opencv_env python=3.x
```

激活环境：

```text
conda activate opencv_env
```

安装 OpenCV：

```text
conda install -c conda-forge opencv
```

使用 Anaconda 安装时，opencv 会自动处理所有的依赖，并且在大多数情况下能够顺利安装。

Anaconda 相关内容：Anaconda 教程。


## 记忆卡片

- 一句话定义：`OpenCV 安装` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
