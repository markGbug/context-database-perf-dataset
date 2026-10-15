# Redis：Redis 数据备份与恢复

- 来源：[Redis 数据备份与恢复](https://www.runoob.com/redis/redis-backup.html)
- 分类：数据库
- 技术：Redis
- 笔记类型：学习笔记
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


## 复习重点

- 能说明 `Redis 数据备份与恢复` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
