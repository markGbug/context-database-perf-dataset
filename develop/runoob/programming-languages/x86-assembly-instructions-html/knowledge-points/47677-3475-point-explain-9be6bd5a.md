# 知识点 47677：汇编语言：汇编指令速查表 - 数据传送指令

- 来源：[汇编指令速查表](https://www.runoob.com/assembly/x86-assembly-instructions-html.html)
- 来源章节：[3475-x86-assembly-instructions-html-study.md](../chapters/3475-x86-assembly-instructions-html-study.md)
- 分类：编程语言
- 技术：汇编语言
- 所在小节：数据传送指令
- 知识类型：解释
- 原章节序号：3475

## 原文片段

LEA 与 MOV 的关键区别：LEA REG, [ADDR] 装入的是地址值本身，而 MOV REG, [ADDR] 装入的是该地址处的内存内容。在进行地址计算（如 LEA EAX, [EBX+4*ECX+8]）时 LEA 非常高效。

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `数据传送指令` 这一小节和 `汇编指令速查表` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
