# Pandas：Pandas 常用函数

- 来源：[Pandas 常用函数](https://www.runoob.com/pandas/pandas-functions.html)
- 分类：Python / 数据科学
- 技术：Pandas
- 笔记类型：学习笔记
- 章节序号：4018

## 本章内容

以下列出了 Pandas 常用的一些函数及使用实例：


## 读取数据


## 实例


## 查看数据


## 实例


## 实例

以上实例输出结果为：

```text
     name  likes                     url
0  Google     25  https://www.google.com
1  Runoob     30  https://www.runoob.com
     name  likes                     url
2  Taobao     35  https://www.taobao.com
```


## 数据清洗


## 实例


## 数据选择和切片


## 实例


## 数据排序


## 实例


## 数据分组和聚合


## 实例


## 数据合并


## 实例


## 数据选择和过滤


## 数据统计和描述


## 实例

假设我们有如下的 JSON 数据，数据保存到 data.json 文件：


## data.json 文件

我们可以使用 Pandas 读取 JSON 数据，并进行数据清洗和处理、数据选择和过滤、数据统计和描述等操作，具体如下：


## 实例

输出结果如下：

```text
# df
   姓名  年龄 性别  成绩
1  Bob   0  male  90

# grouped
             年龄  成绩
性别
female  25.000000  80
male    27.500000  80

# stats
         成绩
count   1.0
mean   90.0
std     NaN
min    90.0
25%    90.0
50%    90.0
75%    90.0
max    90.0

# mean
成绩    90.0
dtype: float64

# median
成绩    90.0
dtype: float64

# mode
    姓名    成绩
0  Bob  90.0

# count
姓名    1
成绩    1
dtype: int64
```


## 复习重点

- 能说明 `Pandas 常用函数` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
