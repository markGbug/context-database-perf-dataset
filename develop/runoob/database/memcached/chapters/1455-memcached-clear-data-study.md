# Memcached：Memcached flush_all 命令

- 来源：[Memcached flush_all 命令](https://www.runoob.com/memcached/memcached-clear-data.html)
- 分类：数据库
- 技术：Memcached
- 笔记类型：学习笔记
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


## 复习重点

- 能说明 `Memcached flush_all 命令` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
