# R：R Excel 文件

- 来源：[R Excel 文件](https://www.runoob.com/r/r-input-excel-file.html)
- 分类：Python / 数据科学
- 技术：R
- 笔记类型：学习笔记
- 章节序号：4241

## 本章内容

Excel 格式的文件主要是 xls 或 xlsx，这两种文件可以在 R 语言中导入 xlsx 库来实现直接的读取。

R 语言读写 Excel 文件需要安装扩展包，我们可以在 R 到控制台输入以下命令来安装：

install.packages("xlsx", repos = "https://mirrors.ustc.edu.cn/CRAN/") 安装过程如下： 事实上，几乎所有的 Excel 软件与大多数表格软件一样支持 CSV 格式的数据，所以完全可以通过 CSV 与 R 交互，没必要再使用 Excel。

查看 xlsx 是否安装成功：


## 实例

执行以上代码输出结果为：

```text
[1] TRUE
Loading required package: rJava
Loading required package: methods
Loading required package: xlsxjars
```

Excel 文件数据：

点击链接下载 Excel 测试数据：https://static.jyshare.com/download/sites.xlsx

接下来，我们可以使用 read.xlsx() 函数来读取 Excel 数据：


## 实例


## 复习重点

- 能说明 `R Excel 文件` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
