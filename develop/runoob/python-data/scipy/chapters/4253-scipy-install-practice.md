# SciPy：SciPy 安装

- 来源：[SciPy 安装](https://www.runoob.com/scipy/scipy-install.html)
- 分类：Python / 数据科学
- 技术：SciPy
- 笔记类型：练习笔记
- 章节序号：4253

## 本章内容

本章节，我们使用 pip 工具来安装 SciPy 库，如果还未安装该工具，可以参考 Python pip 安装与使用。

升级 pip：

```text
python3 -m pip install -U pip
```

安装 scipy 库：

```text
python3 -m pip install -U scipy
```

安装完成后，我们就可以通过 from scipy import module 来导入 scipy 的库：

constants 是 scipy 的常量模块。

以下实例，我们通过导入 scipy 库，然后查看 scipy 库的版本号：

## 实例

执行以上代码，输出结果如下：

```text
1.7.0
```

以下实例，我们通过导入 scipy 的常量模块 constants 来查看一英亩等于多少平方米：

## 实例

执行以上代码，输出结果如下：

```text
4046.8564223999992
```

## 动手验证

- 复现 `SciPy 安装` 中的关键示例或命令。
- 修改一个输入、参数或条件，观察结果变化。
- 记录报错信息、定位过程和修复方式。
