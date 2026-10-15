# Python：Python csv 模块

- 来源：[Python csv 模块](https://www.runoob.com/python3/python-csv.html)
- 分类：Python / 数据科学
- 技术：Python
- 笔记类型：学习笔记
- 章节序号：4164

## 本章内容

CSV（Comma-Separated Values）文件是一种常见的文件格式，用于存储表格数据。

CSV 文件由纯文本组成，每一行代表表格中的一行数据，而每一列则通过逗号（或其他分隔符）分隔。

CSV 文件通常用于数据交换，因为它简单且易于处理。

Python 提供了一个内置的 csv 模块，用于读取和写入 CSV 文件。这个模块简化了处理 CSV 文件的过程，使得开发者可以轻松地操作表格数据。


### 1. 读取 CSV 文件

要读取 CSV 文件，可以使用 csv.reader 对象。以下是一个简单的示例：


## 实例

- open('data.csv', mode='r', encoding='utf-8')：以只读模式打开名为 data.csv 的文件，并指定编码为 UTF-8。
- csv.reader(file)：创建一个 csv.reader 对象，用于读取文件内容。
- for row in csv_reader：逐行读取文件内容，每一行数据会被解析为一个列表。


### 2. 写入 CSV 文件

要写入 CSV 文件，可以使用 csv.writer 对象。以下是一个示例：


## 实例

- open('output.csv', mode='w', encoding='utf-8', newline='')：以写入模式打开名为 output.csv 的文件，并指定编码为 UTF-8。newline='' 用于避免在 Windows 系统中出现空行。
- csv.writer(file)：创建一个 csv.writer 对象，用于写入文件内容。
- csv_writer.writerow(row)：将每一行数据写入文件。


### 3. 使用字典读取和写入 CSV 文件

csv 模块还提供了 DictReader 和 DictWriter 类，它们可以将 CSV 文件的每一行解析为字典，或者将字典写入 CSV 文件。


## 实例


## 实例


## 常用的属性和方法


### csv 模块核心方法


### csv.reader 和 csv.writer 对象常用方法


### csv.DictReader 和 csv.DictWriter 对象特性


### 常用参数说明


### 实例

1. 读取 CSV 文件


## 实例

2. 写入 CSV 文件


## 实例

3. 使用 DictReader 和 DictWriter（带表头）


## 实例

4. 自定义方言（如处理 TSV 文件）


## 实例


## 复习重点

- 能说明 `Python csv 模块` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
