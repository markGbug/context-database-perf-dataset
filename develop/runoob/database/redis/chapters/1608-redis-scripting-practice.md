# Redis：Redis 脚本

- 来源：[Redis 脚本](https://www.runoob.com/redis/redis-scripting.html)
- 分类：数据库
- 技术：Redis
- 笔记类型：练习笔记
- 章节序号：1608

## 本章内容

Redis 脚本使用 Lua 解释器来执行脚本。 Redis 2.6 版本通过内嵌支持 Lua 环境。执行脚本的常用命令为 EVAL。


### 语法

Eval 命令的基本语法如下：

```text
redis 127.0.0.1:6379> EVAL script numkeys key [key ...] arg [arg ...]
```


### 实例

以下实例演示了 redis 脚本工作过程：

```text
redis 127.0.0.1:6379> EVAL "return {KEYS[1],KEYS[2],ARGV[1],ARGV[2]}" 2 key1 key2 first second

1) "key1"
2) "key2"
3) "first"
4) "second"
```


## Redis 脚本命令

下表列出了 redis 脚本常用命令：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Redis 脚本` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
