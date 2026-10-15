# 知识点 37821：Ruby：Ruby 异常 - 语法

- 来源：[Ruby 异常](https://www.runoob.com/ruby/ruby-exceptions.html)
- 来源章节：[3738-ruby-exceptions-practice.md](../chapters/3738-ruby-exceptions-practice.md)
- 分类：编程语言
- 技术：Ruby
- 所在小节：语法
- 知识类型：代码
- 原章节序号：3738

## 原文片段

```text
begin #开始

 raise.. #抛出异常

rescue [ExceptionType = StandardException] #捕获指定类型的异常默认值是 StandardException
 $! #表示异常信息
 $@ #表示异常出现的代码位置
else #其余异常
 ..
ensure #不管有没有异常，进入该代码块

end #结束
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `语法` 这一小节和 `Ruby 异常` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
