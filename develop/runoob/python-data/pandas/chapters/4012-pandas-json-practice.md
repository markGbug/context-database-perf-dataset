# Pandas：Pandas JSON

- 来源：[Pandas JSON](https://www.runoob.com/pandas/pandas-json.html)
- 分类：Python / 数据科学
- 技术：Pandas
- 笔记类型：练习笔记
- 章节序号：4012

## 本章内容

JSON（JavaScript Object Notation，JavaScript 对象表示法），是存储和交换文本信息的语法，类似 XML。

JSON 比 XML 更小、更快，更易解析，更多 JSON 内容可以参考 JSON 教程。

Pandas 提供了强大的方法来处理 JSON 格式的数据，支持从 JSON 文件或字符串中读取数据并将其转换为 DataFrame，以及将 DataFrame 转换回 JSON 格式。

Pandas 可以很方便的处理 JSON 数据，本文以 sites.json 为例，内容如下：


## 实例

```text
[
   {
   "id": "A001",
   "name": "菜鸟教程",
   "url": "www.runoob.com",
   "likes": 61
   },
   {
   "id": "A002",
   "name": "Google",
   "url": "www.google.com",
   "likes": 124
   },
   {
   "id": "A003",
   "name": "淘宝",
   "url": "www.taobao.com",
   "likes": 45
   }
]
```


## 从 JSON 文件/字符串加载数据


### pd.read_json() - 读取 JSON 数据

read_json() 用于从 JSON 格式的数据中读取并加载为一个 DataFrame。它支持从 JSON 文件、JSON 字符串或 JSON 网址中加载数据。

语法格式：

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

参数说明：

常见的 orient 参数选项:

从 JSON 文件加载数据：


## 实例

to_string() 用于返回 DataFrame 类型的数据，我们也可以直接处理 JSON 字符串。


## 实例

以上实例输出结果为：

```text
     id    name             url  likes
0  A001    菜鸟教程  www.runoob.com     61
1  A002  Google  www.google.com    124
2  A003      淘宝  www.taobao.com     45
```

JSON 对象与 Python 字典具有相同的格式，所以我们可以直接将 Python 字典转化为 DataFrame 数据：


## 实例

以上实例输出结果为：

```text
      col1 col2
row1     1    x
row2     2    y
row3     3    z
```

从 URL 中读取 JSON 数据：


## 实例

以上实例输出结果为：

```text
     id    name             url  likes
0  A001    菜鸟教程  www.runoob.com     61
1  A002  Google  www.google.com    124
2  A003      淘宝  www.taobao.com     45
```

从 JSON 字符串加载数据：


## 实例

输出：

```text
      Name  Age           City
0    Alice   25       New York
1      Bob   30    Los Angeles
2  Charlie   35        Chicago
```

从 JSON 数据读取（指定 orient 为 records）：


## 实例

输出：

```text
      Name  Age           City
0    Alice   25       New York
1      Bob   30    Los Angeles
2  Charlie   35        Chicago
```


### 内嵌的 JSON 数据


## nested_list.json 文件内容

使用以下代码格式化完整内容：


## 实例

以上实例输出结果为：

```text
          school_name   class                                           students
0  ABC primary school  Year 1  {'id': 'A001', 'name': 'Tom', 'math': 60, 'phy...
1  ABC primary school  Year 1  {'id': 'A002', 'name': 'James', 'math': 89, 'p...
2  ABC primary school  Year 1  {'id': 'A003', 'name': 'Jenny', 'math': 79, 'p...
```

这时我们就需要使用到 json_normalize() 方法将内嵌的数据完整的解析出来：


## 实例

以上实例输出结果为：

```text
     id   name  math  physics  chemistry
0  A001    Tom    60       66         61
1  A002  James    89       76         51
2  A003  Jenny    79       90         78
```

data = json.loads(f.read()) 使用 Python JSON 模块载入数据。

json_normalize() 使用了参数 record_path 并设置为 ['students'] 用于展开内嵌的 JSON 数据 students。

显示结果还没有包含 school_name 和 class 元素，如果需要展示出来可以使用 meta 参数来显示这些元数据：


## 实例

以上实例输出结果为：

```text
     id   name  math  physics  chemistry         school_name   class
0  A001    Tom    60       66         61  ABC primary school  Year 1
1  A002  James    89       76         51  ABC primary school  Year 1
2  A003  Jenny    79       90         78  ABC primary school  Year 1
```

接下来，让我们尝试读取更复杂的 JSON 数据，该数据嵌套了列表和字典，数据文件 nested_mix.json 如下：


## nested_mix.json 文件内容

nested_mix.json 文件转换为 DataFrame：


## 实例

以上实例输出结果为：

```text
     id   name  math  physics  chemistry   class info.president info.contacts.tel
0  A001    Tom    60       66         61  Year 1    John Kasich         123456789
1  A002  James    89       76         51  Year 1    John Kasich         123456789
2  A003  Jenny    79       90         78  Year 1    John Kasich         123456789
```


### 读取内嵌数据中的一组数据

以下是实例文件 nested_deep.json，我们只读取内嵌中的 math 字段：


## nested_deep.json 文件内容

这里我们需要使用到 glom 模块来处理数据套嵌，glom 模块允许我们使用 . 来访问内嵌对象的属性。

第一次使用我们需要安装 glom：

```text
pip3 install glom
```


## 实例

以上实例输出结果为：

```text
0    60
1    89
2    79
Name: students, dtype: int64
```


## 将 DataFrame 转换为 JSON


### DataFrame.to_json() - 将 DataFrame 转换为 JSON 数据

to_json() 方法用于将 DataFrame 转换为 JSON 格式的数据，可以指定 JSON 的结构化方式。

语法格式：

```text
df.to_json(
    path_or_buffer=None,    # 输出的文件路径或文件对象，如果是 None 则返回 JSON 字符串
    orient=None,            # JSON 格式方式，支持 'split', 'records', 'index', 'columns', 'values'
    date_format=None,       # 日期格式，支持 'epoch', 'iso'
    default_handler=None,   # 自定义非标准类型的处理函数
    lines=False,            # 是否将每行数据作为一行（适用于 'records' 或 'split'）
    encoding='utf-8'        # 编码格式
)
```

参数说明：


## 实例

将 DataFrame 转换为 JSON 文件（指定 orient='records'）：


## 实例

将 DataFrame 转换为 JSON 并指定日期格式：


## 实例

```text
{"Name":{"0":"Alice","1":"Bob","2":"Charlie"},"Date":{"0":"2021-01-01T00:00:00.000Z","1":"2022-02-01T00:00:00.000Z","2":"2023-03-01T00:00:00.000Z"},"Age":{"0":25,"1":30,"2":35}}
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Pandas JSON` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
