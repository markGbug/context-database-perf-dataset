# Python：Python hashlib 模块

- 来源：[Python hashlib](https://www.runoob.com/python3/python-hashlib.html)
- 分类：Python / 数据科学
- 技术：Python
- 笔记类型：学习笔记
- 章节序号：4149

## 本章内容

Python hashlib 模块主要用于进行哈希（hash）操作。

哈希（Hash）是一种将任意长度的输入数据映射为固定长度输出数据的算法。

哈希通常用于验证数据的完整性、安全存储密码等场景。

哈希函数的输出通常是一串看似随机的字母和数字。

hashlib 模块提供了常见的哈希算法的实现，如 MD5、SHA-1、SHA-256 等。

要使用 hashlib 函数必须先导入：

```text
import hashlib
```

查看 hashlib 模块中的内容:


## 实例

以下是 hashlib 模块的一些常用方法和哈希算法的简介：


### 常用方法

hashlib.new(name, data=None): 创建一个哈希对象。

name 参数是哈希算法的名称，data 参数是要被哈希的数据。


## 实例

输出结果为：

```text
673dc967d03201db7fe47b7eabd56c47ca5bc694222de303106a5504e5d0daa8
```

hashlib.md5() / hashlib.sha1() / hashlib.sha256() / ...: 直接使用特定的哈希算法创建哈希对象。


## 实例

输出结果为：

```text
18fa661e2a4a7dd6471cc1407290cf6e
```


### 哈希对象方法

update(data): 更新哈希对象的消息内容。


## 实例

输出结果为： 1b56561022276e9a5a8e1cda72e1b39fca6f6074326a74d39f6dfd9540c8ecd7 hexdigest(): 获取十六进制表示的哈希值。


## 实例

输出结果为：

```text
18fa661e2a4a7dd6471cc1407290cf6e
```

digest(): 获取二进制表示的哈希值。


## 实例

输出结果为：

```text
b'4\x17\t\xd0\xdb\xc2f3/\x1c\xbc\xd8\xc2_\xd4\xa0T\x12\xb7\xd4'
```


### 常见哈希算法

MD5


## 实例

输出结果为：

```text
18fa661e2a4a7dd6471cc1407290cf6e
```

SHA-1


## 实例

输出结果为：

```text
341709d0dbc266332f1cbcd8c25fd4a05412b7d4
```

SHA-256


## 实例

输出结果为：

```text
673dc967d03201db7fe47b7eabd56c47ca5bc694222de303106a5504e5d0daa8
```

SHA-512


## 实例

输出结果为：

```text
7cfe50493eebd48ee7330c797459c2d0d5ca943bd1c84ad7a0b6783b11cd49d06b4a1dc84ee9ea5e20d0bfedbdb67e716500a20e5870abecea3f32dc8484a811
```

在实际应用中，选择合适的哈希算法取决于具体的需求。需要注意的是，MD5 和 SHA-1 已经被认为不安全，特别是在安全领域，推荐使用更强大的算法，如 SHA-256 或 SHA-512。

Python hashlib 模块中常见的哈希算法及其含义：

说明：

- 摘要长度（位）： 表示哈希算法输出的摘要长度，以位为单位。
- 输出长度（字节）： 表示哈希算法输出的摘要长度，以字节为单位。
- 安全性： 表示哈希算法的安全性级别，包括 "不安全"、"低"、"中等"、"高"。这是一个一般性的分类，具体的安全性还要考虑算法的用途和具体的攻击场景。


## 复习重点

- 能说明 `Python hashlib` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
