# Pandas：Pandas Excel 文件操作

- 来源：[Pandas Excel](https://www.runoob.com/pandas/pandas-excel.html)
- 分类：Python / 数据科学
- 技术：Pandas
- 笔记类型：学习笔记
- 章节序号：4011

## 本章内容

Pandas 提供了丰富的 Excel 文件操作功能，帮助我们方便地读取和写入 .xls 和 .xlsx 文件，支持多表单、索引、列选择等复杂操作，是数据分析中必备的工具。


### pd.read_excel() - 读取 Excel 文件

pd.read_excel() 方法用于从 Excel 文件中读取数据并加载为 DataFrame。它支持读取 .xls 和 .xlsx 格式的文件。

语法格式如下：

```html
pandas.read_excel(io, sheet_name=0, *, header=0, names=None, index_col=None, usecols=None, dtype=None, engine=None, converters=None, true_values=None, false_values=None, skiprows=None, nrows=None, na_values=None, keep_default_na=True, na_filter=True, verbose=False, parse_dates=False, date_parser=<no_default>, date_format=None, thousands=None, decimal='.', comment=None, skipfooter=0, storage_options=None, dtype_backend=<no_default>, engine_kwargs=None)
```

参数说明：

- io：这是必需的参数，指定了要读取的 Excel 文件的路径或文件对象。
- sheet_name=0：指定要读取的工作表名称或索引。默认为0，即第一个工作表。
- header=0：指定用作列名的行。默认为0，即第一行。
- names=None：用于指定列名的列表。如果提供，将覆盖文件中的列名。
- index_col=None：指定用作行索引的列。可以是列的名称或数字。
- usecols=None：指定要读取的列。可以是列名的列表或列索引的列表。
- dtype=None：指定列的数据类型。可以是字典格式，键为列名，值为数据类型。
- engine=None：指定解析引擎。默认为None，pandas 会自动选择。
- converters=None：用于转换数据的函数字典。
- true_values=None：指定应该被视为布尔值True的值。
- false_values=None：指定应该被视为布尔值False的值。
- skiprows=None：指定要跳过的行数或要跳过的行的列表。
- nrows=None：指定要读取的行数。
- na_values=None：指定应该被视为缺失值的值。
- keep_default_na=True：指定是否要将默认的缺失值（例如NaN）解析为NA。
- na_filter=True：指定是否要将数据转换为NA。
- verbose=False：指定是否要输出详细的进度信息。
- parse_dates=False：指定是否要解析日期。
- date_parser=<no_default>：用于解析日期的函数。
- date_format=None：指定日期的格式。
- thousands=None：指定千位分隔符。
- decimal='.'：指定小数点字符。
- comment=None：指定注释字符。
- skipfooter=0：指定要跳过的文件末尾的行数。


## 实例

输出结果为：

```text
      表格 1 Unnamed: 1   Unnamed: 2
0     Name        Age         City
1    Alice         25     New York
2      Bob         30  Los Angeles
3  Charlie         35      Chicago
```

read_excel 默认读取第一个表单（sheet_name=0），假设 data.xlsx 文件中只有一个表单，读取后的数据会存储在一个 DataFrame 中。

如果 data.xlsx 文件中有多个表单，可以通过指定 sheet_name 来读取特定表单的数据，例如 pd.read_excel('data.xlsx', sheet_name='Sheet1')。


## 实例


### DataFrame.to_excel() - 将 DataFrame 写入 Excel 文件

to_excel() 方法用于将 DataFrame 写入 Excel 文件，支持 .xls 和 .xlsx 格式。

语法格式如下：

```text
DataFrame.to_excel(excel_writer, *, sheet_name='Sheet1', na_rep='', float_format=None, columns=None, header=True, index=True, index_label=None, startrow=0, startcol=0, engine=None, merge_cells=True, inf_rep='inf', freeze_panes=None, storage_options=None, engine_kwargs=None)
```

参数说明：

- excel_writer：这是必需的参数，指定了要写入的 Excel 文件路径或文件对象。
- sheet_name='Sheet1'：指定写入的工作表名称，默认为 'Sheet1'。
- na_rep=''：指定在 Excel 文件中表示缺失值（NaN）的字符串，默认为空字符串。
- float_format=None：指定浮点数的格式。如果为 None，则使用 Excel 的默认格式。
- columns=None：指定要写入的列。如果为 None，则写入所有列。
- header=True：指定是否写入列名作为第一行。如果为 False，则不写入列名。
- index=True：指定是否写入索引作为第一列。如果为 False，则不写入索引。
- index_label=None：指定索引列的标签。如果为 None，则不写入索引标签。
- startrow=0：指定开始写入的行号，默认从第0行开始。
- startcol=0：指定开始写入的列号，默认从第0列开始。
- engine=None：指定写入 Excel 文件时使用的引擎，默认为 None，pandas 会自动选择。
- merge_cells=True：指定是否合并单元格。如果为 True，则合并具有相同值的单元格。
- inf_rep='inf'：指定在 Excel 文件中表示无穷大值的字符串，默认为 'inf'。
- freeze_panes=None：指定冻结窗格的位置。如果为 None，则不冻结窗格。
- storage_options=None：用于云存储的参数字典。
- engine_kwargs=None：传递给引擎的额外参数字典。


## 实例


### ExcelFile - 加载 Excel 文件

ExcelFile 是一个用于读取 Excel 文件的类，它可以处理多个表单，并在不重新打开文件的情况下访问其中的数据。

语法格式如下：

```text
excel_file = pd.ExcelFile('data.xlsx')
```

常用方法：


## 实例


### ExcelWriter - 写入 Excel 文件

ExcelWriter 是 pandas 提供的一个类，用于将 DataFrame 或 Series 对象写入 Excel 文件。使用 ExcelWriter，你可以在一个 Excel 文件中写入多个工作表，并且可以更灵活地控制写入过程。

语法格式如下：

```text
pandas.ExcelWriter(path, engine=None, date_format=None, datetime_format=None, mode='w', storage_options=None, if_sheet_exists=None, engine_kwargs=None)
```

参数说明：

- path：这是必需的参数，指定了要写入的 Excel 文件的路径、URL 或文件对象。可以是本地文件路径、远程存储路径（如 S3）、URL 链接或已打开的文件对象。
- engine：这是一个可选参数，用于指定写入 Excel 文件的引擎。如果为 None，则 pandas 会自动选择一个可用的引擎（默认优先选择 openpyxl，如果不可用则选择其他可用引擎）。常见的引擎包括 'openpyxl'（用于 .xlsx 文件）、'xlsxwriter'（提供高级格式化和图表功能）、'odf'（用于 OpenDocument 格式如 .ods）等。
- date_format：这是一个可选参数，指定写入 Excel 文件中日期的格式字符串，例如 "YYYY-MM-DD"。
- datetime_format：这是一个可选参数，指定写入 Excel 文件中日期时间对象的格式字符串，例如 "YYYY-MM-DD HH:MM:SS"。
- mode：这是一个可选参数，默认为 'w'，表示写入模式。如果设置为 'a'，则表示追加模式，向现有文件中添加数据（仅支持部分引擎，如 openpyxl）。
- storage_options：这是一个可选参数，用于指定与存储后端连接的额外选项，例如认证信息、访问权限等，适用于写入远程存储（如 S3、GCS）。
- if_sheet_exists：这是一个可选参数，默认为 'error'，指定如果工作表已经存在时的行为。选项包括 'error'（抛出错误）、'new'（创建一个新工作表）、'replace'（替换现有工作表的内容）、'overlay'（在现有工作表上覆盖写入）。
- engine_kwargs：这是一个可选参数，用于传递给引擎的其他关键字参数。这些参数会传递给相应引擎的函数，例如 xlsxwriter.Workbook(file, **engine_kwargs) 或 openpyxl.Workbook(**engine_kwargs) 等。

创建 ExcelWriter 对象：


## 实例

这里，ExcelWriter 被用作上下文管理器，确保文件在操作完成后正确关闭。

写入多个工作表：

你可以使用同一个 ExcelWriter 对象将不同的 DataFrame 写入同一个 Excel 文件的不同工作表。


## 实例

设置日期格式或日期时间格式：


## 实例

向现有 Excel 文件追加内容：


## 实例

使用 if_sheet_exists 参数替换已存在的工作表：


## 实例

向同一个工作表写入多个 DataFrame，注意 if_sheet_exists 参数需要设置为 overlay：


## 实例

将 Excel 文件存储在内存中：


## 实例

将 Excel 文件打包到 zip 压缩文件中：


## 实例

向底层引擎传递额外的参数：


## 实例

在追加模式下，engine_kwargs 会传递给 openpyxl 的 load_workbook：


## 实例


## 复习重点

- 能说明 `Pandas Excel` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
