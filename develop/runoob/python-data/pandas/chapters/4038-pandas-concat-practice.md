# Pandas：Pandas 数据拼接（concat / append）

- 来源：[Pandas 数据拼接](https://www.runoob.com/pandas/pandas-concat.html)
- 分类：Python / 数据科学
- 技术：Pandas
- 笔记类型：练习笔记
- 章节序号：4038

## 本章内容

数据拼接是将多个 DataFrame 或 Series 按行或按列拼接在一起。pd.concat 是主要的拼接函数，append 是简化版本（已废弃，更推荐使用 concat）。


## concat 基本用法

pd.concat() 可以沿着轴方向拼接多个 DataFrame 或 Series。


### 行方向拼接（上下拼接）


## 实例


### 列方向拼接（左右拼接）


## 实例

axis=0 表示行方向拼接（增加行），axis=1 表示列方向拼接（增加列）。


## 处理重复索引


### ignore_index


## 实例


### 验证重复键


## 实例


## 处理列不匹配


### join 参数


## 实例


### 只添加新列


## 实例


## keys 参数创建层次索引


## 实例


## 实战：合并多个月份数据


## 实例


## append 方法（已废弃）

DataFrame.append() 在 Pandas 2.0 中已废弃，不推荐使用。请使用 pd.concat() 代替。

```text
# 不推荐（已废弃）
result = df1.append(df2)

# 推荐
result = pd.concat([df1, df2])
```

concat 是 Pandas 中拼接数据的标准方法，性能更好，功能更完整。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Pandas 数据拼接` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
