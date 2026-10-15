# Memcached：Memcached add 命令

- 来源：[Memcached add 命令](https://www.runoob.com/memcached/memcached-add-data.html)
- 分类：数据库
- 技术：Memcached
- 笔记类型：练习笔记
- 章节序号：1442

## 本章内容

Memcached add 命令用于将 value(数据值) 存储在指定的 key(键) 中。

如果 add 的 key 已经存在，则不会更新数据(过期的 key 会更新)，之前的值将仍然保持相同，并且您将获得响应 NOT_STORED。


### 语法：

add 命令的基本语法格式如下：

```text
add key flags exptime bytes [noreply]
value
```

参数说明如下：

- key：键值 key-value 结构中的 key，用于查找缓存值。
- flags：可以包括键值对的整型参数，客户机使用它存储关于键值对的额外信息 。
- exptime：在缓存中保存键值对的时间长度（以秒为单位，0 表示永远）
- bytes：在缓存中存储的字节数
- noreply（可选）： 该参数告知服务器不需要返回数据
- value：存储的值（始终位于第二行）（可直接理解为key-value结构中的value）


### 实例

以下实例中我们设置：

- key → new_key
- flag → 0
- exptime → 900 (以秒为单位)
- bytes → 10 (数据存储的字节数)
- value → data_value

```text
add new_key 0 900 10
data_value
STORED
get new_key
VALUE new_key 0 10
data_value
END
```


### 输出

如果数据添加成功，则输出：

```text
STORED
```

输出信息说明：

- STORED：保存成功后输出。
- NOT_STORED ：在保存失败后输出。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Memcached add 命令` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
