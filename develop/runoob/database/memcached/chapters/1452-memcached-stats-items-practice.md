# Memcached：Memcached stats items 命令

- 来源：[Memcached stats items 命令](https://www.runoob.com/memcached/memcached-stats-items.html)
- 分类：数据库
- 技术：Memcached
- 笔记类型：练习笔记
- 章节序号：1452

## 本章内容

Memcached stats items 命令用于显示各个 slab 中 item 的数目和存储时长(最后一次访问距离现在的秒数)。


### 语法：

stats items 命令的基本语法格式如下：

```text
stats items
```


### 实例

```text
stats items
STAT items:1:number 1
STAT items:1:age 7
STAT items:1:evicted 0
STAT items:1:evicted_nonzero 0
STAT items:1:evicted_time 0
STAT items:1:outofmemory 0
STAT items:1:tailrepairs 0
STAT items:1:reclaimed 0
STAT items:1:expired_unfetched 0
STAT items:1:evicted_unfetched 0
END
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Memcached stats items 命令` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
