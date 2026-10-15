# Python：Python3 OS 文件/目录方法

- 来源：[Python3 OS](https://www.runoob.com/python3/python3-os-file-methods.html)
- 分类：Python / 数据科学
- 技术：Python
- 笔记类型：练习笔记
- 章节序号：4117

## 本章内容

os 模块是 Python 标准库中的一个重要模块，它提供了与操作系统交互的功能。

通过 os 模块，你可以执行文件操作、目录操作、环境变量管理、进程管理等任务。

os 模块是跨平台的，这意味着你可以在不同的操作系统（如 Windows、Linux、macOS）上使用相同的代码。

在使用 os 模块之前，你需要先导入它。导入 os 模块的代码如下：

```text
import os
```


## os 模块的常用功能


### 1. 获取当前工作目录

os.getcwd() 函数用于获取当前工作目录的路径。当前工作目录是 Python 脚本执行时所在的目录。


## 实例


### 2. 改变当前工作目录

os.chdir(path) 函数用于改变当前工作目录。path 是你想要切换到的目录路径。


## 实例


### 3. 列出目录内容

os.listdir(path) 函数用于列出指定目录中的所有文件和子目录。如果不提供 path 参数，则默认列出当前工作目录的内容。


## 实例


### 4. 创建目录

os.mkdir(path) 函数用于创建一个新的目录。如果目录已经存在，会抛出 FileExistsError 异常。


## 实例


### 5. 删除目录

os.rmdir(path) 函数用于删除一个空目录。如果目录不为空，会抛出 OSError 异常。


## 实例


### 6. 删除文件

os.remove(path) 函数用于删除一个文件。如果文件不存在，会抛出 FileNotFoundError 异常。


## 实例


### 7. 重命名文件或目录

os.rename(src, dst) 函数用于重命名文件或目录。src 是原始路径，dst 是新的路径。


## 实例


### 8. 获取环境变量

os.getenv(key) 函数用于获取指定环境变量的值。如果环境变量不存在，返回 None。


## 实例


### 9. 执行系统命令

os.system(command) 函数用于在操作系统的 shell 中执行命令。命令执行后，返回命令的退出状态。


## 实例


## os 常用方法

os 模块提供了非常丰富的方法用来处理文件和目录。常用的方法如下表所示：

os.access(path, mode)

os.chdir(path)

os.chflags(path, flags)

os.chmod(path, mode)

os.chown(path, uid, gid)

os.chroot(path)

os.close(fd)

os.closerange(fd_low, fd_high)

os.dup(fd)

os.dup2(fd, fd2)

os.fchdir(fd)

os.fchmod(fd, mode)

os.fchown(fd, uid, gid)

os.fdatasync(fd)

os.fdopen(fd[, mode[, bufsize]])

os.fpathconf(fd, name)

os.fstat(fd)

os.fstatvfs(fd)

os.fsync(fd)

os.ftruncate(fd, length)

os.getcwd()

os.getcwdb()

os.isatty(fd)

os.lchflags(path, flags)

os.lchmod(path, mode)

os.lchown(path, uid, gid)

os.link(src, dst)


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Python3 OS` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
