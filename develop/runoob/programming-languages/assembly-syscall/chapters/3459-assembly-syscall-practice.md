# 汇编语言：汇编语言 - 系统调用

- 来源：[汇编语言 - 系统调用](https://www.runoob.com/assembly/assembly-syscall.html)
- 分类：编程语言
- 技术：汇编语言
- 笔记类型：练习笔记
- 章节序号：3459

## 本章内容

系统调用（System Call）是用户程序与操作系统内核交互的唯一途径。通过系统调用，汇编程序可以读写文件、分配内存、创建进程等。


## 什么是系统调用

用户程序运行在受限的 用户态（User Mode），无法直接访问硬件或执行特权操作。

当程序需要执行 IO 操作、内存分配等内核级功能时，必须通过 系统调用 向操作系统内核请求服务。

系统调用的流程是：用户程序发起系统调用 → CPU 切换到内核态 → 内核执行对应服务 → 返回用户态继续执行。

可以把系统调用理解为：用户程序给操作系统打个电话，请求帮忙做一件自己没有权限做的事情。


## Linux 系统调用机制

在 Linux 32 位系统中，系统调用通过以下步骤完成：

- 将 系统调用号 放入 EAX 寄存器
- 将参数放入 EBX、ECX、EDX、ESI、EDI 等寄存器
- 执行 int 0x80 指令触发软件中断
- CPU 切换到内核态，内核根据 EAX 中的调用号执行对应服务
- 内核将返回值放入 EAX，切换回用户态继续执行


## 常用系统调用一览

完整的系统调用列表可在 /usr/include/asm/unistd_32.h 中查看。注意 32 位和 64 位的系统调用号不同。


## sys_write - 输出字符串

最常用的系统调用，用于向屏幕打印内容：


## 实例

运行结果：

```text
$ nasm -f elf32 write_syscall.asm -o write_syscall.o
$ ld -m elf_i386 write_syscall.o -o write_syscall
$ ./write_syscall
Hello, runoob! Welcome to assembly.
```


## sys_read - 读取用户输入

从标准输入（键盘）读取数据：


## 实例

运行结果：

```text
$ nasm -f elf32 read_syscall.asm -o read_syscall.o
$ ld -m elf_i386 read_syscall.o -o read_syscall
$ ./read_syscall
Please enter your name: runoob
Hello, runoob
```


## sys_exit - 退出程序

每个程序都必须调用 sys_exit 来正常退出，否则 CPU 会继续执行后面的垃圾数据导致段错误。


## 实例

退出码可以在 shell 中通过 $? 查看：

```text
$ ./program
$ echo $?
0
```


## 系统调用通用模板

编写系统调用时，可以遵循以下通用模板：


## 实例

int 0x80 触发后，EAX 存放返回值。大多数系统调用成功时返回非负值，失败时返回负的错误码（如 -1 表示 EPERM）。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `汇编语言 - 系统调用` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
