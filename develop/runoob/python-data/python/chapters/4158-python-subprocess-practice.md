# Python：Python subprocess 模块

- 来源：[Python subprocess 模块](https://www.runoob.com/python3/python-subprocess.html)
- 分类：Python / 数据科学
- 技术：Python
- 笔记类型：练习笔记
- 章节序号：4158

## 本章内容

subprocess 是 Python 标准库中的一个模块，用于创建和管理子进程。

subprocess 允许你在 Python 程序中执行外部命令，并与这些命令进行交互。

通过 subprocess 模块，你可以执行系统命令、调用其他程序，并获取它们的输出或错误信息。


### 为什么使用 subprocess 模块？

在 Python 中，有时我们需要执行一些系统命令或调用其他程序来完成特定的任务。例如，你可能需要运行一个 shell 命令、启动一个外部应用程序，或者与一个命令行工具进行交互。subprocess 模块提供了一种安全且灵活的方式来处理这些需求。

与早期的 os.system() 或 os.popen() 相比，subprocess 模块提供了更强大的功能和更好的控制能力。它允许你更精细地管理子进程的输入、输出和错误流，并且可以处理更复杂的场景。


## subprocess 模块的核心功能


### 1. 执行外部命令

subprocess.run() 是 subprocess 模块中最常用的函数之一。它可以执行一个外部命令，并等待命令完成。以下是一个简单的示例：


## 实例

在这个例子中，subprocess.run() 执行了 ls -l 命令，并将输出捕获到 result.stdout 中。


### 2. 处理输入和输出

subprocess 模块允许你控制子进程的输入、输出和错误流。你可以将数据传递给子进程的标准输入，或者从子进程的标准输出和标准错误中读取数据。以下是一个示例：


## 实例

在这个例子中，subprocess.run() 执行了 grep python 命令，并将字符串 'hello\npython\nworld' 作为输入传递给子进程。


### 3. 处理错误

subprocess 模块还允许你处理子进程的错误。如果子进程返回非零的退出状态码，subprocess.run() 会抛出一个 CalledProcessError 异常。你可以通过检查 result.returncode 来获取子进程的退出状态码。


## 实例

在这个例子中，subprocess.run() 执行了 ls nonexistent_file 命令，由于文件不存在，命令失败并抛出了 CalledProcessError 异常。


## subprocess 模块的高级用法


### 1. 使用 Popen 类

subprocess.Popen 类提供了更底层的接口，允许你更灵活地控制子进程。你可以使用 Popen 来启动一个子进程，并在后台运行它，或者与它进行交互。


## 实例

在这个例子中，subprocess.Popen 启动了一个 ping google.com 命令，并在后台运行它。程序通过循环读取子进程的输出，并在子进程结束后获取其退出状态码。


### 2. 使用管道

subprocess 模块允许你使用管道将多个命令连接在一起。你可以将一个命令的输出作为另一个命令的输入。


## 实例

在这个例子中，ls -l 命令的输出被传递给 grep py 命令，最终输出包含 py 的文件或目录。


## subprocess 模块的常用方法、类和参数

以下是 Python subprocess 模块的常用方法、类和参数的说明，包含功能描述及示例：


### subprocess 模块核心方法


### subprocess.CompletedProcess 对象属性（run() 方法的返回对象）


### subprocess.Popen 类常用方法/属性


### 常用参数说明（适用于 run() 和 Popen()）


### 实例

执行命令并捕获输出：


## 实例

通过 Shell 执行复杂命令：

```text
subprocess.run("grep 'error' log.txt | wc -l", shell=True, check=True)
```


## 实例

超时控制：


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Python subprocess 模块` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
