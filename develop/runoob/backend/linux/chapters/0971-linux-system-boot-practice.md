# Linux：Linux 系统启动过程

- 来源：[Linux 系统启动过程](https://www.runoob.com/linux/linux-system-boot.html)
- 分类：后端开发
- 技术：Linux
- 笔记类型：练习笔记
- 章节序号：0971

## 本章内容

linux启动时我们会看到许多启动信息。

Linux系统的启动过程并不是大家想象中的那么复杂，其过程可以分为5个阶段：

- 内核的引导。
- 运行 init。
- 系统初始化。
- 建立终端 。
- 用户登录系统。

init程序的类型：

- SysV: init, CentOS 5之前, 配置文件： /etc/inittab。
- Upstart: init,CentOS 6, 配置文件： /etc/inittab, /etc/init/*.conf。
- Systemd： systemd, CentOS 7,配置文件： /usr/lib/systemd/system、 /etc/systemd/system。


## 内核引导

当计算机打开电源后，首先是BIOS开机自检，按照BIOS中设置的启动设备（通常是硬盘）来启动。

操作系统接管硬件以后，首先读入 /boot 目录下的内核文件。


## 运行init

init 进程是系统所有进程的起点，你可以把它比拟成系统所有进程的老祖宗，没有这个进程，系统中任何进程都不会启动。

init 程序首先是需要读取配置文件 /etc/inittab。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Linux 系统启动过程` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
