# Memcached：Memcached stats sizes 命令

- 来源：[Memcached stats sizes 命令](https://www.runoob.com/memcached/memcached-stats-sizes.html)
- 分类：数据库
- 技术：Memcached
- 笔记类型：练习笔记
- 章节序号：1454

## 本章内容

Memcached stats sizes 命令用于显示所有item的大小和个数。

该信息返回两列，第一列是 item 的大小，第二列是 item 的个数。


### 语法：

stats sizes 命令的基本语法格式如下：

```text
stats sizes
```


### 实例

```text
stats sizes
STAT 96 1
END
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Memcached stats sizes 命令` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
