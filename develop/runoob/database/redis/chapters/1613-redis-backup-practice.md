# Redis：Redis 数据备份与恢复

- 来源：[Redis 数据备份与恢复](https://www.runoob.com/redis/redis-backup.html)
- 分类：数据库
- 技术：Redis
- 笔记类型：练习笔记
- 章节序号：1613

## 本章内容

Redis SAVE 命令用于创建当前数据库的备份。


### 语法

redis Save 命令基本语法如下：

```text
redis 127.0.0.1:6379> SAVE
```


### 实例

```text
redis 127.0.0.1:6379> SAVE
OK
```

该命令将在 redis 安装目录中创建dump.rdb文件。


## 恢复数据

```text
redis 127.0.0.1:6379> CONFIG GET dir
1) "dir"
2) "/usr/local/redis/bin"
```

以上命令 CONFIG GET dir 输出的 redis 安装目录为 /usr/local/redis/bin。


## Bgsave

创建 redis 备份文件也可以使用命令 BGSAVE，该命令在后台执行。


### 实例

```text
127.0.0.1:6379> BGSAVE

Background saving started
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Redis 数据备份与恢复` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
