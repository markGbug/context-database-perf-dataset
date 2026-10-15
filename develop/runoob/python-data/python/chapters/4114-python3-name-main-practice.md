# Python：Python __name__ 与 __main__

- 来源：[Python __name__](https://www.runoob.com/python3/python3-name-main.html)
- 分类：Python / 数据科学
- 技术：Python
- 笔记类型：练习笔记
- 章节序号：4114

## 本章内容

在阅读 Python 代码时，我们经常会在文件末尾看到下面的写法：

```text
if __name__ == "__main__":
    main()
```

这段代码是什么意思？为什么很多 Python 程序都采用这种写法？

在 Python 中，__name__ 是模块的一个特殊属性，"__main__" 是用于标识主执行模块的名称。

通过判断 __name__ 是否等于 "__main__"，可以区分当前模块是作为程序入口运行，还是作为普通模块被导入。

这种写法通常用于将程序的功能定义与运行入口分开，方便代码复用和测试。


## 1、__name__ 变量

__name__ 是 Python 自动设置的模块特殊属性，用于表示当前模块的名称。

它的值取决于模块的运行方式：

- 直接运行模块：__name__ 通常等于 "__main__"。
- 通过 import 导入模块：__name__ 通常等于模块的名称。
- 导入包中的子模块：__name__ 通常是完整模块名，例如 "mypackage.utils"。

下面创建一个名为 module.py 的文件：


## 实例

在终端中直接运行：

```text
python module.py
```

输出结果：

```text
模块名称： __main__
```

如果在另一个 Python 文件中通过 import module 导入该模块，输出则为：

```text
模块名称： module
```

这是因为两种运行方式下，Python 为模块设置的 __name__ 不同。


## 2、__main__ 的含义

__main__ 是 Python 中用于标识顶层执行环境的特殊模块名称。

当直接运行一个 Python 脚本时，Python 会将该脚本作为主执行模块，并把它的 __name__ 设置为 "__main__"。

例如：

```text
python hello.py
```

此时，hello.py 中的 __name__ 为 "__main__"。

如果使用 python -m 运行某个模块：

```text
python -m mymodule
```

被作为程序入口执行的模块，其 __name__ 同样为 "__main__"。

因此，"__main__" 并不是普通的文件名称，而是 Python 用于标识主执行模块的特殊名称。

另外，Python 还支持通过包中的 __main__.py 文件定义包的运行入口，这种方式常用于可以通过 python -m 包名 启动的程序。


## 3、if __name__ == "__main__": 的作用

在 Python 中，一个文件既可以直接运行，也可以被其他文件导入。

如果直接将测试代码、命令行交互或程序启动逻辑放在模块顶层，那么这些代码在模块首次被导入时也可能执行。

为了避免这种情况，可以使用以下判断：

```text
if __name__ == "__main__":
    # 只有作为主程序运行时才执行
    main()
```

其中：

- __name__：当前模块的名称。
- "__main__"：主执行模块的名称。
- if：判断当前模块是否作为程序入口运行。
- main()：程序的主函数，需要提前定义。

例如，下面是一个可以直接运行的完整程序：


## 实例

直接运行时，输出结果为：

```text
程序开始运行
```

如果将该文件作为模块导入，main() 不会因为这个判断而自动执行，但仍然可以通过模块名称主动调用该函数。

注意：if __name__ == "__main__": 只控制其内部代码是否执行，并不会阻止模块中的其他顶层代码在导入时运行。


## 4、完整实例

下面通过两个 Python 文件，演示同一个模块在直接运行和被导入时的区别。


### 创建 example.py

首先创建 example.py 文件：


## example.py 文件


### 直接运行 example.py

在终端执行：

```text
python example.py
```

输出结果：

```text
该脚本正在直接运行。
来自 example 模块的问候！
```

因为 example.py 是直接运行的，所以 __name__ 等于 "__main__"，执行 if 分支中的代码。


### 导入 example.py

接下来在同一目录创建另一个文件 another_script.py：


## another_script.py 文件

在终端执行：

```text
python another_script.py
```

输出结果：

```text
该脚本作为模块被导入。
来自 example 模块的问候！
```

这里的执行过程如下：

- Python 执行 another_script.py。
- 遇到 import example，加载并执行 example.py 的顶层代码。
- 此时 example.__name__ 为 "example"，因此执行 else 分支。
- 随后执行 example.greet()，输出问候信息。

因此，导入模块并不意味着模块中的所有代码都不会执行，而是只有受到 if __name__ == "__main__": 保护的代码不会在普通导入时执行。


## 5、实际应用：将功能代码与运行入口分离

在实际开发中，通常不需要在 if __name__ == "__main__": 后面编写 else 分支。

更常见的做法是，将可以复用的函数写在模块中，然后通过 main() 统一组织程序入口。

例如，创建 calculator.py：


## 实例

直接运行：

```text
python calculator.py
```

输出结果：

```text
加法结果： 15
乘法结果： 50
```

如果在其他模块中导入：


## 实例

输出结果：

```text
计算结果： 10
```

在这个例子中，导入 calculator 时不会自动执行 main()，但可以正常使用 add() 和 multiply() 函数。

这种组织方式可以让同一个 Python 文件同时用于独立运行、模块导入和单元测试。


## 6、python -m 与 __main__.py

除了直接运行 Python 文件，还可以使用 python -m 执行模块或包。

例如，假设项目结构如下：

```text
myproject/
└── mypackage/
    ├── __init__.py
    └── __main__.py
```

其中，__main__.py 内容为：


## 实例

在 myproject 目录中执行：

```text
python -m mypackage
```

输出结果：

```text
通过 python -m 启动程序
```

这是因为 Python 在通过 -m 执行包时，会查找并执行该包中的 __main__.py 文件。

注意：__main__.py 是一个具有特殊用途的 Python 文件名，而 "__main__" 是主执行模块的名称，两者虽然相关，但不是同一个概念。


## 7、常见问题


### 为什么导入模块时，print() 仍然会执行？

因为 Python 在首次正常导入模块时，通常会执行该模块的顶层语句，包括函数和类的定义，以及不受条件保护的 print() 等代码。

例如：

```text
print("模块正在加载")

def hello():
    print("Hello")
```

即使只是执行 import module，也会输出"模块正在加载"。

如果不希望某段代码在导入时执行，可以将其放入 if __name__ == "__main__": 中。


### 每个 Python 文件都必须使用这个判断吗？

不是。

如果文件只用于提供函数、类和其他模块功能，不需要独立运行，就没有必要添加这个判断。

如果文件需要同时支持独立运行和导入复用，使用这种写法通常更合适。


### main() 是 Python 的特殊函数吗？

不是。

main 只是一个普通的函数名称，是开发者经常采用的程序入口命名约定。

Python 不要求必须存在 main() 函数，也不要求必须使用这个名称。

例如：

```text
def start():
    print("程序启动")


if __name__ == "__main__":
    start()
```

这样的写法同样合法。


### __name__ 与 __file__ 有什么区别？

__name__ 表示模块名称，而 __file__ 通常表示模块对应的文件路径。

例如：

```text
print(__name__)
print(__file__)
```

直接运行普通 Python 脚本时，__name__ 通常为 "__main__"，而 __file__ 为脚本文件的路径。

需要注意，某些运行环境中的模块可能没有 __file__ 属性，例如部分交互式环境和内置模块。


## 总结

Python 中的 __name__ 和 __main__ 主要用于区分模块的执行方式。

最常见的写法是：

```text
if __name__ == "__main__":
    main()
```

它的作用是：只有当前模块作为主程序执行时，才运行其中的入口代码。

在编写需要复用的 Python 模块时，建议将功能封装为函数或类，再使用 if __name__ == "__main__": 组织独立运行的程序入口。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Python __name__` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
