# Ruby：Ruby 命令行选项

- 来源：[Ruby 命令行选项](https://www.runoob.com/ruby/ruby-command-line-options.html)
- 分类：编程语言
- 技术：Ruby
- 笔记类型：练习笔记
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


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Ruby 命令行选项` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
