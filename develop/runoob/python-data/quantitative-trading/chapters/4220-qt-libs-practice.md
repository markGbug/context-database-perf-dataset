# 量化交易：Python 量化金融库

- 来源：[Python 量化金融库](https://www.runoob.com/python-qt/qt-libs.html)
- 分类：Python / 数据科学
- 技术：量化交易
- 笔记类型：练习笔记
- 章节序号：4220

## 本章内容

学习一些量化金融领域常用的 Python 库，比如：

- zipline: 用于回测和实施交易算法的库，安装命令：pip install zipline。
- Quantlib: 用于定价金融工具和执行金融计算的库，安装命令：pip install Quantlib。
- TA-Lib: 用于技术分析的库，安装命令：pip install TA-Lib。
- pyfolio: 是一个用于评估投资组合性能的库，它可以与zipline等回测工具集成，提供分析投资组合收益、风险等方面的工具，安装命令：pip install pyfolio。
- statsmodels: 是一个用于估计统计模型的库，包括线性回归、时间序列分析等。在量化金融中，它可用于建立和测试交易策略，安装命令：pip install statsmodels。


## zipline

zipline 是一个用于量化金融研究和算法交易的开源框架。

它是由 Quantopian 公司开发的，旨在为研究员和开发者提供一个方便的工具，用于构建、测试和执行量化交易策略。

在 zipline 的使用之前，请确保你已经安装了该库，你可以使用以下命令进行安装：

```text
conda install -c conda-forge zipline
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Python 量化金融库` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
