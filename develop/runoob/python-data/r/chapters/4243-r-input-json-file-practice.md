# R：R JSON 文件

- 来源：[R JSON 文件](https://www.runoob.com/r/r-input-json-file.html)
- 分类：Python / 数据科学
- 技术：R
- 笔记类型：练习笔记
- 章节序号：4243

## 本章内容

JSON: JavaScript Object Notation(JavaScript 对象表示法)。

JSON 是存储和交换文本信息的语法。

JSON 类似 XML，但比 XML 更小、更快，更易解析。

如果你对 JSON 还不了解，可以先查阅：JSON 教程

R 语言读写 JSON 文件需要安装扩展包，我们可以在 R 到控制台输入以下命令来安装：

```text
install.packages("rjson", repos = "https://mirrors.ustc.edu.cn/CRAN/")
```

查看是否安装成功：

```text
> any(grepl("rjson",installed.packages()))
[1] TRUE
```

创建 sites.json 文件，json 文件与测试脚本同一目录下，代码如下：


## 实例

```text
{
   "id":["1","2","3"],
   "name":["Google","Runoob","Taobao"],
   "url":["www.google.com","www.runoob.com","www.taobao.com"],
   "likes":[ 111,222,333]
}
```

查看数据，某一行使用 [ ], 指定的行和列使用 [[ ]]:


## 实例

执行以上代码输出结果为：

```text
$id
[1] "1" "2" "3"

$name
[1] "Google" "Runoob" "Taobao"

$url
[1] "www.google.com" "www.runoob.com" "www.taobao.com"

$likes
[1] 111 222 333

[1] "==============="
$id
[1] "1" "2" "3"

[1] "==============="
[1] "Runoob"
```

我们也可以使用 as.data.frame() 函数将 json 文件数据可以转为数据框类型，这样我们就更方便对数据进行操作：


## 实例

执行以上代码输出结果为：

```text
  id   name            url likes
1  1 Google www.google.com   111
2  2 Runoob www.runoob.com   222
3  3 Taobao www.taobao.com   333
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `R JSON 文件` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
