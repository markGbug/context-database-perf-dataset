# 知识点 67141：Pandas：Pandas JSON - pd.read_json() - 读取 JSON 数据

- 来源：[Pandas JSON](https://www.runoob.com/pandas/pandas-json.html)
- 来源章节：[4012-pandas-json-practice.md](../chapters/4012-pandas-json-practice.md)
- 分类：Python / 数据科学
- 技术：Pandas
- 所在小节：pd.read_json() - 读取 JSON 数据
- 知识类型：代码
- 原章节序号：4012

## 原文片段

```text
import pandas as pd

df = pd.read_json(
    path_or_buffer,      # JSON 文件路径、JSON 字符串或 URL
    orient=None,         # JSON 数据的结构方式，默认是 'columns'
    dtype=None,          # 强制指定列的数据类型
    convert_axes=True,   # 是否转换行列索引
    convert_dates=True,  # 是否将日期解析为日期类型
    keep_default_na=True # 是否保留默认的缺失值标记
)
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `pd.read_json() - 读取 JSON 数据` 这一小节和 `Pandas JSON` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
