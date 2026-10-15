# 知识点 57704：Pandas：Pandas CSV - pd.read_csv() - 读取 CSV 文件

- 来源：[Pandas CSV](https://www.runoob.com/pandas/pandas-csv-file.html)
- 来源章节：[4010-pandas-csv-file-study.md](../chapters/4010-pandas-csv-file-study.md)
- 分类：Python / 数据科学
- 技术：Pandas
- 所在小节：pd.read_csv() - 读取 CSV 文件
- 知识类型：代码
- 原章节序号：4010

## 原文片段

```text
import pandas as pd

# 读取 CSV 文件，并自定义列名和分隔符
df = pd.read_csv('data.csv', sep=';', header=0, names=['A', 'B', 'C'], dtype={'A': int, 'B': float})
print(df)
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `pd.read_csv() - 读取 CSV 文件` 这一小节和 `Pandas CSV` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
