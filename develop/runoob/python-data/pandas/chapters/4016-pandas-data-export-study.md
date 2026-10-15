# Pandas：Pandas 数据导出

- 来源：[Pandas 数据导出](https://www.runoob.com/pandas/pandas-data-export.html)
- 分类：Python / 数据科学
- 技术：Pandas
- 笔记类型：学习笔记
- 章节序号：4016

## 本章内容

Pandas 提供了丰富的导出功能，可以将 DataFrame 导出为各种常见格式，包括 CSV、Excel、SQL 数据库、JSON 等。本节详细介绍各种导出方式的使用方法和注意事项。


## 导出为 CSV

CSV 是最通用的数据交换格式，导出会受环境默认编码影响，需要注意中文编码问题。


### 基本导出


## 实例


### 中文编码处理


## 实例


### 导出选项详解


## 实例


## 导出为 Excel

Excel 格式适合人工查看和编辑，但大文件导出较慢。


### 安装依赖

```text
pip install openpyxl xlwt
```


### 基本导出


## 实例


### 多 Sheet 导出


## 实例


### 格式化导出


## 实例


## 导出为数据库

可以直接将 DataFrame 导出到 SQL 数据库，详见《Pandas 读取 SQL 数据库》一章。


## 实例


## 导出为 JSON


## 实例


## 导出为其他格式


### 导出为 HTML


## 实例


### 导出为 Markdown


## 实例


## 后续章节

- 导出为 LaTeX
- 实例
- 导出为 Pickle
- 实例
- 大数据量导出
- 实例
- 常见问题与注意事项

## 复习重点

- 能说明 `Pandas 数据导出` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
