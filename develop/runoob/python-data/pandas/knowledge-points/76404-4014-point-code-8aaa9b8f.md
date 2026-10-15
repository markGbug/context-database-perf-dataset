# 知识点 76404：Pandas：Pandas 读取 HTML - 实例

- 来源：[Pandas 读取 HTML](https://www.runoob.com/pandas/pandas-html.html)
- 来源章节：[4014-pandas-html-practice.md](../chapters/4014-pandas-html-practice.md)
- 分类：Python / 数据科学
- 技术：Pandas
- 所在小节：实例
- 知识类型：代码
- 原章节序号：4014

## 原文片段

```text
原始数据：
           日期   产品    销量   备注
0  2024-01-01  产品A  1234  NaN
1  2024-01-02  产品B   567   缺货
2  2024-01-03  产品C    --  未统计

清洗后：
          日期   产品      销量    备注
0 2024-01-01  产品A  1234.0   NaN
1 2024-01-02  产品B   567.0  <NA>
2 2024-01-03  产品C     NaN  <NA>

数据类型：
日期    datetime64[ns]
产品            object
销量           float64
备注            object
dtype: object
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `实例` 这一小节和 `Pandas 读取 HTML` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
