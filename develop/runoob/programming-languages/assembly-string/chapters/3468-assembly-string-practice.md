# 汇编语言：汇编语言 - 字符串处理

- 来源：[汇编语言 - 字符串处理](https://www.runoob.com/assembly/assembly-string.html)
- 分类：编程语言
- 技术：汇编语言
- 笔记类型：练习笔记
- 章节序号：3468

## 本章内容

字符串处理是编程中常见的需求。

在汇编中处理字符串意味着直接操作内存中的字节序列，虽然更底层但也更灵活。


## 字符串的定义和存储

在 NASM 中，字符串本质上是字节序列，可以用 DB 伪指令定义：


## 实例


## 计算字符串长度

有两种方式获取字符串长度：编译时计算（EQU）和运行时计算（遍历查找 null）：


## 实例


## 字符串复制

使用循环逐字节复制，或使用 x86 的字符串操作指令 MOVSB：


## 实例

REP MOVSB 是 x86 最经典的字符串复制方式。但在现代 CPU 上，手动复制循环配合循环展开可能比 REP MOVSB 更快，因为现代 CPU 对简单操作有更好的流水线优化。


## 字符串比较

使用 CMPSB 配合 REPE（重复直到不等）逐字节比较：


## 实例


## 字符串操作指令汇总


## 大小写转换示例


## 实例

运行结果：

```text
$ nasm -f elf32 case_convert.asm -o case_convert.o
$ ld -m elf_i386 case_convert.o -o case_convert
$ ./case_convert
Hello, runoob! Welcome to Assembly.
HELLO, RUNOOB! WELCOME TO ASSEMBLY.
```

方向标志 DF 决定了字符串操作的方向：DF=0 时 ESI/EDI 递增（正向），DF=1 时递减（反向）。用 CLD 清零 DF，用 STD 置位 DF。在调用 C 函数或系统调用前应该确保 DF=0（cdecl 要求）。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `汇编语言 - 字符串处理` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
