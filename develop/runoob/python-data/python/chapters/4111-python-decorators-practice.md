# Python：Python 装饰器

- 来源：[Python3 装饰器](https://www.runoob.com/python3/python-decorators.html)
- 分类：Python / 数据科学
- 技术：Python
- 笔记类型：练习笔记
- 章节序号：4111

## 本章内容

装饰器（decorator）是 Python 中的一种高级功能，用于在不修改原函数代码的前提下，动态扩展函数或类的功能。

本质上，装饰器是一个函数：它接收一个函数作为参数，并返回一个新的函数（通常是对原函数的增强版本）。

装饰器通过 @decorator_name 语法应用在函数或方法定义之前。

Python 还提供了一些内置装饰器，例如 @staticmethod 和 @classmethod。

常见应用场景：

- 日志记录：记录函数调用信息、参数和返回值
- 性能统计：统计函数执行时间
- 权限控制：限制函数访问权限
- 缓存：缓存函数结果，提高性能


### 基本语法

装饰器的核心思想是：用一个函数"包装"另一个函数。


## 语法

解析：

- decorator_function：装饰器函数（接收原函数）
- wrapper：包装函数（真正被执行）
- @decorator_function：等价于函数替换

等价写法：

```javascript
target_function = decorator_function(target_function)
```

👉 调用 target_function() 时，实际上执行的是 wrapper()


### 使用装饰器

装饰器通过 @ 语法糖应用在函数定义前：

```text
@time_logger
def target_function():
    pass
```

等价于：

```javascript
def target_function():
    pass

target_function = time_logger(target_function)
```

这种机制使我们可以在不修改原函数的情况下，统一添加功能（如日志、权限等）。


## 实例：打印日志

输出：

```text
函数执行前
Hello!
函数执行后
```

- my_decorator 接收 say_hello
- @my_decorator 替换原函数


### 带参数的装饰器

如果原函数有参数，需要在 wrapper 中使用 *args, **kwargs：


## 实例

输出：

```text
执行前
Hello, Alice!
执行后
```

说明：使用 *args, **kwargs 可以兼容任意参数函数。


## 带参数的装饰器（进阶）

说明：这是"装饰器工厂"，外层函数用于接收参数。

```text
Hello!
Hello!
Hello!
```


## 类装饰器

除了函数，装饰器也可以作用于类。

类装饰器接收一个类，并返回修改后的类或包装类。

- 增强类方法
- 控制实例化过程
- 实现单例、日志等功能


### 函数形式的类装饰器


## 实例

```text
调用前
原方法
调用后
```


### 类形式的类装饰器


## 实例：单例模式

```text
初始化
True
```


## 内置装饰器

常用内置装饰器：

- @staticmethod：定义静态方法
- @classmethod：定义类方法
- @property：将方法变为属性


## 实例


## 多个装饰器的堆叠

多个装饰器在定义阶段从下到上依次包裹函数，调用阶段从上到下依次执行：


## 实例

最终输出：

```text
Decorator 1
Decorator 2
Hello!
```


## 核心总结

```text
装饰器 = 函数包装函数 + 不修改原代码扩展功能
```

- @ 语法本质是函数替换
- wrapper 才是真正执行的函数
- 推荐使用 *args, **kwargs 提高通用性
- 支持函数、类、甚至带参数的装饰器


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Python3 装饰器` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
