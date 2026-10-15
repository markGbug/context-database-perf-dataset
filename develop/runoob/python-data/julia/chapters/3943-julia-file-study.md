# Julia：Julia 文件读写

- 来源：[Julia 文件读写](https://www.runoob.com/julia/julia-file.html)
- 分类：Python / 数据科学
- 技术：Julia
- 笔记类型：学习笔记
- 章节序号：3943

## 本章内容

Julia 提供了一些基本的函数来处理文件：

- open() - 打开文件
- read() - 读取文件内容
- write() - 写入内容
- close() - 关闭文件

从文件读取或者写入数据需要使用文件句柄。

文件句柄其实就是一个指针，指向文件中的某个位置。从一个文件读取数据，应用程序首先要调用操作系统函数并传送文件名来打开文件，打开文件的函数会返回一个顺序号，即文件句柄（file handle），该文件句柄对于打开的文件是唯一的识别依据。


## open() 函数

Julia 可以使用 open() 函数打开一个文件，该函数返回文件句柄：

语法格式：

```text
open(filename, mode)
```

filename 为文件名，mode 为读写模式，可以是以下值：

```text
# Windows 打开文件
foo = open("D://runoob-test//julia//runoob-file.txt")

# Linux 或 Mac 打开文件
foo = open("./runoob-test/julia/runoob-file.txt")
```


### close() 函数

在对文件操作完成后，我们需要对文件进行关闭操作，不然会造成资源泄露等问题，关闭文件使用 close() 函数：

```text
# 关闭上面代码中打开文件返回的 foo 句柄
close(foo)
```

在 Julia 中，我们建议把文件处理包装在 do 语句块中：当该语句块执行完成时，打开的文件将自动关闭（自动调用 close() 函数），即使中途抛出异常也能保证关闭：


## 实例


## 写入文件

创建并写入文件的基本流程：open 以 "w" 模式打开（文件不存在会创建，已存在会清空），write 写入，close 关闭：


## test.jl 文件代码

执行以上代码：

```text
$ julia test.jl
```

执行成功后，我们就在当前代码文件的目录下创建了一个 runoob-file.txt 文件，写入内容如下：

```text
Hello world!
Runoob Julia Test
```

使用 do 语句就不需要手动 close：


## test.jl 文件代码

更简单的方式：直接用 write 方法写文件，它内部会自动打开和关闭文件：


## 实例

write 的返回值是写入的字节数。

追加模式：用 "a" 模式打开可以在文件末尾追加内容而不清空原内容：open("runoob-file.txt", "a") do io; write(io, "新的一行\n"); end


## 读取文件


### read() 函数

使用 read() 函数，我们可以读取文件的全部内容：


## 实例

执行以上代码，输出结果如下：

```text
$ julia test.jl
Hello world!
Runoob Julia Test
```

do 语句中使用 read() 函数：


## 实例

还有更简洁的写法，read 直接接受文件名：


## 实例


### readlines() 函数

我们可以使用 readlines() 函数将文件内容按行放到数组中：

```text
readlines(io; keep::Bool=false)
readlines(filename; keep::Bool=false)
```


## 实例

执行以上代码，输出结果如下：

```text
$ julia test.jl
["Hello world!\n", "Runoob Julia Test\n", "使用 do 语句"]
```


### eachline() 逐行处理

对于大文件，用 eachline() 逐行读取处理可以避免一次性把整个文件读入内存：


## 实例

执行以上代码，输出结果如下：

```text
$ julia test.jl
12, Hello world!
17, Runoob Julia Test
8, 使用 do 语句
```

我们也可以获取当前的行号：


## 实例

执行以上代码，输出结果如下：

```text
$ julia test.jl
1 Hello world!
2 Runoob Julia Test
3 使用 do 语句
```


## stat() 函数

stat() 函数用于获取文件的信息：

```text
stat(pathname)
```


## 实例

执行以上代码，输出结果如下：

```text
$ julia test.jl
desc: runoob-file.txt
device: 16777222
inode: 35345094
mode: 33188
nlink: 1
uid: 501
gid: 20
rdev: 0
size: 47
blksize: 4096
blocks: 8
mtime: 1.6524042534674733e9
ctime: 1.6524042534674733e9
```

常用的快捷字段函数有 filesize(path)（文件大小）、isfile(path)（是否为文件）、isdir(path)（是否为目录）等。


## abspath() 函数

abspath() 函数用于把相对路径转换为绝对路径：

```text
abspath(path)
```


## 实例

执行以上代码，输出结果如下：

```text
["/Users/RUNOOB/runoob-test/.Rhistory", "/Users/RUNOOB/runoob-test/.vscode",
...
```


## 文件与路径操作函数

下表列出了处理文件的其他相关函数：

cd(path)

切换当前目录

pwd()

获取当前目录

readdir(path)

返回目录下的文件与子目录名列表

abspath(path)

将相对路径转换为绝对路径

joinpath(str, str, ...)

从参数中组装路径名（自动处理分隔符，跨平台）

isdir(path)

判断提供的路径参数 path 是否是一个目录

splitdir(path)

将路径拆分为目录名和文件名的元组

splitdrive(path)

Windows 上将路径拆分为驱动器号部分和路径部分，在 Unix 系统上，第一个组件始终是空字符串

splitext(path)

将路径拆分为扩展名前和扩展名（含点）两部分，无扩展名时第二部分为空字符串

expanduser(path)

将路径开头的波浪字符 ~ 替换为当前用户的主目录

normpath(path)

规范化路径，删除 "." 和 ".." 目录

realpath(path)

解析符号链接并规范化路径，删除 "." 和 ".." 目录

homedir()

获取当前用户的主目录

dirname(path)


## 实例：常用文件操作


## 复习重点

- 能说明 `Julia 文件读写` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
