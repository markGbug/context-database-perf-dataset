# Memcached：Memcached flush_all 命令

- 来源：[Memcached flush_all 命令](https://www.runoob.com/memcached/memcached-clear-data.html)
- 分类：数据库
- 技术：Memcached
- 笔记类型：练习笔记
- 章节序号：1455

## 本章内容

Memcached flush_all 命令用于清理缓存中的所有 key=>value(键=>值) 对。

该命令提供了一个可选参数 time，用于在指定的时间后执行清理缓存操作。


### 语法：

flush_all 命令的基本语法格式如下：

```text
flush_all [time] [noreply]
```


### 实例

清理缓存:

```text
set runoob 0 900 9
memcached
STORED
get runoob
VALUE runoob 0 9
memcached
END
flush_all
OK
get runoob
END
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Memcached flush_all 命令` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
