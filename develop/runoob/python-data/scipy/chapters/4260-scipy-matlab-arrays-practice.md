# SciPy：SciPy Matlab 数组

- 来源：[SciPy Matlab 数组](https://www.runoob.com/scipy/scipy-matlab-arrays.html)
- 分类：Python / 数据科学
- 技术：SciPy
- 笔记类型：练习笔记
- 章节序号：4260

## 本章内容

NumPy 提供了 Python 可读格式的数据保存方法。

SciPy 提供了与 Matlab 的交互的方法。

SciPy 的 scipy.io 模块提供了很多函数来处理 Matlab 的数组。


### 以 Matlab 格式导出数据

savemat() 方法可以导出 Matlab 格式的数据。

- filename - 保存数据的文件名。
- mdict - 包含数据的字典。
- do_compression - 布尔值，指定结果数据是否压缩。默认为 False。

将数组作为变量 "vec" 导出到 mat 文件：


## 实例

注意：上面的代码会在您的计算机上保存了一个名为 "arr.mat" 的文件。


### 导入 Matlab 格式数据

loadmat() 方法可以导入 Matlab 格式数据。

该方法参数：

- filename - 保存数据的文件名。

返回一个结构化数组，其键是变量名，对应的值是变量值。

以下实例从 mat 文件中导入数组：


## 实例

返回结果如下：

```text
{
   '__header__': b'MATLAB 5.0 MAT-file Platform: nt, Created on: Tue Sep 22 13:12:32 2020',
   '__version__': '1.0',
   '__globals__': [],
   'vec': array([[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]])
 }
```


## 实例

返回结果如下：

```text
[[0 1 2 3 4 5 6 7 8 9]]
```

从结果可以看出数组最初是一维的，但在提取时它增加了一个维度，变成了二维数组。

解决这个问题可以传递一个额外的参数 squeeze_me=True：


## 实例

返回结果如下：

```text
[0 1 2 3 4 5 6 7 8 9]
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `SciPy Matlab 数组` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
