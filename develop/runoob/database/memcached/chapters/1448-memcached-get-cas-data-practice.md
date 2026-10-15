# Memcached：Memcached gets 命令

- 来源：[Memcached gets 命令](https://www.runoob.com/memcached/memcached-get-cas-data.html)
- 分类：数据库
- 技术：Memcached
- 笔记类型：练习笔记
- 章节序号：1448

## 本章内容

Memcached gets 命令获取带有 CAS 令牌存 的 value(数据值) ，如果 key 不存在，则返回空。


### 语法：

gets 命令的基本语法格式如下：

```text
gets key
```

多个 key 使用空格隔开，如下:

```text
gets key1 key2 key3
```

参数说明如下：

- key：键值 key-value 结构中的 key，用于查找缓存值。


### 实例

在以下实例中，我们使用 runoob 作为 key，过期时间设置为 900 秒。

```text
set runoob 0 900 9
memcached
STORED
gets runoob
VALUE runoob 0 9 1
memcached
END
```

在 使用 gets 命令的输出结果中，在最后一列的数字 1 代表了 key 为 runoob 的 CAS 令牌。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Memcached gets 命令` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
