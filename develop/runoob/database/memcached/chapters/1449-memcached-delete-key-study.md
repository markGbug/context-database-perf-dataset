# Memcached：Memcached delete 命令

- 来源：[Memcached delete 命令](https://www.runoob.com/memcached/memcached-delete-key.html)
- 分类：数据库
- 技术：Memcached
- 笔记类型：学习笔记
- 章节序号：1449

## 本章内容

Memcached delete 命令用于删除已存在的 key(键)。


### 语法：

delete 命令的基本语法格式如下：

```text
delete key [noreply]
```

参数说明如下：

- key：键值 key-value 结构中的 key，用于查找缓存值。
- noreply（可选）： 该参数告知服务器不需要返回数据


### 实例

在以下实例中，我们使用 runoob 作为 key，过期时间设置为 900 秒。之后我们使用 delete 命令删除该 key。

```text
set runoob 0 900 9
memcached
STORED
get runoob
VALUE runoob 0 9
memcached
END
delete runoob
DELETED
get runoob
END
delete runoob
NOT_FOUND
```


### 输出

输出信息说明：

- DELETED：删除成功。
- ERROR：语法错误或删除失败。
- NOT_FOUND：key 不存在。


## 复习重点

- 能说明 `Memcached delete 命令` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
