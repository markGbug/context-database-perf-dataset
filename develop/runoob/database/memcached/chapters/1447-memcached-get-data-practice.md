# Memcached：Memcached get 命令

- 来源：[Memcached get 命令](https://www.runoob.com/memcached/memcached-get-data.html)
- 分类：数据库
- 技术：Memcached
- 笔记类型：练习笔记
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


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Memcached get 命令` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
