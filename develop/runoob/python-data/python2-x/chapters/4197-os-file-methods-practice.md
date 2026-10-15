# Python2.x：Python OS 文件/目录方法

- 来源：[Python OS 文件/目录方法](https://www.runoob.com/python/os-file-methods.html)
- 分类：Python / 数据科学
- 技术：Python2.x
- 笔记类型：练习笔记
- 章节序号：4197

## 本章内容

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


### 参考地址：

- https://blog.konghy.cn/2015/08/02/python-os/
- https://python.usyiyi.cn/python_278/library/os.html


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Python OS 文件/目录方法` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
