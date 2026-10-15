# Ruby：Ruby 中文编码

- 来源：[Ruby 中文编码](https://www.runoob.com/ruby/ruby-encoding.html)
- 分类：编程语言
- 技术：Ruby
- 笔记类型：学习笔记
- 章节序号：3714

## 本章内容

前面章节中我们已经学会了如何用 Ruby 输出 "Hello, World!"，英文没有问题，但是如果你输出中文字符"你好，世界"就有可能会碰到中文编码问题。

Ruby 文件中如果未指定编码，在执行过程会出现报错：

```text
#!/usr/bin/ruby -w

puts "你好，世界！";
```

以上程序执行输出结果为：

```text
invalid multibyte char (US-ASCII)
```

以上出错信息显示了 Ruby 使用用 ASCII 编码来读源码，中文会出现乱码，解决方法为只要在文件开头加入 # -*- coding: UTF-8 -*-（EMAC写法） 或者 #coding=utf-8 就行了。


## 实例

```text
#!/usr/bin/ruby -w
# -*- coding: UTF-8 -*-

puts "你好，世界！";
```

输出结果为：

```text
你好，世界！
```

所以如果大家再学习过程中，源代码文件中，若包含中文编码，则需要注意两点：

- 1. 必须在首行添加 # -*- coding: UTF-8 -*-,告诉解释器使用utf-8来解析源码。
- 2. 必须设置编辑器保存文件的编码为utf-8。


## 复习重点

- 能说明 `Ruby 中文编码` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
