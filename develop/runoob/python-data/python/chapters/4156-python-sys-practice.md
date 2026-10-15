# Python：Python sys 模块

- 来源：[Python sys 模块](https://www.runoob.com/python3/python-sys.html)
- 分类：Python / 数据科学
- 技术：Python
- 笔记类型：练习笔记
- 章节序号：4156

## 本章内容

sys 是 Python 标准库中的一个模块，提供了与 Python 解释器及其环境交互的功能。

通过 sys 库，你可以访问与 Python 解释器相关的变量和函数，例如命令行参数、标准输入输出、程序退出等。


### 导入 sys 库

在使用 sys 库之前，你需要先导入它。导入方式如下：

```text
import sys
```


## 实例


## sys 库的常用功能


### 1. 命令行参数

sys.argv 是一个包含命令行参数的列表。sys.argv[0] 是脚本的名称，后续元素是传递给脚本的参数。

示例代码：


## 实例

运行方式：

```text
python script.py arg1 arg2
```

输出结果：

```text
脚本名称: script.py
参数列表: ['arg1', 'arg2']
```


### 2. 程序退出

sys.exit() 用于退出程序。你可以传递一个整数作为退出状态码，通常 0 表示成功，非零值表示错误。

示例代码：


## 实例


### 3. 标准输入输出

sys.stdin、sys.stdout 和 sys.stderr 分别代表标准输入、标准输出和标准错误流。你可以重定向这些流以实现自定义的输入输出行为。

示例代码：


## 实例


### 4. Python 版本信息

sys.version 和 sys.version_info 提供了当前 Python 解释器的版本信息。

示例代码：


## 实例

输出结果：

```html
<code>Python 版本: 3.9.7 (default, Aug 31 2021, 13:28:12)
[GCC 7.5.0]
版本信息: sys.version_info(major=3, minor=9, micro=7, releaselevel='final', serial=0)
</code>
```


### 5. 模块搜索路径

sys.path 是一个列表，包含了 Python 解释器在导入模块时搜索的路径。你可以修改这个列表来添加自定义的模块搜索路径。

示例代码：


## 实例


## sys 模块常用属性


## sys 模块常用方法


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Python sys 模块` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
