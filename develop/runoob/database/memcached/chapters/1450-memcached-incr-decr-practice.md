# Memcached：Memcached incr 与 decr 命令

- 来源：[Memcached incr/decr 命令](https://www.runoob.com/memcached/memcached-incr-decr.html)
- 分类：数据库
- 技术：Memcached
- 笔记类型：练习笔记
- 章节序号：1450

## 本章内容

Memcached incr 与 decr 命令用于对已存在的 key(键) 的数字值进行自增或自减操作。

incr 与 decr 命令操作的数据必须是十进制的32位无符号整数。

如果 key 不存在返回 NOT_FOUND，如果键的值不为数字，则返回 CLIENT_ERROR，其他错误返回 ERROR。


## incr 命令


### 语法：

incr 命令的基本语法格式如下：

```text
incr key increment_value
```

参数说明如下：

- key：键值 key-value 结构中的 key，用于查找缓存值。
- increment_value： 增加的数值。


### 实例

在以下实例中，我们使用 visitors 作为 key，初始值为 10，之后进行加 5 操作。

```text
set visitors 0 900 2
10
STORED
get visitors
VALUE visitors 0 2
10
END
incr visitors 5
15
get visitors
VALUE visitors 0 2
15
END
```


### 输出

输出信息说明：

- NOT_FOUND：key 不存在。
- CLIENT_ERROR：自增值不是对象。
- ERROR其他错误，如语法错误等。


## decr 命令

decr 命令的基本语法格式如下：

```text
decr key decrement_value
```

参数说明如下：

- key：键值 key-value 结构中的 key，用于查找缓存值。
- decrement_value： 减少的数值。


### 实例

```text
set visitors 0 900 2
10
STORED
get visitors
VALUE visitors 0 2
10
END
decr visitors 5
5
get visitors
VALUE visitors 0 1
5
END
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Memcached incr/decr 命令` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
