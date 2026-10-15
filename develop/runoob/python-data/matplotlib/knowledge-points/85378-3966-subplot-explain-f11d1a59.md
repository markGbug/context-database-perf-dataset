# 知识点 85378：Matplotlib：Matplotlib 绘制多图 - subplot

- 来源：[Matplotlib 绘制多图](https://www.runoob.com/matplotlib/matplotlib-subplots.html)
- 来源章节：[3966-matplotlib-subplots-study.md](../chapters/3966-matplotlib-subplots-study.md)
- 分类：Python / 数据科学
- 技术：Matplotlib
- 所在小节：subplot
- 知识类型：解释
- 原章节序号：3966

## 原文片段

实例 import matplotlib.pyplot as plt import numpy as np #plot 1: xpoints = np.array([0, 6]) ypoints = np.array([0, 100]) plt.subplot(1, 2, 1) plt.plot(xpoints,ypoints) plt.title("plot 1") #plot 2: x = np.array([1, 2, 3, 4]) y = np.array([1, 4, 9, 16]) plt.subplot(1, 2, 2) plt.plot(x,y) plt.title("plot 2") plt.suptitle("RUNOOB subplot Test") plt.show() 显示结果如下： 设置 numRows ＝ 2，numCols ＝ 2，就是将图表绘制成 2x2 的图片区域, 对应的坐标为： (1, 1), (1, 2) (2, 1), (2, 2) plotNum ＝ 1, 表示的坐标为(1, 1), 即第一行第一列的子图。

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `subplot` 这一小节和 `Matplotlib 绘制多图` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
