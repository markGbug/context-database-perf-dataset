# Python：Python3 内置函数

- 来源：[Python3 内置函数](https://www.runoob.com/python3/python3-built-in-functions.html)
- 分类：Python / 数据科学
- 技术：Python
- 笔记类型：学习笔记
- 章节序号：4136

## 本章内容

Python 提供了大量内置函数（Built-in Functions），无需导入任何库即可直接使用。 这些函数覆盖了数据类型转换、数学计算、迭代操作、反射机制等常见场景，是每个 Python 初学者必须掌握的基础工具。


### 为什么要掌握内置函数？

- 减少代码量：一行顶多行（例如 sum()、max()）
- 提升可读性：语义明确，比手写逻辑更清晰
- 性能更优：底层 C 实现，通常比 Python 循环更快


### 常见分类

- 数值计算：abs()、round()、min()、max()、sum()
- 类型转换：int()、float()、str()、list()、tuple()
- 迭代与函数式：code>map()、filter()、zip()、enumerate()
- 反射与对象：type()、isinstance()、getattr()、setattr()
- 输入输出：print()、input()、open()


### 常用函数示例

```text
# 求和
sum([1, 2, 3])  # 6

# 最大值
max([3, 6, 2])  # 6

# 类型转换
int("123")      # 123

# 枚举
for i, v in enumerate(['a', 'b']):
    print(i, v)

# map
list(map(lambda x: x * 2, [1,2,3]))  # [2,4,6]
```


## 函数速查表


## 复习重点

- 能说明 `Python3 内置函数` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
