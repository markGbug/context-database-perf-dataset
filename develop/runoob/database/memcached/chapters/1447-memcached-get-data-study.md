# Memcached：Memcached get 命令

- 来源：[Memcached get 命令](https://www.runoob.com/memcached/memcached-get-data.html)
- 分类：数据库
- 技术：Memcached
- 笔记类型：学习笔记
- 章节序号：1447

## 本章内容

Memcached get 命令获取存储在 key(键) 中的 value(数据值) ，如果 key 不存在，则返回空。


### 语法：

get 命令的基本语法格式如下：

```text
get key
```

多个 key 使用空格隔开，如下:

```text
get key1 key2 key3
```

参数说明如下：

- key：键值 key-value 结构中的 key，用于查找缓存值。


### 实例

在以下实例中，我们使用 runoob 作为 key，过期时间设置为 900 秒。

```text
set runoob 0 900 9
memcached
STORED
get runoob
VALUE runoob 0 9
memcached
END
```


## 复习重点

- 能说明 `Memcached get 命令` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
