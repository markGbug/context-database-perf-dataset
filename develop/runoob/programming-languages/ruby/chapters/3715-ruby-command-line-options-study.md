# Ruby：Ruby 命令行选项

- 来源：[Ruby 命令行选项](https://www.runoob.com/ruby/ruby-command-line-options.html)
- 分类：编程语言
- 技术：Ruby
- 笔记类型：学习笔记
- 章节序号：3715

## 本章内容

Ruby 一般是从命令行运行，方式如下：

```text
$ ruby [ options ] [.] [ programfile ] [ arguments ... ]
```

解释器可以通过下列选项被调用，来控制解释器的环境和行为。

单字符的命令行选项可以组合使用。下面两行表达了同样的意思：

```java
$ ruby -ne 'print if /Ruby/' /usr/share/bin


$ ruby -n -e 'print if /Ruby/' /usr/share/bin
```


## 复习重点

- 能说明 `Ruby 命令行选项` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
